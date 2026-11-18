# Issue

**Title:** Separate plugin file system from `BASA_DATA_DIR`

## Description

When processing data via plugins, input and output files are located in ONE shared filesystem, i.e. `BASE_DATA_DIR` (and `WORKING_DIR` for temporary files). This works well as long as the plugin process and Qiita pet & DB are operating within one machine or machines equipped with network file systems like slurm grids.

We intend to host Qiita within a kubernets cloud environment. A plugin will become an independent docker image running as one or multiple pods. It would therefore be advisable to separate the central file system (Qiita pet & DB) from individual plugins, as this would slow boot up of plugin pods AND we might later distribute plugin jobs across multiple clouds. In this use case, transferring the whole `BASE_DATA_DIR` is infeasible.

<img width="1960" height="543" alt="text236" src="https://github.com/user-attachments/assets/66bdd4fe-5a82-4b17-954b-c7c05be6de5a" />

I understand the current flow as follows:
1. the user composes a processing / analysis workflow and hits "run". Qiita pet uses a launcher to "submit" a new job for the according plugin
2. the plugin command requests information about e.g. an artifact, the prep file, ... via qiita_client, which calls the postgress DB and returns filepaths in `BASE_DATA_DIR`.
3. the plugin command directly accesses content of filepaths from 2.

My suggested flow is designed to require minimal changes for plugin codes, e.g. wrapping the filepath when reading / writing content with additional functions `fetch_file_from_central` and `push_file_to_central` to pull or push file content either directly from/to the filesystem (no change from what is done currently) or receive/push and create files in the plugin local or central filesystem, respectively.

This PR adds two endpoints/functions to Qiita pet to send https://github.com/jlab/qiita/blob/be38c1079fe8cb12e120d9b96c48e97b8b3cd062/qiita_pet/handlers/cloud_handlers/file_transfer_handlers.py#L15 and receive https://github.com/jlab/qiita/blob/be38c1079fe8cb12e120d9b96c48e97b8b3cd062/qiita_pet/handlers/cloud_handlers/file_transfer_handlers.py#L61 files to and from plugins.

Both endpoints are deactivated by default (to make Qiita behave as is) and can be activated by setting https://github.com/jlab/qiita/blob/be38c1079fe8cb12e120d9b96c48e97b8b3cd062/qiita_core/support_files/config_test.cfg#L53-L57 to `True`).

For higher performance, file content will be send through nginx instead of plain python/tornado. I thus had to fix the `/Users/username` prefix in the nginx example configuration file to match the actual filepaths.

It's not yet clear to me, IF we need to add a mechanism to check if a plugin has permissions to access the requested file(s) from `BASE_DATA_DIR`. Currently, we "trust" the plugin via oauth credentials.

This PR is accompanied by  to equip the Qiita Client (part of every plugin) to handle according requests. The client can select between the current central `filesystem` mechanism 
https://github.com/jlab/qiita_client/blob/d9543c9575f0171620c17f4e87897ed5cf52a905/qiita_client/qiita_client.py#L783-L790
OR the novel file transfer through `https`
https://github.com/jlab/qiita_client/blob/d9543c9575f0171620c17f4e87897ed5cf52a905/qiita_client/qiita_client.py#L792-L811
Both mechanisms return the actual filepath of the requested (and potentially transferred) files. This allows individual plugins to use different mechanisms, i.e. we don't need to migrate all plugins at once.

As only the plugin functions know which files they request / send as artifact components, we need to "decorate" file access in their individual implementations. Here is an example PR for qp-deblur:

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a34dcebc44ea`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.