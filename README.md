# ECE2112_PA-2
Isaac Benedict R. Deangkinay

This repository contains the code itself in python language and three files with ```.npy``` extentions for the Programming Assignment 2 of ECE2112 Advanced Programming and Algorithms. This assignment features three different type of problems utilizing Numpy and its uses in order to create solutions in running each code for the problems.
### Universal Function
```python
import numpy as np
print(" ",' ')
```
These functions will work through out the three problems of the assignment.

* ```import numpy as np``` will import numpy as a shortened version np for every beginning line of each code.
* ```print(" ",' ')``` will print with a title of the input together with it's function.

# A. REPRODUCIBLE NORMALIZATION PROBLEM
> OBJECTIVES: Create a reproducible random 5 × 5 integer ndarray named X. Use the following two statements before performing any calculation: ```np.random.seed(2112) X = np.random.randint(10, 101, size=(5, 5))``` Normalize the complete array using Z = X − ¯x / σ , where ¯x is the mean of all 25 elements and σ is their population standard deviation as returned by NumPy’s default std() call. Store the normalized array in X normalized. Required checks: Display X, X normalized, its mean, and its standard deviation. Up to floating- point rounding, the normalized mean must be 0 and the normalized standard deviation must be 1.

## Discussion
### Funtions Used
```python
np.random.seed(2112)
X = np.random.randint(10, 101, size=(5, 5))
print("Original Matrix (X) \n", X)

X_normalized = (X - np.mean(X)) / np.std(X)
print("X_normalized Matrix\n",X_normalized)

print("Mean of X =",np.mean(X))

print("Mean of X =",np.std(X))

print("Mean of X_normalized =",np.mean(X_normalized))

print("Mean of X_normalized =",np.std(X_normalized))

np.save("X_normalized.npy", X_normalized)
```

* ```np.random.seed(2112)```: Sets the random number generator's seed to 2112. This ensures that every time the code runs, it generates the exact same sequence of random numbers.

* ```np.random.randint(10, 101, size=(5, 5))```: Generates a 5x5 two-dimensional NumPy array filled with random integers ranging from 10 up to 100 (the upper limit 101 is exclusive).

* ```np.mean(X)```: Calculates the average (arithmetic mean) of all $25$ elements across the entire array 

* ```X.np.std(X)```: Computes the population standard deviation of all elements in array X.

* ```X_normalized = (X - np.mean(X)) / np.std(X)```: Performs Z-score normalization. It subtracts the mean from every element (centering it around 0) and divides by the standard deviation (scaling the spread to 1).

* ```np.save('X_normalized.npy', X_normalized)```: Saves the resulting array into a binary file named X_normalized.npy on disk for later retrieval.

# B. CUBES DIVISIBLE BY 4 PROBLEM
> Using NumPy, create the first 100 positive integers, cube every element, and reshape the result into a 10 × 10 ndarray named C. Thus, C begins with 13 and ends with 1003. Page 1 — Experiment No. 2 Use a Boolean condition on C to obtain every cubed value divisible by 4. Store the selected values in div by 4. Preserve NumPy’s normal row-major selection order. Required checks: Display the shape of C, the array div by 4, and the number of selected elements. A correct solution has 50 selected elements; the first is 8 and the last is 1,000,000.

## Discussion
### Functions Used
```python
X = np.arange(1,101)
print("X Matrix\n",X)

C = X.reshape(10,10)
print("C Matrix (10x10)\n", C)

cubed = C**3
print("Cubed C Matrix\n", cubed)

Mod = cubed % 4
print("Modulo 4 of C Matrix\n", Mod)

chk_mod = Mod == 0
print("Divisible by 4 checker\n", chk_mod)

chk_cubed = cubed[chk_mod]
print("Cubed Checker\n", chk_cubed)

np.save('div_by_4.npy', C)
```
* ```np.arange(1, 101)```: Generates a 1D NumPy array containing sequential integers starting at 1 up to 100 (the stop value 101 is exclusive).

* ```x.reshape(10, 10)```: Takes the 100-element 1D array and reorganizes its shape into a 10x10 two-dimensional matrix named C.

* ```C ** 3```: Raises every individual element in matrix C to the power of 3 (cubing each value).

* ```cubed % 4```: Applies the modulo operator to compute the remainder when each cubed element is divided by 4.

* ```Mod == 0```: A comparison operation returning a Boolean array (True/False) where elements are True if the remainder is 0 (i.e., divisible by 4) and False otherwise. This will then be imported to being chk_mod

* ```cubed[chk_mod]```: Uses the Boolean array as a mask to extract only the values from cubed where the corresponding condition is True. This will then be imported to being chk_cubed

* ```np.save('div_by_4.npy', C)```: Saves the array C to disk in binary .npy format.

# C. ABOVE-MEAN SQUARES PROBLEM
``` Create a 6 × 6 ndarray named S containing the squares of the first 36 positive integers in increasing row-major order. Compute the mean of all elements of S and store it in S mean. Then use Boolean filtering to select only the elements strictly greater than S mean. Store these values in above mean. Required checks: Display S, S mean, above mean, and the number of selected elements. A correct solution has 15 selected elements; the first is 484 and the last is 1296.```

## Discussion
### Functions Used
```python
X = np.arange(1,37)
print("First 36 Numbers\n", X)

S = X.reshape(6,6)
print("S Matrix (6x6)\n", S)

sqr = S**2
print("Squared S Matrix\n", sqr)

Sum = np.sum(sqr)
print("Summation of Squared S Matrix =", Sum)

S_mean = Sum/36
print("Mean of S Matrix =", S_mean)

above_mean = sqr[sqr > S_mean]
print("Above Mean S Matrix\n", above_mean)

Num_of_Elements = len(above_mean)
print("Number of Elements =", Num_of_Elements)

np.save('above_mean.npy', above_mean)
```

* ```np.arange(1, 37)```: Generates a 1D array of integers from 1 through 36.

* ```x.reshape(6, 6)```: Reorganizes the 36 sequential elements into a 6x6 two-dimensional matrix S.

* ```S ** 2```: Squares every element in matrix S.

* ```np.sum(sqr)```: Calculates the sum of all elements inside the sqr matrix.

* ```Sum / 36```: Manually computes the arithmetic mean by dividing the grand total by the total number of elements (36).

* ```sqr > S_mean```: Evaluates whether each squared element is strictly greater than the calculated mean S_mean, producing a Boolean mask.

* ```sqr[sqr > S_mean]```: Filters the matrix to return only the values where the condition is True.

* ```len(above_mean)```: Counts the total number of elements in the filtered 1D array above_mean.

* ```np.save('above_mean.npy', above_mean)```: Exports the resulting array to disk as a .npy file.

## HISTORY OF README FILE
September 3, 2026: Finalization and Completing readme file
September 2, 2026: Addition of Functions and Objectives of each problem
August 27, 2026: Creation of repository and readme file

Thank you and Godbless
