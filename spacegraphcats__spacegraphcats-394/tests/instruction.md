# Issue

**Title:** Fix assignment bug in rdomset.domination_graph

## Description

Note: This PR requires a rebuild of catlas.

### 1. Testing

We added unit tests to `test_rdomset.py` that fails with the current code and passes with the updated code.

### 2. Performance

We ran our benchmark code with several datasets and observed almost the same running time as the current version. See [[Fix 390] Performance](https://github.com/mogproject/spacegraphcats/wiki/%5BFix-390%5D-Performance) for details.

### 3. Statistics

This fix requires a rebuild of catlas. In this section, we argue statistical effects of the fix on vertex partitioning. See [[Fix 390] Statistics](https://github.com/mogproject/spacegraphcats/wiki/%5BFix-390%5D-Statistics) for details.

#### 3.1 Distance profile

Here we computed the frequency of the distance from every vertex to its assigned dominator in the *induced subgraph* on each piece. Due to the bug, the current version resulted in a partitioning where a vertex is farther than the radius.


```
Distance Profile (twofoo, k=31, seed={1,2,3})

              distance 0              1              2               3     4      5       6
--------------------------------------------------------------------------------------------
r=1	before	 125,272 	 72,654 	 7,737             237 	   2 	  1 	    
		 125,279 	 72,610 	 7,771             215 	   2 		
		 125,325 	 72,545 	 7,791             222 	   6 		
	after	 125,272 	 80,631 					
		 125,279 	 80,598 					
		 125,325 	 80,564 					
r=2	before	  83,448 	 71,982 	 47,303 	 2,846 	 304 	 18 	 2 
		  83,379 	 71,866 	 47,432 	 2,905 	 273 	 22 	
		  83,501 	 71,835 	 47,390 	 2,867 	 273 	 19 	 4 
	after	  83,448 	 83,686 	 38,769 				
		  83,379 	 83,603 	 38,895 				
		  83,501 	 83,645 	 38,743 				
r=3	before	  80,381 	 70,272 	 49,833 	 4,915 	 460 	 38 	 4 
		  80,353 	 70,215 	 49,899 	 4,939 	 432 	 37 	 2 
		  80,359 	 70,035 	 50,010 	 4,982 	 460 	 38 	 5 
	after	  80,381 	 79,502 	 45,014 	 1,006 			
		  80,353 	 79,422 	 45,102 	 1,000 			
	 	  80,359 	 79,216 	 45,276 	 1,038 			
```

![Picture1](https://user-images.githubusercontent.com/2019701/118345021-135d5800-b4ef-11eb-8905-2aed3d083a81.png)


#### 3.2 Piece sizes

After fixing the bug, partitioned piece sizes tend to be slightly more variant. Therefore, the maximum piece size tends to be larger after the fix.

```
Piece Sizes (twofoo, k=31, seed={1,2,3})

[r=1 before]
mean=1.64, min=1, max=6, Q1=1.00, median=1.00, Q3=2.00, variance=0.79, stddev=0.89
mean=1.64, min=1, max=7, Q1=1.00, median=1.00, Q3=2.00, variance=0.78, stddev=0.89
mean=1.64, min=1, max=6, Q1=1.00, median=1.00, Q3=2.00, variance=0.78, stddev=0.88

[r=1 after]
mean=1.64, min=1, max=7, Q1=1.00, median=1.00, Q3=2.00, variance=0.86, stddev=0.93
mean=1.64, min=1, max=10, Q1=1.00, median=1.00, Q3=2.00, variance=0.86, stddev=0.93
mean=1.64, min=1, max=8, Q1=1.00, median=1.00, Q3=2.00, variance=0.86, stddev=0.93

[r=2 before]
mean=2.47, min=1, max=9, Q1=1.00, median=2.00, Q3=4.00, variance=2.87, stddev=1.69
mean=2.47, min=1, max=9, Q1=1.00, median=2.00, Q3=4.00, variance=2.88, stddev=1.70
mean=2.47, min=1, max=9, Q1=1.00, median=2.00, Q3=4.00, variance=2.87, stddev=1.69

[r=2 after]
mean=2.47, min=1, max=11, Q1=1.00, median=2.00, Q3=4.00, variance=3.32, stddev=1.82
mean=2.47, min=1, max=12, Q1=1.00, median=2.00, Q3=4.00, variance=3.35, stddev=1.83
mean=2.47, min=1, max=12, Q1=1.00, median=2.00, Q3=4.00, variance=3.33, stddev=1.83

[r=3 before]
mean=2.56, min=1, max=11, Q1=1.00, median=2.00, Q3=4.00, variance=3.38, stddev=1.84
mean=2.56, min=1, max=11, Q1=1.00, median=2.00, Q3=4.00, variance=3.38, stddev=1.84
mean=2.56, min=1, max=13, Q1=1.00, median=2.00, Q3=4.00, variance=3.39, stddev=1.84

[r=3 after]
mean=2.56, min=1, max=12, Q1=1.00, median=2.00, Q3=4.00, variance=3.77, stddev=1.94
mean=2.56, min=1, max=13, Q1=1.00, median=2.00, Q3=4.00, variance=3.79, stddev=1.95
mean=2.56, min=1, max=13, Q1=1.00, median=2.00, Q3=4.00, variance=3.79, stddev=1.95
```

![Picture2](https://user-images.githubusercontent.com/2019701/118345025-1d7f5680-b4ef-11eb-916c-b9de64ea0bf4.png)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1f3b0a9a15c0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.