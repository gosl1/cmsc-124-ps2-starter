# Reasoning Before Execution

Write the rule behind each case before you commit your predictions. Replace
every placeholder line below with one to three sentences that name the rule
producing that case's value, type, length, and dimensions. One rule is enough.
After you run and find a miss, add a short correction entry under that case in a
later commit.

## P01
The coercion ladder runs logical, integer, double, and character, which is the rule is used in this case. With double being the highest because of the presence of 3.5, so true becomes 1, 2L becomes 2, 3.5 stays and each one is a double. The value is [1,2,3.5] with length 3 and no dimensions.

## P02
The coercion ladder runs logical, integer, double, and character, which is the rule is used in this case. With character being the highest because of the presence of "2", so 1 becomes "1", "2" stays, TRUE becomes "TRUE" and the result is character. The value is ["1","2","TRUE"] with length 3 and no dimensions.

## P03
The recycling case where the shorter operand is repeated, which is the rule used in this case. The shorter vector's first element 1L is paired (added) with 10L and 30L, while the second element 2L is paired with 20L and 40L, both operands are integers, so the result stays integer. The value is [11,22,31,42] with length four and no dimensions.

## P04
Indexing by position using the positive indices which selects the position. 3 selects the third position and 1 selects the first position, all have L so the type is integer. The value is [third=9,first=8] with length two and no dimensions.

## P05
Indexing by exclusion using the negative indices which excludes that position and includes everything else. -2L drops the second position and keeps the others, all have L so the type is integer. The value is [4, 9] with length two and no dimensions.

## P06
Indexing by logical value and missing values rule selects positions where the condition is true and TRUE | NA is TRUE and FALSE | NA is NA, so is.na(x) | x > 10L selects a missing element, respectively. is.na(x) is F,T,F,F and x > 10L is F,NA,T,F, so the mask is F,T,T,F so it picks the NA and the 12. The value is [NA,12], type integer, with length two, no dimensions.

## P07
The factor rule stores integer codes and level labels, so typeof reports integer, not character. The printed labels low and high are the level names that the codes point to, while the levels were supplied as low, high, so that order is kept. The value is factor[low,high,low];levels=[low,high], type integer, with length three and no dimensions.

## P08
A list is an object consisting of an ordered collection of objects known as its components, it can store unlike types. Length gives the top-level components only, and scores and label make two items even though scores holds two values. The value is list{scores=[3,5],label=["A"]}, type list, with length two and no dimensions.

## P09
A data frame is a list of equal-length columns, so typeof reports list, not data.frame. Length counts top-level items, which are the columns, so it is two and not the row count, while dimensions are rows by columns, which gives 2x2. The value is data.frame[2x2]{id=[1,2],passed=[TRUE,FALSE]}, type list, with length two and dimensions 2x2.

## P10
Recycling a vector into a matrix rule, a matrix is stored by column, so R recycles the shorter vector down that order and the result keeps the matrix's dimensions. For matrix(1:6, nrow = 2L), the stored order is 1,2,3,4,5,6, so c(10L, 20L) repeats as 10,20,10,20,10,20 and gives 11,22,13,24,15,26 (added). The value is matrix[2x3](11,22,13,24,15,26), type integer, with length six and dimensions 2x3.

## P11
Missing values arithmetic with a missing value gives a missing value. The NA_real_ in c(8, NA_real_, 10) affects the whole computation, so the result is NA. The value is [NA], type double (mean() returns a double), with length one and no dimensions.

## P12
Missing values with na.rm = TRUE removes missing values before mean() computes, so the NA no longer affects the result. The NA_real_ is dropped, leaving 8 and 10, and the mean is (8 + 10) / 2 = 9. The value is [9], type double (mean() returns double), with length one and no dimensions.

## P13
Atomic vectors and their one shared type means that an atomic vector stores one basic type, so when subassignment puts a double into an integer vector, R widens the whole vector to double so the new value fits. x starts as the integer vector 1:3 ([1,2,3]), and assigning 2.5 to position 2 makes all three elements doubles. The value is [1,2.5,3], with length three and no dimensions.

## P14
Missing values and indexing by logical value where ifelse() replaces the NA with 0 and multiplies the rest by 2, and a condition inside [ ] changes only the TRUE positions. The multiplied scores are 14,0,24,8, and only the 24 is above 15, so it is assigned 15. All the values are doubles, so the value is [14,0,15,8], type double, with length four and no dimensions.

## P15
Arrays and matrices an array is an atomic vector with a dim attribute, and its values are listed in storage order, down the columns. 1:8 holds eight integers, and dim = c(2L, 2L, 2L) arranges them into a 2x2x2 shape without changing the stored order. The value is array[2x2x2](1,2,3,4,5,6,7,8), type integer, with length eight and dimensions 2x2x2.

## P16
Indexing by position where R indices begin at 1, and index 0 selects nothing, returning a zero-length result of the same atomic type. c(4L, 7L, 9L) is an integer vector, so 0L selects nothing. The value is [], with length zero and no dimensions.
