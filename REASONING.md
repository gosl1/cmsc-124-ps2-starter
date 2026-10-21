# Reasoning Before Execution

Write the rule behind each case before you commit your predictions. Replace
every placeholder line below with one to three sentences that name the rule
producing that case's value, type, length, and dimensions. One rule is enough.
After you run and find a miss, add a short correction entry under that case in a
later commit.

## P01
c() combines the arguments into one atomic vector. Based on coercion logic, the highest type within the list is double, so the type for the atomic vector will be double, and each element will be converted to double as well, with TRUE -> 1, 2L -> 2, 3.5 -> 3.5 or [1,2,3.5]. Length is 3 with dim none.


## P02
The highest type in the coercion ladder is character which is evident in index 2 = "2". Hence each element becomes a character ["1L","2","TRUE"] with length 3 and dim none.

After comparing, it was supposed to be 1, not 1L. Because L is a literal suffix and not part of the value.

## P03
Because the right operand is shorter than the left, we use recycling and repeat the values until it reaches the end of the left operand. Each element is an integer so the atomic vector type will be integer [11,22,31,42]. Length being 4, and dim as none.
## P04
Positive indices return the values based on selected positions and what order they are as arguments. The elements they return also keeps their names. [third=9,first=8], integer, with length 2, and dim none.

## P05
Negative indices excludes in a selected position. This is in contrast to P04 that selects positions instead. Hence, the atomic vector is [4,9], integer, length 2, and dim none.

## P06
is.na() identifies arguments that are NA (missing values). The other condition is x being greater than 10. Since we have an OR/| boolean we check each argument if they pass either condition. It then returns an atomic vector with arguments passing the conditions holding TRUE. [NA,12], with length 2, and dim none.

## P07
The position of a label in the levels vector dictates their code. So "low" = 1 and "high" = 2. Our vector
is then factor["low","high","low];levels=["low","high"]. With type integer, length 3, and dim none.

After comparing, there should've been no quotation. factor[low,high,low];levels=[low,high]

## P08
value — item 1 is an integer vector, and item 2 is a character vector.  list{[scores=[3,5],label=["A"]]}

type — the outer container is a list. The inner vector being integer doesn't change the outer type.

length — length() on a list counts top‑level items, not elements inside them. so the integer vector with 2 arguments is considered 1.

dim — none

after comparing, i figured i accidentally added extra brackets.


## P09
A data frame is a list of columns so typeof() reports list, and length() counts columns, not rows. The dim is rows × columns. Value is data.frame[2x2]{id=[1,2],passed=[TRUE,FALSE]}, type list, length 2, dim 2x2.


## P10
A matrix is an atomic vector plus a dim attribute, stored column-wise. The underlying vector is [1,2,3,4,5,6]. Both operands are integer, so no widening. matrix(1:6, nrow = 2L) in this case has 2 rows and 2 columns. Value: matrix[2x3](11,22,13,24,15,26), type: integer, length: 6, dim: 2x3.


## P11
`NA` is a missing value but `mean()` returns a single number, so the result collapses to one value based on the average of the elements. Value `[6]`, type `integer`, length `1`, dim `none`.

After comparing, I realized the value was [NA] and not 6, with the type being double. This is because of NA propagation and mean() always returning a double.


## P12
`na.rm = TRUE` tells `mean()` to remove the missing value first, then average what remains: `(8 + 10) / 2 = 9`. `mean()` still returns a single number. Value `[9]`, type `integer`, length `1`, dim `none`.

After comparing, the type should've been a double.

## P13
`1:3` is an integer vector. Writing the double `2.5` into one slot is mixed-mode assignment: R cannot store a double inside an integer vector, so it widens the entire vector to double, retyping every element rather than truncating `2.5`. The block returns its last expression. Value `[1,2.5,3]`, type `double`, length `3`, dim `none`.


## P14
`scores` is an integer vector. `ifelse` evaluates the `is.na` mask and the `scores * 2` branch, then picks per position: where the mask is `TRUE` take `0`, else take the doubled value, giving `14,0,24,8`. The cap mask `adjusted > 15` sets position 3 to `15`, giving `14,0,15,8`. Value `[14,0,15,8]`, type `integer`, length `4`, dim `none`.

After comparing, I realized NA_real still harbors the double type even if we change its value.
So scores is a double vector instead.

## P15
An array is an atomic vector plus a multi-dimensional `dim` attribute. `1:8` is an integer sequence, so the storage type is integer. `length()` counts total elements, and the `dim` attribute is the three dimensions. Values are written in storage order. Value `array[2x2x2](1,2,3,4,5,6,7,8)`, type `integer`, length `8`, dim `2x2x2`.


## P16
A zero index selects nothing — positions start at 1, and a zero contributes no positions to the result, so the result is an empty vector. The empty result keeps the storage type of the original vector, so it is an empty integer vector (`integer(0)`), not `NULL`. `length()` is 0, and a plain atomic vector carries no `dim`. Value `[]`, type `integer`, length `0`, dim `none`.
