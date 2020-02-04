## Matlab matrixes (multidimensional arrays)

In this page:

-   Creating matrixes
-   Accessing elements
-   Manipulating arrays

#### Creating matrixes

`A = [1 2 3; 4 5 6; 7 8 9]`
A = 3x3
1 2 3
4 5 6
7 8 9

Add 3rd dimention value (: represents insert of all row/col values):
`A(:,:,2) = [10 11 12; 13 14 15; 16 17 18]`

Set all x/y values to 0, append new z
`B(:,:,4) = 0`

#### Accessing elements

`A(x,y,z) // row, column, page`

Use the index vector [1 3] in the second dimension to access only the first and last columns of each page of A.

`C = A(p:,[1 3],:)`

In other words: I need **all rows**, **1st and 3rd column**, **all pages**

`D = A(2:3,:,:)`

I need 2to3 rows, all columns, all pages

#### function examples

```matlab
z = 2:9
ave2 = average(z)

function result = average(x)
	result = sum(x(:))/numel(x);
end
```
