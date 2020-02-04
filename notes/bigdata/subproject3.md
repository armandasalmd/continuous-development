## Big data sub-project3

-   compare the traditional ensemble with cluster based ensemble (**CBE**)

-   **ensemble comparisons** - challenge level(8/10)
-   if you choose this option then CBE data in a 2D array for each hour is provided
-       you still be required to show Big Data techniques in the form of parellel processing

#### Project main steps

1. load data from CBE (data given)
1. load the data models
1. generate a simple traditional ensemble (from step 2 data)
1. compare 2 e.g. by subtracting the values of the one from the other

#### Example

Model A | B | CBE:
1 1 1 | 3 3 3 | 1 2 3
1 1 1 | 3 3 3 | 3 2 1
1 1 1 | 3 3 3 | 2 2 2

To generate tradictional ensemble, we laod model A&B and take the mean(avg) value resulting in (1+3)/2:
2 2 2
2 2 2
2 2 2

Then we compare 2 ensembles by subtracting the traditional ensemble from the CBE
(1-2) (2-2) (3-2) -1 0 1
(3-1) (2-2) (1-2) = 2 0 -1
(2-2) (2-2) (2-2) 0 0 0

\>0 means that CBE values are higher
\<0 means that traditional ensemble values are higher
=0 means that models are equal
