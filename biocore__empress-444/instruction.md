# Issue

**Title:** Ultrametric option

## Description

@gibsramen and I threw together a method for rendering trees as ultrametric ( )

Here are some screenshots of the ultrametric trees:
Rectangular
![Screen Shot 2020-11-09 at 4 26 57 PM](https://user-images.githubusercontent.com/19470970/98621791-e8364980-22bc-11eb-923c-c8c43ea70187.png)
Circular
![Screen Shot 2020-11-09 at 4 32 36 PM](https://user-images.githubusercontent.com/19470970/98621793-ea98a380-22bc-11eb-92f7-f59cca1f90b2.png)
Unrooted
![Screen Shot 2020-11-09 at 6 54 35 PM](https://user-images.githubusercontent.com/19470970/98621855-1156da00-22bd-11eb-9d8e-ce2003b0ad05.png)

I am unsure why the unrooted layout does not appear to have equal root to tip distances is unclear to me and I could use some guidance here.

This method relies on the algorithm as described in comments and below:
```
         The lengths for intermediate nodes are effectively "stretched" until
         their deepest descendant hits the deepest level in the whole tree.

         E.g., if we are at the node represented by * in the tree below:

         |--------------------------maxDistance-------------------------|
         |--distanceAbove--|           |---distanceBelow---|
                            |-length--|                     |-remainder-|
                                                    ____
                                        ___________|
                            *__________|           |_______
          __________________|          |__
                            |
                            |___________________________________________

         then the branch will be extended so that its deepest tip has the
         same depth as the deepest tip in the whole tree,
         i.e., newLength = length + remainder
         however, below it is equivalently calculated with
         newLength = maxDistance - distanceAbove - distanceBelow

         E.g.,
         |--------------------------maxDistance-------------------------|
         |--distanceAbove--|                        |---distanceBelow---|
                            |-length--||-remainder-|
                                                                 ____
                                                     ___________|
                            *_______________________|           |_______
          __________________|                       |__
                            |
                            |___________________________________________

        Repeated in a pre-order traversal, this will result in an ultrametric tree

```

## Questions for reviewers
* Do you know why the unrooted layout renders as it does?
* I did not spend a ton of time thinking out how this should be exposed to the user. Currently it is a checkbox under the layout page, and if it is check the "Ignore branch lengths" checkbox is ignored. How do you think we should code the interaction between these two functionalities?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4c681c056fa4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.