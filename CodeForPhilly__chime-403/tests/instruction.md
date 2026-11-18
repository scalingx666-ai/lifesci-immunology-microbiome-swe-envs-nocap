# Issue

**Title:** Issue #239: Fixed off by one day error

## Description

The graph displays one day less than entered. Here is how the graph looks with the incorrect index

![Screenshot (3)_LI](https://user-images.githubusercontent.com/61572112/78084076-4729fc80-7385-11ea-8ac3-9231aa0ee29f.jpg)

The graph ends with July 8th, which is 99 days from today (3/31/2020). When removing the incorrect index, the graph extends to July 9th, 100 days from today (3/31/2020).

![Screenshot (4)_LI](https://user-images.githubusercontent.com/61572112/78084308-c9b2bc00-7385-11ea-8473-81441c124f74.jpg)

The graphs were calculated with all of the default values entered into the sidebar. The values in the graph do not change, except for the added day. This is due to the incorrect indexing error with the panda data frames. This becomes apparent when looking at the data in csv format. Here is what the new admissions data looks like using a text difference checker.

------------(With the change) ------------------------------------------- (Without the change)---------
![Capture](https://user-images.githubusercontent.com/61572112/78086954-75abd580-738d-11ea-85fa-8528f974cac0.JPG)

Now both the chart and the csv files display the proper number of days, and the csv files end with the correct day number.


***The first two commits did not fully solve the issue, the third and final commit does**

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f60da6ffc5ae`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.