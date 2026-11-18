# Issue

**Title:** Curation of trees in manual mode

## Description

Phylogenetic tree calculations often take a few rounds of curation, but curating them is not so easy when you want to have full control over branching patterns with insights into underlying sequences effectively.

The PR adds a new feature into `anvi-interactive` that enables users to use the 'inscpection' window of the program (that shows up when they click the items button in the Bins panel) to pick and choose which items they want to keep in their bin, discard forever, or move to other bins (see the screenshots below).

This feature becomes most powerful when the interactive interface is called with a FASTA file an a phylogenetic tree, such as this:

```
anvi-interactive --fasta sequences.fa \
                 --tree sequences.newick \
                 --profile profile.db
```

Since not only it allows you to see your sequences, but also helps you download a version of your FASTA file by excluding sequences described in one or more bins (or vice versa).

Let's assume you are looking at a region like this in your phylogenetic tree,

<img width="2091" height="1458" alt="image" src="https://github.com/user-attachments/assets/989bdcf4-9cf3-43f4-b2fc-d437abd66929" />

And you wish to see how the sequences relate to one another in this region. With this PR, clicking on the items button on the bins panel,

<img width="195" height="105" alt="image" src="https://github.com/user-attachments/assets/ac72cd81-2a18-4dae-a20c-9f7c325179f1" />

Will show a window like this:

<img width="1976" height="1339" alt="image" src="https://github.com/user-attachments/assets/16b2876c-162e-40ff-9d2a-1febcfeb6964" />

Then you will be able to select a sequence or more like this,

<img width="1959" height="1322" alt="image" src="https://github.com/user-attachments/assets/fac29bd6-0aef-4fd7-b3af-6b0c8b7b11fd" />

And perhaps move it to another bin (let's say into a bin called `delete`, to mark undesirable sequences for deletion as you go through your tree manually):

<img width="1959" height="1322" alt="image" src="https://github.com/user-attachments/assets/633b5948-18d8-4d47-a070-d5d4fcb2dd80" />

When you click apply and close the window, now they will be in that other bin. From which you can later get all the item ids copied, removed from the FASTA file using `anvi-script-reformat-fasta` with the `--exclude-ids` parameter, and recalculate your tree, and so on. OR BETTER YET, you can use the Bins panel and click, say, 'excluding sequences in bins' button here,

<img width="995" height="128" alt="image" src="https://github.com/user-attachments/assets/8be7f4fb-54e4-4562-b769-369ae0295a3d" />

To download your input FASTA file, without the sequences collected in one or more bins:

<img width="1026" height="802" alt="image" src="https://github.com/user-attachments/assets/e57cc591-a40d-4235-a444-a95957fa22dc" />

---

This will (hopefully) be very useful for those who go into rabbit holes of carefully curating phylogenetic trees, and want to have maximum control over their final data by keeping an eye on the sequence context (like @katysloz 💪, but perhaps also for people like @tdelmont and his colleagues who deal with phylogenetic trees and want more visual help for control).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `87467981db8e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.