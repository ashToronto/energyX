#Running the program
There are no dependencies, opted for built in minitest instead of rspec.
execute ``` ruby run.rb ``` to view inputs
execute ``` ruby nasa_command_test.rb ``` to run test suite 

## The Grid
1 The first line of input is the upper-right coordinates of the plateau
2 The lower-left coordinates are assumed to be 0,0.

##The Rovers
1   A rover's position and the location is represented by a combination of x and y coordinates and a letter representing one of the four cardinal compass points.
2   The plateau is divided up into a grid to simplify navigation.
3   To control a rover, NASA sends a simple string of letters. The possible letters are 'L', 'R' and 'M'. 'L' and 'R' makes the rover spin 90 degrees left or right respectively
4   'M' means move forward one grid point, and maintain the same heading.
5   Assume that the square directly North from (x, y) is (x, y+1).

##Understanding the Test Input

5 5                 --> grid upper right corner 0,0 will be lower left thus giving us size of the rectangular grid/plateau
1 2 N               --> Rovers initial position: x and y coordinates and bearing: N S E W
LMLMLMLMM           --> rover movement commands  
3 3 E               --> Second rover only starts when first is done
MMRMMRMRRM          --> Second rover movement commands

##Understanding the Expected Output

1 3 N               --> Final coordinates and bearing Rover 1
5 1 E               --> Final coordinates and bearing Rover 2

##Key Considerations
1 Rovers can only turn left and right
2 Rovers can move of the grid meaning they get destroyed or out of communication from NASA

##Solution Breakdown
1 N S E W can be defined as an array of [0,1,2,3] this means that y+1 will turn the direction
2 When the rover moves Left it should execute -1 and wehn we go Right we should perform +1
3 When we move forward it'll either be + or -
4 The square directly North from (x, y) is (x, y+1) that means South will be (x, y-1)
