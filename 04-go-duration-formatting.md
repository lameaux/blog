# Go time.Duration Formatting

## Problem

In Go, there is a useful data type called [time.Duration](https://pkg.go.dev/time#Duration), which is typically used to represent time intervals, such as request latency.

However, the default [String()](https://pkg.go.dev/time#Duration.String) method doesn’t always return a concise output. 
For instance, the following code might generate an unnecessarily long string:

```golang
fmt.Printf("Total duration: %s\n", totalDuration)
```

```
Total duration: 5.66225375s
```

What if I don’t need this level of nanosecond precision? Is there a way to display the duration in milliseconds only?


## Solution

We can use either [Round()](https://pkg.go.dev/time#Duration.Round) or [Truncate()](https://pkg.go.dev/time#Duration.Truncate) methods to achieve the desired level of precision.

In this case, I am using **Round()** to keep the milliseconds only:

```golang
fmt.Printf("Total duration: %s\n", totalDuration.Round(time.Millisecond))
```

Now, the value is formatted neatly:

```
Total duration: 5.662s
```

Examples from [Round() documentation](https://pkg.go.dev/time#Duration.Round) show how it can be used to format **time.Duration**:
```
d.Round(   1ns) = 1h15m30.918273645s
d.Round(   1µs) = 1h15m30.918274s
d.Round(   1ms) = 1h15m30.918s
d.Round(    1s) = 1h15m31s
d.Round(    2s) = 1h15m30s
d.Round(  1m0s) = 1h16m0s
d.Round( 10m0s) = 1h20m0s
d.Round(1h0m0s) = 1h0m0s
```
