# alteredKnapsack
This program was made for Dr. Niu's algorithm class.

<h3>The Assignment:</h3
The assignment was to create a program that solved the knapsack problem without the weights. The knapsack problem: how do you determine if a set of numbers can be used to add up to a number, k?
  
  </h3>The Solution:</h3>
  The solution is to create a 2D array with a width equal to the set's length and a height of K + 1. Mark (0, 0) with a 1. Then add the first element of the set to 0 and place a 1 in the sum. Copy the first row into the second, add the row's "set" number to all the positions with a 1. Copy that row into the next until you have done this for the entire set. If if the "K" position is marked, the program can stop as this indicates that the set does add up to K. An example is shown below:
  
| |0|1|2|3|4|5|6|7|8|9|10|
|-|-|-|-|-|-|-|-|-|-|-|-|
|2|1|0|1|0|0|0|0|0|0|0|0|
|2, 3|1|0|1|1|-|1|0|0|0|0|0|
|2, 3, 4|1|0|1|1|1|1|1|1|0|0|0|
|2, 3, 4, 5|1|0|1|1|1|1|1|1|1|1|1|
