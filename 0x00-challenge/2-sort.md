# Ruby Sorting Script - Issue and Fix

## Introduction

This Ruby script sorts integer arguments in ascending order. The script takes a list of arguments, filters out non-integer values, and then sorts the integers.

## Issue in Original Implementation

The original implementation had a logical issue in the part of the code responsible for inserting each integer into the `result` array at the correct position. The problematic line was:

```ruby
result.insert(i - 1, i_arg)
```

This line attempts to insert `i_arg` at the position `(i - 1)` in the `result` array. However, the value of `i` is already pointing to the correct position where `i_arg` should be inserted, making the `- 1` unnecessary and incorrect.

## Fix

The fix is simple: change the line to insert `i_arg` at the position `i` in the `result` array. The corrected line is:

```ruby
result.insert(i, i_arg)
```

With this change, the script correctly sorts the integers in ascending order.

## Corrected Code

Here's the corrected code snippet:

```ruby
# ... (previous code)

# insert result at the right position
is_inserted = false
i = 0
l = result.size
while !is_inserted && i < l do
    if result[i] < i_arg
        i += 1
    else
        result.insert(i, i_arg)  # Corrected this line
        is_inserted = true
        break
    end
end
result << i_arg if !is_inserted

# ... (next code)
```

## Conclusion

By correcting the position at which each integer is inserted into the `result` array, the Ruby sorting script now works as expected. Always remember to carefully consider array indices when inserting elements into an array.
