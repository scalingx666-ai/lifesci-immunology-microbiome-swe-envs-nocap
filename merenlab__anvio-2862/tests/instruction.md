# Issue

**Title:** Add an HTML player that steps through a map's samples in `anvi-draw-kegg-pathways`

## Description

`--collate-files-by-map` gathers the individual maps into a directory per map, so a map can be compared across samples by stepping through its directory in a file browser. This PR adds `--animate-files-by-map`, which writes an HTML player beside each of those directories. The player shows the map of each sample, contigs database, genome, or group in turn, like a video. It can be paused, a slider moves back and forth to any frame, and the arrow keys step one frame at a time. The file opens in any current web browser, straight from the disk, with no internet connection and no anvi'o installation, so it can be passed around as a single file.

```bash
anvi-draw-kegg-pathways --reaction-txt kegg-reaction.txt \
  --draw-individual-files \
  --collate-files-by-map \
  --animate-files-by-map \
  -o output_dir
```

<img width="2880" height="1920" alt="1_player_glycolysis" src="https://github.com/user-attachments/assets/4b2852b2-be0d-4dcc-bff0-fbd0904c746e" />

*The player of ko00010 Glycolysis / Gluconeogenesis, `by_map/ko00010.html`, for 12 samples with made-up coverages of 341 KOs. The fifth frame is shown, and the colorbar of the individual maps sits beside the map.*

<img width="4060" height="1520" alt="2_player_groups" src="https://github.com/user-attachments/assets/d37a0794-cef8-4804-9ecc-fe60740d6ed1" />

*Both frames of a grouped run, where group G1 holds one sample and G2 holds two. Each group's maps are colored by a count scale of its own, so over the course of the animation, the colorbar changes with the group in the frame.*

<img width="2880" height="1920" alt="3_player_global_map" src="https://github.com/user-attachments/assets/ba164fec-e56b-494e-bd47-5def5e27b17e" />

*The player of the global map ko01100 Metabolic pathways for the 12 samples from before. The map is fitted to the window. "Actual size" shows it at the full resolution of the KEGG image, to be scrolled.*

## Features

- The player of a map is written under `by_map` beside the collated map image directory. For example, `by_map/ko00010` occurs with `by_map/ko00010.html`. `--name-files` and `--categorize-files` apply as they do to the directory, giving, say, `by_map/Metabolism/Carbohydrate_metabolism/ko00010_Glycolysis_Gluconeogenesis.html`.

- The page has a play/pause button, also on the space bar, and a slider with one stop per frame. The left and right arrow keys step one frame, and Home and End jump to the first and last frames. The seconds per frame and looping can be changed on the page. "Actual size" switches between fitting the map to the window and showing it at full resolution.

- Frames follow the order of the run, which is also the order of the panels of a map grid. Samples are sorted by name as text, groups follow the `groups-txt` file, contigs databases follow the order in which they were given, and genomes follow the pangenome. Names listed after `--draw-individual-files` play in the order listed.

- A source with no data on a map has no file in that map's directory. The player shows the bare map in its place, with the note "No data on this map", so every player of a run has the same frames in the same order. With `--draw-bare-maps`, the bare map of that source is drawn and gathered like any other map, and the player shows it without the note.

- The colorbars that key the individual maps are shown beside the map, such as `colorbar_reactions_samples.pdf` and its border counterpart. Where groups are colored by counts of their own sources, the colorbar switches with the frame.

- Each frame is stored in the page as a lossless WebP image at the resolution of the KEGG image, so the colors are those of the map files. Identical images are stored once. Three frames of ko00010, a standard map, take about 0.2 MB, and twelve frames of ko01100, a global map, take about 13 MB. Memory use while writing does not grow with the number of frames.

- The page loads no other file and runs no outside code. Its first frame is written visible, so viewers that run no script, such as Quick Look and Finder thumbnails, still show a map.

- The flag is refused without `--collate-files-by-map`, where only one sample, contigs database, genome, or group gets maps of its own; for a reaction network JSON file; and where the installed Pillow cannot write WebP.

## Implementation

- `HTMLPlayerDrawer`, at the end of `keggmapping.py`, writes a player from a list of PDF files. It is composed into `Mapper` like `PDFGridDrawer` and knows nothing about samples or maps. The page is the template `anvio/data/static/template/kegg-map-player.tmpl`, with inline CSS and plain JavaScript, filled in by replacing placeholders.

- `Mapper._draw_map_players` runs after collation. It takes the frames from the record of the maps drawn in this run, not from the files on disk, so maps left by an earlier run get no player. It draws the bare map of a pathway once, in a temporary directory, where a source lacks the map.

- The closure that found a map's path in `_draw_map_grids` became the method `Mapper._map_path`, which `_find_maps` and the players also use. `_find_maps` takes the extension of the files written into each directory, so the overwrite check covers the players.

- `pillow` is declared in `pyproject.toml` and in the program's dependency check. It was already installed through matplotlib and reportlab.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9938b3f97dfd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.