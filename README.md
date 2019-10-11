#plot four

The game of "plot four" or "connect four" is as follows. It consists of a grid with 6 rows and 7 columns. The grid is placed vertically on a table. There are two players, with pieces coloured red and yellow respectively. The pieces are flat disks that can be dropped into the grid. Once dropped into a column of the grid, a piece always travels to the bottommost unoccupied cell of that column. Observe that if no column is filled up, there are exactly seven possible moves in each step. The player who first has four pieces arranged in a consecutive manner vertically, horizontally or diagonally, wins.

#problem statement

1) Design a program to enable a gameplay between two players in the terminal. The first player's pieces are marked as 'o' while the second players pieces are marked as 'x'. Your program should alternately request the first and second player to input the column number for their move. If no move is possible at the given column number then your program should print error and repeat the request. The state of the grid after each move should be displayed in the terminal. A typical state may look like this:

| . | . | . | . | . | . | . |	

| . | . | . | . | . | . | . |	

| . | . | . | . | . | . | . |

| . | . | . | x | . | . | . |

| . | . | x | o | . | . | . |

| . | x | o | x | o | . | . |

When a player wins, your program should end the game and acknowledge his victory.
