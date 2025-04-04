# Quicksort Pivots

in the lectures I only briefly mentioned strategies for determining a good pivot
for quicksort. The implementation on the slides simply picks the leftmost
element in the part of the array that we consider as a pivot. I also mentioned a
few other ways of picking a good pivot, e.g. randomly.

Median-of-three is also a good way of picking a pivot -- inspect the first,
middle, and last elements of the part of the array under consideration and
choose the median value. Using the probabilities for picking a pivot in a
particular part of the array (in the same way as we did on slide 34), argue
whether this method is more or less (or equally) likely to pick a good pivot
compared to simply choosing the first element. Assume that all permutations are
equally likely, i.e. the input array is ordered randomly.

Your answer must derive probabilities for choosing a good pivot and
quantitatively reason with them.

From the slides, picking the first element as the pivot gives an odd of n/2 of being a good pivot. 

Median-of-three chooses a pivot from three examined value, choosing the median/middle value of the ones inspected. 

Using the chart from the slides as reference, a table representing a good value in array can be split into three sections. There is the first n/4 (values too low to be a good pivot), the middle section from n/4 to 3n/4 (the middle values representing a good pivot), and the last values from 3n/4 to n (values too high to be a good pivot). Overall the odds for a good or bad pivot is n/2, but because median-of-three chooses a median value, a too low bad pivot will be differentiated from a too high bad pivot. 

- L - too low bad pivot, probability of n/4
- G - good pivot, probability of n/2
  - to use mathematically, G will be treated as two values when calculating probability to match the lower probability of n/4
- H - too high bad pivot, probability of n/4

As G makes up two portions of n/4, it can count as two separate probabilites when computing total possible number of combinations (counts for n/4 to n/2 and n/2 to 3n/4). With 4 options for 3 values, there are $4^3 = 64$ possible combinations (with 2 G's). For there to be a good pivot, at least one G must be present in the combination and there cannot be two L's or H's. If there are, one of the L's or H's will be selected as the median value (GHH, LLG, etc for bad pivot selections). Examples of combinations that will give good pivots are LHG, GGL, GHG, etc. 

For 2 options (L or H) for 3 values, there are $2^3 = 8$ possible combinations where G is not present. 

There are six combinations where there are 2 L's or 2 G's: LLG, LGL, GLL, HHG, HGH, and GHH. Accounting for the two distinct G values, there are 12  in terms of the 64 combinations.

Thus there are $8 + 12 = 20$ combinations out of the total 64 where a good pivot will not be chosen. Thus there are $64 - 20 = 44$ combinations of the 64 where a good pivot can be selected. Then the odds of selecting a good pivot are $44n/64 = 11n/16$. 

The probability of 11n/16 for median-of-three is much higher than the n/2 probability for picking the first element as the pivot, thus giving median-of-three a higher probability of selecting a good pivot than picking the first element. 

Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.

“I certify that I have listed all sources used to complete this exercise, including the use of any Large Language Models. All of the work is my own, except where stated otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is suspected, charges may be filed against me without prior notice.” - Natalie Sleight
