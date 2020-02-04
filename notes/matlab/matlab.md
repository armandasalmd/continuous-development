## Matlab programming basics

**MATLAB is an abbreviation for "matrix laboratory."**

create variable

```matlab
a = 1
```

use math functions like: `sin(x), cos(x)`

if you add semicolumn matlab dont display the result, but calculates `e = a*b;`

#### Matrix and arrays

create array: `a = [1 2 3 4]` or `a = [1,2,3,4]`

create matrix: `a = [1 2 3; 4 5 6; 7 8 10]`, **semi** separates new rows!

```matlab
a = 3x3
1 2 3
4 5 6
7 8 10
```

create matrix (creates array colXrow):

-   `zeros(colCount, rowCount)`
-   `ones(colCount, rowCount)`
-   `rand(colCount, rowCount)`

**operations on matrix (a):**
i.e. `a + 10` would add 10 to all matrix values!

**transpose/rotate matrix with a'**

**matrix mult** when a and b are matrix: `a * b`
**matrix elem-wise mult** `a .* b`
**matrix elem-wise power** `a .^ b`

matrix concatination:

-   column-wise `A=[a,a]`
-   row-wise `A=[a;a]`

https://uk.mathworks.com/help/matlab/learn_matlab/array-indexing.html
