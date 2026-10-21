# Vector and Scalar Evaluation

clean_scores_vector() first creates a vector of scores, based on an original 
scores vector passed in, say c(4, NA_real_, 15). We run an ifelse, to convert 
NA_real_ to 0 and to double 4 to 8 and 15 to 30. Then, we select all the scores 
greater than 20 (30) and set them to 20, essentially doing a ceil operation.

The vector approach operates over the entire vector, and is much more concise.
Using selectors, entire columns and subsets of the data can be manipulated at
once. The selectors themselves are powerful, allowing you to slice and mask
the vector. The scalar approach, on the other hand, operates on the individual
elements, iterating over each one. This approach is less concise, but offers
the benefits of granular control and possibly being more readable for other
programmers from a non-R background. Recycling could possibly tip the scales
in favor of the vector approach, as it offers a feature that would be awkward
to implement with the scalar approach. 

Ultimately, there is no singular right answer as to which of the two is strictly
superior. The right answer is on a case-by-case basis. 

For example, if I were to, say, develop an app in collaboration with programmers 
who have less experience with R, I might go for the scalar approach. If I want 
more granular control, say, call a method then perform more complex operations for
every element greater than 20 in a vector, I would lean towards scalar as well since
those cases would make the vector implementation awkward or even impossible.

On the other hand, if I wanted to perform alternating addition/subtractions on
every element in a vector, or maybe use complex masks to select certain items,
the vector approach is much more idiomatic.