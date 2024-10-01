# Inference and Modeling

## 1. Parameters and Estimates

**Parameters**: we define _parameters_ to represent unknown parts of our models.

## 4. Hypothesis testing

**p_value**: We have observed a random variable X¯=0.52, and the p-value is the answer to the question: How likely is it to see a value this large, when the null hypothesis is true? If the p-value is small enough, we _reject the null hypothesis_ and say that the results are _statistically significant_. (The p-value is the probability of observing a value as extreme or more extreme than the result given that the null hypothesis is true.)

**Power**: _power_ is the probability of detecting spreads different from 0.

## 6. Data-driven models

``map_df`` v. s. ``sapply``:

In R programming, `map_df` and `sapply` are both functions used for applying a function to each element of a vector or list, but they have some key differences:

1. **Output Type**:
    - `map_df` from the purrr package (part of the tidyverse) applies a function to each element of a vector or list and then combines the results into a single data frame. It is specifically designed to work with data frames and tibbles.
    - `sapply` applies a function to each element of a vector or list and returns a matrix, a higher-dimensional array, or a list, depending on the input and the nature of the function applied.
2. **Default Data Structure**:
    - `map_df` always returns a data frame (or a tibble, which is a modern version of a data frame).
    - `sapply` returns a matrix or an array if possible, otherwise it returns a list.
3. **Performance**:
    - `map_df` is often easier to use with non-standard evaluation and can be more readable when working with data frames.
    - `sapply` can be faster in some cases because it is optimized for matrix operations, but it might require more manual handling of the output structure.
4. **Ease of Use**:
    - `map_df` is part of the tidyverse, which promotes a consistent and easy-to-understand syntax for data manipulation.
    - `sapply` is a base R function, and while it is very powerful, it might require more effort to handle the output in a tidy data frame format.

## 8. Hierarchical Models

 A key difference between the **Bayesian** and the **Frequentist** hierarchical model approach is that, in the latter, we use data to construct priors rather than treat priors as a quantification of prior expert knowledge.