---
layout: post
title: "Linear Regression in R"
comments: true
meta : R, machine learning, statistics
---

### Linear Regression in R

Using the closed form formula for beta minimizing the mean squared error (MSE):

<img src="https://latex.codecogs.com/svg.latex?\Large&space;\hat{\beta} = (X^TX)^{-1}X^TY" />

```
linear <- function(y, X) {
  # fit a linear model
  beta <- solve(t(X) %*% X) %*% t(X) %*% y
  return(beta)
}

# simulate some data:
n <- 100
X <- rnorm(n)
# the "true" function plus Gaussian error:
y <- 4.5*X + 12.345 + rnorm(n, 0, 1) * 2
plot(X, y)

# augment X with a column of 1's
X <- cbind(X, rep(1,n))
# fit the model
beta = linear(y, X)

# plot the fit line
X <- -10:10
y <- beta[1] * X + beta[2]
lines(X, y)
```

![plot 1]({{ "/assets/lr1.png" | absolute_url }})


### Using `lm`
`model <- lm(y ~ X)`
