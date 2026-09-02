# ECE2112_PA-2
Isaac Benedict R. Deangkinay

This repository contains a python code of three problems about arrays etc

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

Thank you and Godbless
