# Issue

**Title:** Refactoring pangenome-graph state structure, handling, and use

## Description

The PR solves a few minor issues and a MAJOR issue. Minor issues include,

* The load state / save state functionality that was not working (there has been a few bugs to clean up)
* And the load state / save state modal windows looking way different than the rest of the windows in the codebase used for the same purpose (now they are standardized)

The major issue became clear after these changes.

Since these changes enabled me to use `anvi-export-state` and `anvi-import-state` to study, edit, and re-import state files (simply to not have to go through all the changes in the interface manually while comparing different runs for the same dataset), I realized that the variable names for visual entities in the HTML side of things (as well as in the JS code) could have benefited from a refactor.

Here is an example state prior to this PR:

```json
{
    "rearranged_color": "#8ff0a4",
    "accessory_color": "#dc8add",
    "paralog_color": "#ffa348",
    "singleton_color": "#99c1f1",
    "core_color": "#bcbcbc",
    "trna_color": "#f66151",
    "layer_color": "#f5f5f5",
    "non_back_color": "#f8e45c",
    "back_color": "#3d70a0",
    "flexsaturation": true,
    "arrow": 3,
    "flexarrow": true,
    "globalbackbone": 3,
    "flexglobalbackbone": true,
    "flexstart": false,
    "flexstop": false,
    "flexpartial": false,
    "flexcall_type": false,
    "start": 0,
    "stop": 0,
    "partial": 0,
    "call_type": 0,
    "flexp4_satellite_0001layer": true,
    "flexp4_satellite_0002layer": true,
    "flexp4_satellite_0003layer": true,
    "flexp4_satellite_0004layer": true,
    "flexp4_satellite_0005layer": true,
    "flexp4_satellite_0006layer": true,
    "p4_satellite_0001layer": 7,
    "p4_satellite_0002layer": 7,
    "p4_satellite_0003layer": 7,
    "p4_satellite_0004layer": 7,
    "p4_satellite_0005layer": 7,
    "p4_satellite_0006layer": 7,
    "flextree": true,
    "tree_length": 44,
    "tree_offset": 1,
    "tree_thickness": 2,
    "distx": 45,
    "disty": 120,
    "size": 15,
    "circ": 5,
    "edge": 5,
    "flexlinear": true,
    "line": 5,
    "label": 0,
    "label_offset": 1,
    "search_hit": 3,
    "inner_margin": 3,
    "outer_margin": 0,
    "inner": 41,
    "start_angle": 0,
    "end_angle": 270,
    "num_position": 20,
    "flexcondtr": false,
    "condtr": -1,
    "flexmaxlength": true,
    "maxlength": 1000,
    "flexgroupcompress": false,
    "groupcompress": 1,
    "track_line_width": 5,
    "region_label_size": 14,
    "region_label_min_width": 80,
    "region_label_distance": 2,
    "flexbinlabels": true,
    "bin_label_orientation": "natural",
    "bin_label_size": 21,
    "bin_ring_height": 4,
    "bin_ring_opacity": 0.8,
    "flexbinedges": true,
    "bin_edge_thickness": 4,
    "bin_edge_color": "#ffffff",
    "bin_edge_opacity": 1,
    "flexp4_satellite_0001": true,
    "flexp4_satellite_0002": true,
    "flexp4_satellite_0003": true,
    "flexp4_satellite_0004": true,
    "flexp4_satellite_0005": true,
    "flexp4_satellite_0006": true,
    "p4_satellite_0001": "#000000",
    "p4_satellite_0002": "#000000",
    "p4_satellite_0003": "#000000",
    "p4_satellite_0004": "#000000",
    "p4_satellite_0005": "#000000",
    "p4_satellite_0006": "#000000"
}
```

There are multiple issues here. layers appear multiple times, variable names are quite cryptic, and we do not exploit the nested nature of JSON objects. Altogether, these make the use of pan-db state files outside of the interface (manually or programmatically) almost impossible. The same state file (well, without all the genomes shown for brevity) could look like this after renaming cryptic variable names and implemented a nested structure:

```json
{
      "drawing": {
          "type": "circular",
          "inner_radius": 41,
          "start_angle": 0,
          "end_angle": 270,
          "node_x_spacing": 45,
          "node_y_spacing": 120
      },
      "nodes": {
          "radius": 15,
          "outline_width": 5,
          "fade_by_prevalence": true,
          "type_colors": {
              "core": "#BCBCBC",
              "rearrangement": "#8FF0A4",
              "accessory": "#DC8ADD",
              "multi_copy": "#FFA348",
              "singleton": "#99C1F1",
              "trna": "#F66151"
          }
      },
      "edges": {
          "width": 5
      },
      "graph_layout": {
          "grouping_enabled": false,
          "grouping_threshold": -1,
          "max_edge_length_enabled": true,
          "max_edge_length": 1000,
          "group_compression_enabled": false,
          "group_compression": 1.0
      },
      "layers": {
          "backbone": {
              "visible": true,
              "height": 3,
              "backbone_color": "#3D70A0",
              "variable_region_color": "#F8E45C"
          },
          "orientation_arrow": {
              "visible": true,
              "height": 3
          },
          "search": {
              "hit_height": 3
          }
      },
      "genome_tracks": {
          "line_width": 5,
          "background_color": "#F5F5F5",
          "genomes": {
              "p4_satellite_0001": {
                  "color": "#000000",
                  "show": true,
                  "track_height": 7,
                  "show_track": true
              },
              "p4_satellite_0002": {
                  "color": "#000000",
                  "show": true,
                  "track_height": 7,
                  "show_track": true
              },
              {...}
          }
      },
      "layers_tree": {
          "visible": true,
          "height": 44,
          "offset": 1,
          "line_width": 2
      },
      "imported_layers": {
          "some_imported_layer": {
              "visible": false,
              "height": 0
          }
      },
      "labels": {
          "font_size": 0,
          "offset": 1,
          "position_tick_count": 20
      },
      "margins": {
          "inner": 3,
          "outer": 0
      },
      "region_labels": {
          "font_size": 13,
          "min_width_px": 80,
          "distance": 2
      },
      "bins": {
          "show_labels": true,
          "label_orientation": "natural",
          "label_font_size": 19.5,
          "ring_height": 4,
          "ring_opacity": 0.8,
          "show_edges": true,
          "edge_thickness": 4,
          "edge_color": "#FFFFFF",
          "edge_opacity": 1.0
      }
  }
```

Of course changing the state file this way requires also changes in the HTML, JS, as well as the Python code since they are all wired together. And not only that, we need a migration script, otherwise the `anvi-display-pan-graph` will simply fail when working with existing pan-db files.

Thus, in addition to all these changes, this PR bumps the `pan-db` version from 4 to 5, and includes a migration script to make sure nothing is lost in existing pan-db files.

Tested on a mock dataset, Tianyi's `p4` dataset, and Alex's _Undatipelagibacter_ dataset. Works well, migration script is good.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9b976992185a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.