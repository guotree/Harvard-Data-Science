# Probability

This part discusses concepts of probability, and uses R to demonstrate these concepts.

## 1. Discrete probability

Event: refer to things that can happen when something occurs by chance.

Distribution: We simply assign a probability to each category. their proportion defines the distribution.

Monte Carlo

```r
# Setting the random seed
set.seed(1986)
# rep to generate the
beads <- rep(c("red", "blue"), times = c(2,3))
B <- 10000
# repeat the same task any number of times.
events <- replicate(B, sample(beads, 1))
# use table to see the distribution
tab <- table(events)
# prop.table gives the proportions
prop.table(tab)
```

A popular way to pick the seed is the year - month - day

`sample` selects elements _without replacement_

## 2. Continuous probability

## 3. Random variables