# Write section on Map Reduce

## Write functions so that they can be split up, without having to require the entire data-set at once (Map)


(map inc '(1 2 3 4))

=> (2 3 4 5)




## Merge the results together (Reduce)

* E.g. Finding a running average, but returning the correct average at the end. (regular notation)

`((3 * (((2*1 + 2)/2))) + 3)/2`

is functionally equivalent to:

`(1 + 2 + 3 + 4) / 4`


This allows us to quickly find up-to-date averages on large datasets as they grow.

Which is quicker to pass as an argument?

* `'(1 2 3 4)` - but this list may grow arbitarily long. The new average is defined as the sum of all the number divided by the number of values (i.e. length of the list)
  - Values given: entire list of values
  - Passed parameters may be arbitarily long
  - `Average = sum of all values / number of values`


* `'([2 3] 4)` - where the first position in the vector is the current average, and the second position is the new value being added to the set. If the second vector value is less than 1, nil is returned (Indicating not a number / invalid input) - otherwise we prevent values < 1 being passed. (Here we are avoiding have questions of zero, and negative count averages - which may be of future value, but not now - so we note that we ignore them)
 - Values given - current average, weight, new item(s) being added to the set
 - Passed parameters - usually fixed (vector representing average is constantly size 2)
 - opens up new opportunities for arithmetic of averages
 	- E.g. gives us a benchmark of seeing if two sets are equal
   	- if two different sets can be computed to the same [avg weight] representation, then, as averages, they may be considered equal.
   	- We can compare which is greater or more accurate sample size
   	- etc
 - loses value when total count is single-processor manageable*
 - may easily be used in conjuntion with the more "straight-forward" way.
 - **Very useful for reduction**

__* "single-processor manageable"__ here means the total number of values sits within memory constrainsts of a single process, on a single core of a processor, and computed within an acceptable time frame.

Combinations of the two methods may be used to build large values very quickly.



* Another example - multiplication of large numbers or very small (large floating point) numbers. 
 - They can be divided up into parts to be calculated, and merged together