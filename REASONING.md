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

## P03
Because the right operand is shorter than the left, we use recycling and repeat the values until it reaches the end of the left operand. Each element is an integer so the atomic vector type will be integer [11,22,31,42]. Length being 4, and dim as none.
## P04
Positive indices return the values based on selected positions and what order they are as arguments. The elements they return also keeps their names. [third=9,first=8], integer, with length 2, and dim none.

## P05
Negative indices excludes in a selected position. This is in contrast to P04 that selects positions instead. Hence, the atomic vector is [4,9], integer, length 2, and dim none.

## P06
is.na() identifies arguments that are NA (missing values). The other condition is x being greater than 10. Since we have an OR/| boolean we check each argument if they pass either condition. It then returns an atomic vector with arguments passing the conditions holding TRUE. [NA,12], with length 2, and dim none.

## P07
Replace this line with the rule that decides this case.

## P08
Replace this line with the rule that decides this case.

## P09
Replace this line with the rule that decides this case.

## P10
Replace this line with the rule that decides this case.

## P11
Replace this line with the rule that decides this case.

## P12
Replace this line with the rule that decides this case.

## P13
Replace this line with the rule that decides this case.

## P14
Replace this line with the rule that decides this case.

## P15
Replace this line with the rule that decides this case.

## P16
Replace this line with the rule that decides this case.
