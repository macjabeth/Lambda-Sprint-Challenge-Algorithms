## Exercise I

### A

```
a)  a = 0
    while (a < n * n * n):
      a = a + n * n
```

Problem `a` has a runtime complexity of `O(n^3)`, or `n` cubed.

This is because the while loop is dependent upon the input size, and inside the condition we're multiply `n` by itself three times (or to the third power - hence cubed).

### B

```
b)  sum = 0
    for i in range(n):                    O(n)
      i += 1
      for j in range(i + 1, n):             O(n-i+1)
        j += 1
        for k in range(j + 1, n):           O(n-j+1)
          k += 1
          for l in range(k + 1, 10 + k):    O(9)
            l += 1
            sum += 1
```

So, going off of what I have above (which I hope is correct), the runtime complexity of this problem would be `O(n*m*k)` because we start out with the first loop which is of variable size `n`. Inside of this loop, we have two other nested loops that loop up to a length of `n` but are not exactly the same because their starting points depend upon the index of their containing loop. The final loop is always going to run 10 times, so we can assume it's constant time and leave it out of our calculation.

### C

```
c)  def bunnyEars(bunnies):
      if bunnies == 0:
        return 0

      return 2 + bunnyEars(bunnies-1)
```

Recursive functions make my mind bleed a little, but I believe the runtime complexity of this snippet is linear, or `O(n)`. This is the case because it executes once every time it decrements the value of `bunnies`, and it decrements the value until it reaches 0, meaning the function is called recursively `bunnies` times.

## Exercise II

So, we have a building of variable length `n`, and eggs are broken if they're dropped from a floor `f` or higher... however, we're only concerned with the number of *dropped* eggs, not whether they're cracked or not.

I'll assume then that we're only taking one input here - `n` for the number of stories in the building.

And for our output, we need to return `f` - the floor that *minimises* the amount of dropped eggs.

At what floor could we throw it off of where we minimise the amount of eggs that are dropped? Perhaps this seems like too simple a solution... but if we always returned the first floor, then we'd minimize the amount of eggs that could be dropped by `n-1`. It would save us from throwing eggs off every floor above it. This would have a runtime complexity of O(1) because we'd only have to run one operation regardless of input size.

```
def getEggingFloor(n):
    # Ground Floor will just return false
    if n == 0: return False
    # return the first floor which minimises the number of eggs that could be dropped
    return 1
```
