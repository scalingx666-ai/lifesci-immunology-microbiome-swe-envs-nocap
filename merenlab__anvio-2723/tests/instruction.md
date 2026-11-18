# Issue

**Title:** Pan graph interface cosmetics

## Description

This PR introduces a series of cosmetic and functional improvements to the Settings panel of the pan-graph interactive interface. Here are some bullet points on what changed and why:

  - Fixed sidebar scrolling so the nav column stays visible while settings content scrolls
  - Moved colorpicker dimensions out of repetitive inline styles into a shared CSS class
  - Renamed section headers and field labels throughout the panel for clarity. It was very confusing, and hard to intuitively follow. Some changes are very simple (such as "Drawing Type" becoming "Layout", "Others" becoming "Genome Labels & Margins", "Node x-distance" becoming "Horizontal node spacing"), others are a bit more involved (such as moving graph behavior controls moved up next to Layout, relocating arc angle inputs into the Layout section, backbone height and color pickers split into separate rows, etc). All simple at the end, but I think they are much more readable/comprehensible for a life scientist.
  - Redesigned the Genomes section and merged it with Genome Tracks section. It looks quite different compared to what it looked like before. This is before, two separate sections:

    <img width="424" height="278" alt="image" src="https://github.com/user-attachments/assets/44a80367-cc9e-4118-b031-1292b0cad847" />
    <img width="422" height="412" alt="image" src="https://github.com/user-attachments/assets/a019fe69-8f64-4657-a83b-f8b66aa6c66e" />

    and this is now:

      <img width="421" height="513" alt="image" src="https://github.com/user-attachments/assets/caa10c2a-0954-47ce-8616-92bbdd8f9160" />

  - I also fixed the group compression default value (which was 0.0, so when the user clicked on it all groups were compressed to become invisible, and it is now 0.5), and added range validation with user warnings so it can't go below 0.1 and over 1.0 :)

PS: I vibe coded it all, but carefully validated the changes as I go (and I have to admit, it was an exercise in patience, and I implemented the Genomes + Genome Tracks merger step entirely manually because trying to do it with Claude took so long and went so wrong in so many ways that I was like "you know what, I got this part champ").

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `20bc2844ee85`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.