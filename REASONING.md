# Reasoning Before Execution

Write the rule behind each case before you commit your predictions. Replace
every placeholder line below with one to three sentences that name the rule
producing that case's value, type, length, and dimensions. One rule is enough.
After you run and find a miss, add a short correction entry under that case in a
later commit.

## P01
An atomic vector stores one basic type. When c(TRUE, 2L, 3.5) combines logical, integer, and double values, R follows the coercion ladder and uses the highest type, which is double. Therefore, TRUE and 2L become 1 and 2, giving [1,2,3.5]. The type is double, the length is 3, and the dimensions are none.

## P02
An atomic vector must have one common type. In c(1L, "2", TRUE), character is the highest type so every element will turn into a character, including the logical value, which becomes "TRUE" and 1L becomes "1". The result is ["1","2","TRUE"], with type character, length 3, and dimensions none.

## P03
R recycles the shorter vector when performing arithmetic. In c(10L, 20L, 30L, 40L) + c(1L, 2L), 1L is added to positions 1 and 3, while 2L is added to positions 2 and 4. The result is [11,22,31,42] and the type stays integer because both vectors contain integers, the length is 4, and the dimensions are none.

## P04
R uses index starting from 1, and positive indices select values in the requested order. Selecting positions 3 and 1 from c(first = 8L, second = 5L, third = 9L) gives [third=9,first=8] and the type is integer, the length is 2, and the dimensions are none. The names stay attached to their values, and the output follows the order of the selected positions. 

## P05
Negative indexing removes the specified positions. In c(4L, 7L, 9L)[-2L], position 2, which contains 7, is removed. The remaining values are [4,9] in their original order with type integer, length is 2, and the dimensions are none.

## P06
The expression "is.na(x) | x > 10L" inside the square brackets will output TRUE for every value that is either NA or greater than the integer 10, and FALSE otherwise. Here, since we are inserting logical values for every element into the indexing syntax, the program treats it like a mask, and returns the elements at indices where the value is TRUE.

## P07
Since we plug in the vectors into the factor constructor, our final result is a factor, with two possible values "low" and "high" for each element, and actual values "low", "high" and "low". The type is integer because factors always store values as integers under the hood.

## P08
We create a named list with this syntax, which has no unified type among its elements, therefore its type is list. The length being 2 doesn't count the two scores 3 and 5, but rather counts the two "sublists" scores and label. This still doesn't count as a second dimension, however, so the dim stays as none.

## P09
Data frames can also have mixed element types, therefore the list type. The length also counts id and passed, rather than the inner elements. This time though, there are defined dimensions since id and passed are implicitly treated as columns.

## P10
R stores matrices by columns, filling each column from top to bottom, and the matrix stores its values in the order 1,2,3,4,5,6. When c(10L, 20L) is added, recycling adds 10 to stored positions 1, 3, and 5, and 20 to positions 2, 4, and 6, which produces matrix[2x3](11,22,13,24,15,26). The type stays integer because both operands are integer, the length is 6, and the dimensions are 2 × 3.

## P11
NA represents a missing value, and mean() returns NA when a missing value is present and na.rm = TRUE has not been specified. The result is [NA] and Its type is double because the input contains NA_real_ and double values. In P12, na.rm = TRUE changes the result by removing the missing value before calculating the mean.
Correction: I realized the missing value NA still counts one as its length.

## P12
Setting na.rm = TRUE tells mean() to remove missing values before calculating. It uses 8 and 10, so the sum is 18 and the denominator is 2, giving 9. The result has type double, length 1, and dimensions none.

## P13
This block creates a vector made up of the numbers 1, 2 and 3, but then assigns the double value 2.5 to the second element. This assignment implicitly changes the vector type to double, and the two other values are coerced.

## P14
This block first creates a scores vector with type double, due to the lack of L next to the numbers. We then create a new vector, adjusted, which iterates through every score using is.na(scores), and then changing the value using an ifelse. The value becomes 0 if NA, and gets doubled otherwise. Finally, all scores over 15 are ceilinged at 15. The length and type never change, and there were no dimensions in the first place, due to both being regular vectors.

## P15
This is an array initializer using the values 1 to 8 (inclusive), and the dimensions are explicitly defined as 2x2x2. The resulting array is therefore three dimensional, with length 8.

## P16
The inside of the square bracket is a zero, therefore it accesses none of the elements inside the vector. The result is an empty vector, but with the integer type since the source vector is also integer type.