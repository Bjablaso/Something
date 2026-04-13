# SER486 Project 5 - Performance Calculation
## Average Execution Time of led_update()
### Brandon Jablasone

---

## Profiling Setup
In this program we measure the execution cost of led_update() running two separate 10‑second loops. The first loop called c1 count how many iteration can run when loop led_update() is not called. than we establishing the base line for raw speed. The second loop called c2 perform the same measurement but we ened up calling the led_update() for each iteration, allowing us to compute the function execution. From this we form the difference between c1 and c2.


## Formula
```
Tled_update = Ttotal × (1/Nled - 1/Nbaseline)

Where:
  Ttotal = 10 seconds (profiling period)
  Nbaseline = c1 (loop count baseline)
  Nled = c2 (loop count with led_update)
  Tled_update = average time for one led_update() call
```

---

## Measurement Results (Simulator-Only)

We ran the program in the simulator and capture values for `c1` and `c2`. This is due to the the virtual lab serial being  unavailable, use one of these accepted simulator-only methods:

1. Capture from simulator console output if available.
2. Capture from debugger symbols by stopping execution after profiling loops and reading `c1` and `c2` in `main()`.

Record values here:
```
c1 = 1474707
c2 = 591498
```

---

## Calculation Steps

### Step 1: Calculate baseline loop time per iteration
```
Tbaseline_per_iter = Ttotal / Nbaseline = 10.0 / c1 seconds
```

### Step 2: Calculate loop time per iteration with led_update
```
Tled_per_iter = Ttotal / Nled = 10.0 / c2 seconds
```

### Step 3: Calculate led_update() execution time
```
Tled_update = Tled_per_iter - Tbaseline_per_iter
            = 10.0/c2 - 10.0/c1
            = 10.0 × (1/c2 - 1/c1)
```

---

## Calculation

Using captured values from simulator/debugger:
- Nbaseline (c1) = 1474707 loops
- Nled (c2) = 591498 loops

### Calculation:
```
Step 1: Tbaseline = 10.0 / 1474707 = 6.7810e-6 seconds = 6.7810 microseconds

Step 2: Tled = 10.0 / 591498 = 1.6906e-5 seconds = 16.9062 microseconds

Step 3: Tled_update = 16.9062 - 6.7810 = 10.1252 microseconds per call
```

**Result:** `led_update()` takes approximately **10.1252 microseconds** per execution.

---



