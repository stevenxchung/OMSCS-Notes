# Lesson 5

In this lesson we will examine how to make a robot generate smooth paths utilizing [PID control](https://en.wikipedia.org/wiki/PID_controller) techniques.

## Smoothing Algorithm

The smoothing algorithm is as follows:

1. Initialize variables equal to each discrete coordinate ($y_i = x_i$)
2. Minimize error for $(x_i - y_i)^2$ (original vs. smooth point) and $(y_i - y_{i+1})^2$ (each consecutive smooth point)

## Path Smoothing

We may optimize $(x_i - y_i)^2$ and $(y_i - y_{i+1})^2$ with gradient descent as follows:

```python
y_i += alpha * (x_i - y_i) + beta * (y_i_plus + y_i_minus - 2 * y_i)
```

Where `y_i` and `x_i` are 2D (or 3D) vectors (points in space) `alpha` and `beta` may be adjusted. We also want to discard the first and last entry since they will be the same.

## PID Implementation

So far we have observed the following issues in robot motion:

1. _Overshooting_ (may be addressed with _proportional_ gain)
2. _No convergence_ (may be addressed with _derivative_ gain)
3. _Systematic bias_ (may be addressed with _integral_ gain)

We may address these issues with a PID controller denoted by $u(t)$ as follows:

$u(t) = K_p e(t) + K_i \int e(t) dt + K_d (de/dt)$

Where $K_p$, $K_i$, and $K_d$ represent the proportional, integral, and derivative gain respectively. We may use these gains to address the above issues.

## Twiddle

Given we may use PID controller to smooth robot motion, how do we go about finding the best PID control gains? We may leverage the _twiddle_ algorithm as follows:

```python
# Gains
p = [...]
# Gain increments
dp = [...]

acceptable_limit = 1e-5
step_size = 0.1
best_error = run(p)

# Keep modifying gains such that errors are small
while sum(dp) > acceptable_limit:
    # Adjust each gain
    for i in range(len(p)):
        p[i] += dp[i]
        error = run(p)
        if error < best_error:
            # Increase gain by some amount if error is decreasing
            best_error = error
            # May increase by lower or higher value
            dp[i] *= (1 + step_size)
        else:
            # Decrease gain (to twice its value to test other bounds) if error is increasing
            p[i] -= 2 * dp[i]
            error = run(p)
            if error < best_error:
                # Increase gain by some amount if error is decreasing
                best_error = error
                # May increase by lower or higher value
                dp[i] *= (1 + step_size)
            else:
                # Otherwise, error is not improving so we reset values
                p[i] += dp[i]
                dp[i] *= (1 - step_size)
```

This _twiddle_ algorithm allows us to increase or decrease each gain until the most optimal gains are produced which meets an acceptable threshold.

## Section Quizzes

### Robot Motion Quiz

_Given the grid, which path is preferred_? The red one since it is the smoothest.

### Smoothing Algorithm 1 Quiz

_If you apply only the first of the above criteria (provided), what path do you get_? Original path since we only measure the error between the discrete points vs. the smooth ones.

### Smoothing Algorithm 2 Quiz

_If you apply only the second of the above criteria (provided), what path do you get_? No path since each consecutive path would be the same.

### Smoothing Algorithm 3 Quiz

_Suppose you optimize both above criteria (provided) at the same time with an appropriate $\alpha$, what path do you get_? We would get a smooth path since the paths would be similar during optimization for both.

### Zero Data Weight Quiz

_Suppose you have $\alpha=0$ and $\beta=0.1$, which of the following (provided) do you get_? A straight line since the first and last coordinates are not modified.

### PID Control Quiz

_Which do you think is best suited to control the car_? We should steer in proportion to the cross track error (distance between car and reference).

### Proportional Control Quiz

_Given a robot utilizes only a P controller to control the CTE, What will happen with the car_? It will overshoot since the gain is high (marginally stable since the robot never converges).

### Oscillations Quiz

_If you modify the control parameter $\tau$ from 0.1 to 0.3, what happens?_? It will oscillate faster since the gain is higher.

### Systematic Bias Quiz

_What happens when you run with the provided values_? A larger CTE occurs since the system has bias.

### Is PD Enough Quiz

_Can the differential term solve this problem (systematic bias)_? No since the differential term will only work to reduce proportional overshoot.
