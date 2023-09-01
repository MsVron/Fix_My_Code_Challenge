# FizzBuzz Python Implementation - Issue and Fix
---
## Introduction

FizzBuzz is a simple programming task used in coding interviews and as an educational tool. The task is to print numbers from 1 to `n`, but for multiples of three, print "Fizz" instead of the number, and for multiples of five, print "Buzz" instead of the number. For numbers which are multiples of both three and five, print "FizzBuzz".

## Issue in Original Implementation

The original implementation had a logical issue in the conditional statements used to determine what to print for each number in the range from 1 to `n`.

The original code snippet for the conditional logic was:

```python
if (i % 3) == 0:
    tmp_result.append("Fizz")
elif (i % 3) == 0 and (i % 5) == 0:
    tmp_result.append("FizzBuzz")
elif (i % 5) == 0:
    tmp_result.append("Buzz")
else:
    tmp_result.append(str(i))
```

The problem with this logic is that the condition `(i % 3) == 0 and (i % 5) == 0` for "FizzBuzz" is never reached. If a number is a multiple of both 3 and 5, it will first hit the `(i % 3) == 0` condition and append "Fizz" instead of "FizzBuzz".

## Fix

The fix is to rearrange the conditional statements so that the condition for "FizzBuzz" comes before the conditions for "Fizz" and "Buzz". This ensures that numbers which are multiples of both 3 and 5 will correctly append "FizzBuzz".

The corrected code snippet is:

```python
if (i % 3) == 0 and (i % 5) == 0:
    tmp_result.append("FizzBuzz")
elif (i % 3) == 0:
    tmp_result.append("Fizz")
elif (i % 5) == 0:
    tmp_result.append("Buzz")
else:
    tmp_result.append(str(i))
```

## Conclusion

By rearranging the conditional statements, the FizzBuzz implementation now works as expected. Always remember to carefully consider the order of your conditions when multiple conditions could apply to the same input.
