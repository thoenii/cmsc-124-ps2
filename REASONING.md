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
The | operator means logical OR, so TRUE | NA gives TRUE because one side is already true. The mask is.na(x) | x > 10L selects the missing value and 12, giving [NA,12]. It returns the values at the selected positions, not the position numbers, because the missing value was created as NA_integer_ and the other value is integer, the result has type integer, length 2, and dimensions none.

## P07
A factor stores integer codes for its categories and uses levels as labels. Therefore, typeof() reports integer. The three observations are low, high, and low, so the length is 3. The levels are ordered as low and high, giving 2 levels.

## P08
A list can store different types in separate elements without converting them to a common type. This list contains a scores vector and a label, so typeof() reports list and the length is 2. The length counts the top-level elements, not all the values inside them.

## P09
A data frame is a list of columns with the same number of rows, and since it is stored as a list of columns, typeof() reports list, while class() reports data.frame. The id column is integer and the passed column is logical. There are 2 columns and 2 rows, so the length is 2 and the dimensions are 2 × 2.

## P10
R stores matrices by columns, filling each column from top to bottom, and the matrix stores its values in the order 1,2,3,4,5,6. When c(10L, 20L) is added, recycling adds 10 to stored positions 1, 3, and 5, and 20 to positions 2, 4, and 6, which produces matrix[2x3](11,22,13,24,15,26). The type stays integer because both operands are integer, the length is 6, and the dimensions are 2 × 3.

## P11
NA represents a missing value, and mean() returns NA when a missing value is present and na.rm = TRUE has not been specified. The result is [NA] and its type is double because the input contains NA_real_ and double values, its length is 1 because it contains NA, and its dimensions are none. In P12, na.rm = TRUE changes the result by removing the missing value before calculating the mean.

## P12
Setting na.rm = TRUE tells mean() to remove missing values before calculating. It uses 8 and 10, so the sum is 18 and the denominator is 2, giving 9. The result has type double, length 1, and dimensions none.

## P13
The sequence 1:3 starts as an integer vector, and when 2.5 is assigned to position 2, R widens the entire vector to double because a vector must store one common type. The existing values are also retyped, giving [1,2.5,3]. The type is double, the length is 3, and the dimensions are none.

## P14
ifelse() chooses a value at each position based on a test, which in this case, the missing score is replaced with 0 before the comparison, while the other scores are doubled, producing [14,0,24,8]. The comparison selects 24, which is capped at 15, producing [14, 0, 15, 8]. The final result is a double vector of length 4 with no dimensions.

## P15
An array is an atomic vector with a dim attribute attached. The values 1:8 are integers, and arranging them into dimensions does not change their type, and the array has 8 elements, so its length is 8, and its dimensions are 2 × 2 × 2. Its type is integer.

## P16
R indexing starts at position 1, so index 0L selects nothing. The result is an empty vector [] that keeps the original integer type. Its length is 0, and its dimensions are none.
