# Vector and Scalar Evaluation

Replace this paragraph after your checks pass. Trace one input, including the
missing value, through `clean_scores_vector()` and `clean_scores_scalar()`.
Compare the two evaluation models, identify where recycling would change the
answer, and explain which implementation you would keep in an R program.

Tracing `clean_scores_scalar()` on c(A = 6, B = NA, C = 7, D = 67). In pass 1, A's 6 is present, so it is doubled to 12, which is under the cap. In pass 2, B is missing, so 0 is stored and the doubling is skipped. In pass 3, C's 7 is present, so it is doubled to 14, which is under the cap. In pass 4, D's 67 is present, so it is doubled to 134 and capped at 20. The scalar loop makes evaluation order visible in the for loop itself, for(i in seq_along(out)), since it visits the elements one at a time from first to last, with one pass per position. The order also shows inside each pass, where the (is.na(out[[i]])) check runs first and decides whether the element is replaced with 0 or is doubled and capped, using out[[i]] <- min(out[[i]] * 2, 20).

The implementation that we would keep is clean_scores_vector(). It does the same job in just three vector expressions, with no loop and no position handling, so it costs less. On the other hand, clean_scores_scalar() needs a for loop to visit each element and needs to keep the names using setNames() and out[[i]] <- value. The tradeoff is evaluation visibility, the vector version hides each decision inside vector operations, while the loop shows exactly how and when each element is handled.