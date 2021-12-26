# 335-project-1
Implementing algorithms

Group members:

Malka Lazerson mlazerson@csu.fullerton.edu

Ada Lovelace adalovelace@csu.fullerton.edu

Charles Babbage charlesbab@csu.fullerton.edu

Project 1: implementing algorithms
CPSC 335 - Algorithm Engineering
Fall 2021
Instructors: Doina Bein (dbein@fullerton.edu)

The Alternating Disk Problem

You have a row of 2n disks of two colors, n light and n dark. They alternate: light, dark, light, dark, and so on. You want to get all the light disks to the left-hand end, and all the dark disks to the right-hand end. The only moves you are allowed to make are those that interchange the positions of two adjacent disks (i.e. they touch each other). No other moves are allowed. Design an algorithm for solving this puzzle and determine the number of moves it takes.

The alternating disks problem is: 

Input: a positive integer n and a list of 2n disks of alternating colors light-dark, starting with light
Output: a list of 2n disks, the first n disks are light, the next n disks are dark, and an integer m representing the number of swaps to move the dark ones after the light ones.

There are two algorithms, presented below, that solve this problem in O(n2) time. An improvement can be obtained by not going all the way to the left or to the right, since some disks at the ends are already in the correct position. You need to translate the descriptions of the two algorithms into clear pseudocode. You are allowed to do the improvements as long as it does not change the description of the algorithm.
The first algorithm proceeds like a lawnmower: starts with the leftmost disk and proceeds to the right until it reaches the rightmost disk: compares every two adjacent disks and swaps them only if necessary. Now we have two light disks at the left-hand end and two dark disks at the right-hand end. Once it reaches the right-hand end, it starts with the rightmost disk, compares every two adjacent disks and proceeds to the left until it reaches the leftmost disk, doing the swaps only if necessary. The lawnmower movement is repeated (n+1)/2 times. Some improvement can be obtained by not going all the way to the left or to the right, since some disks at the ends are already in the correct position.

The second algorithm has n+1 runs. In each run, every two disks are compared and swap only if necessary. The first run compares the first and second disk, the third and fourth disk, the fifth and the sixth disk, etc.. The second run compares the second and third disk, the fourth and the fifth, the sixth and the seventh disk, etc.. The third run is a repetition of the first run. The fourth run is a repetition of the second run, etc.. Again, swaps are done only if necessary. Run 1, 3, etc. starts with the leftmost disk and proceeds to the right until it reaches the rightmost disk: compares every two adjacent disks and swaps them only if necessary. Now we have one light disk at the left-hand end and the dark disk at the right-hand end. Run 2, 4, etc. starts with the second leftmost disk and proceeds to the right until it reaches the second rightmost disk: compares every two adjacent disks and swaps them only if necessary. There are a total of n+1 runs.

The lawnmower algorithm:

It starts with the leftmost disk and proceeds to the right until it reaches the rightmost disk: compares every two adjacent disks and swaps them only if necessary. Now we have two light disks at the left-hand end and two dark disks at the right-hand end. Once it reaches the right-hand end, it starts with the rightmost disk, compares every two adjacent disks and proceeds to the left until it reaches the leftmost disk, doing the swaps only if necessary. The lawnmower movement is repeated ⌈n/2⌉ times. 
Consider the example below when n=4, and the first row is the input configuration, the second row is the end of comparison from left to right, the third row is the end of the first run (round trip that contains left to right followed by right to left), etc.. 

The alternate algorithm:

It starts with the leftmost disk and proceeds to the right until it reaches the rightmost disk: compares every two adjacent disks and swaps them only if necessary. It does not iterate through each index, but iterates over each pair (i.e., it moves 2 steps at a time). We consider a run to be a check of adjacent disks from left-to-right.
Next it starts with the second leftmost disk and proceeds to the right until it reaches the second rightmost disk: compares every two adjacent disks and swaps them only if necessary.  This is the end of Run 2. Now we have two light disks at the left-hand end and two dark disks at the right-hand end. Next it is Run 3 that proceeds exactly as Run 1, starting with the leftmost disk. Run 3 is followed by Run 4 that is exactly as Run 2, starting with the second leftmost disk. So really, Run 1 and Run 2 continually alternate until sorting has finished. 
There are a total of  n+1 runs.
Consider the example below when n=4, and the first row is the input configuration, the second row is the end of run 1, the third row is the end of run 2, etc..
