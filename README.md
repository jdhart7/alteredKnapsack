# alteredKnapsack
This program was made for Dr. Niu's algorithm class.

<h3>The Assignment:</h3>
The assignment was to create a program that solved the knapsack problem without the weights. The knapsack problem: how do you determine if a set of numbers can be used to add up to a number, k?
  
<h3>The Solution:</h3>
The solution is to create a 2D array with a width equal to the set's length and a height of K + 1. Mark (0, 0) with a 1. Then add the first element of the set to 0 and place a 1 in the sum. Copy the first row into the second, add the row's "set" number to all the positions with a 1. Copy that row into the next until you have done this for the entire set. If if the "K" position is marked, the program can stop as this indicates that the set does add up to K. An example is shown below:
  
| |0|1|2|3|4|5|6|7|8|9|10|
|-|-|-|-|-|-|-|-|-|-|-|-|
|2|1|0|1|0|0|0|0|0|0|0|0|
|2, 3|1|0|1|1|0|1|0|0|0|0|0|
|2, 3, 4|1|0|1|1|1|1|1|1|0|0|0|
|2, 3, 4, 5|1|0|1|1|1|1|1|1|1|1|1|

The left column shows the numbers currently added in the set. The top shows the numbers the set is currently able to add up to. The program found that the 10 position was marked with a 1, so the program quit; the set *can* add up to K.

<h3>How to find the numbers that add up to K:</h3>
For this, you have to start with the completed set and work backwards. You take the final chart, subtract the last number you added, then add the number you subtracted to a set. In the case of the example, you would take 10, subtract 5, then add 5 to a new array (we'll call this x). Instead of ten, x is now equal to 5. 

| |0|1|2|3|4|5|6|7|8|9|10|
|-|-|-|-|-|-|-|-|-|-|-|-|
|2|1|0|1|0|0|0|0|0|0|0|0|
|2, 3|1|0|1|1|0|1|0|0|0|0|0|
|2, 3, 4|1|0|1|1|1|1|1|1|0|0|0|
|2, 3, 4, 5|1|0|1|1|1|1|1|1|1|1|**1**|
set = {5}, x = 5

Check the next row up. If the row has a position marked greater than x, move up another row. In the case of the example, we skip the row where 4 was added to the table. 

| |0|1|2|3|4|5|6|7|8|9|10|
|-|-|-|-|-|-|-|-|-|-|-|-|
|2|1|0|1|0|0|0|0|0|0|0|0|
|2, 3|1|0|1|1|0|1|0|0|0|0|0|
|2, 3, 4|1|0|1|1|1|1|1|**1**|0|0|0|
set = {5}, x = 5

Now the highest number marked with a 1 is 5. 5 is equal to 5, so 3 gets added to the set (making the set = {5, 3}). 

| |0|1|2|3|4|5|6|7|8|9|10|
|-|-|-|-|-|-|-|-|-|-|-|-|
|2|1|0|1|0|0|0|0|0|0|0|0|
|2, 3|1|0|1|1|0|**1**|0|0|0|0|0|
set = {5, 3}, x = 2

5 is then reduced by 3 and the process continues. 

| |0|1|2|3|4|5|6|7|8|9|10|
|-|-|-|-|-|-|-|-|-|-|-|-|
|2|1|0|1|0|0|0|0|0|0|0|0|
set = {5, 3, 2}, x = 0

X is now 0, meaning that the program can stop the process. The final set = {5, 3, 2}.
