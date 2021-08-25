# plot four

The game of **"plot four"** or "connect four" is as follows. It consists of a grid with 6 rows and 7 columns. The grid is placed vertically on a table. There are two players, with pieces coloured red and yellow respectively. The pieces are flat disks that can be dropped into the grid. Once dropped into a column of the grid, **a piece always travels to the bottommost unoccupied cell of that column.** Observe that if no column is filled up, there are exactly seven possible moves in each step. The player who first has four pieces arranged in a consecutive manner vertically, horizontally or diagonally, wins.

## problem statement

**Design a program to enable a gameplay between two players in the terminal.** The first player's pieces are marked as **'o'** while the second players pieces are marked as **'x'**. Your program should alternately request the first and second player to input the column number for their move. **If no move is possible at the given column number then your program should print error and repeat the request.** The state of the grid after each move should be displayed in the terminal. A typical state may look like this:

| . | . | . | . | . | . | . |	

| . | . | . | . | . | . | . |	

| . | . | . | . | . | . | . |

| . | . | . | x | . | . | . |

| . | . | x | o | . | . | . |

| . | x | o | x | o | . | . |

When a player wins, your program should end the game and acknowledge his victory.

## C++ code

```cpp
#include<iostream>
using namespace std;

int a[7][8] = { {0} };

int sol(int a[][8])
{
	int flag = 0;
	//for horizontal matching
	for (int row = 6; row >= 1; row--)
	{
		for (int i = 1; i <= 4; i++)
		{
			if (a[row][i]!=0 && a[row][i] == a[row][i + 1] && a[row][i + 1] == a[row][i + 2] && a[row][i + 2] == a[row][i + 3])
			{
				flag = 1;
				break;
			}
		}
	}
	//for vertical matching
	for (int col = 1; col <= 7; col++)
	{
		for (int i = 6; i >= 4; i--)
		{
			if (a[i][col] != 0 && a[i][col] == a[i - 1][col] && a[i - 1][col] == a[i - 2][col] && a[i - 2][col] == a[i - 3][col])
			{
				flag = 1;
				break;
			}
		}
	}

	//for right diagonal matching
	for (int col = 1; col <= 4; col++)
	{
		for (int row = 6; row >= 4; row--)
		{
			if (a[row][col] != 0 && a[row][col] == a[row - 1][col + 1] && a[row - 1][col + 1] == a[row - 2][col + 2] && a[row - 2][col + 2] == a[row - 3][col + 3])
			{
				flag = 1;
				break;
			}
		}
	}

	//for left diagonal matching
	for (int col = 7; col >= 4; col--)
	{
		for (int row = 6; row >= 4; row--)
		{
			if (a[row][col] != 0 && a[row][col] == a[row - 1][col - 1] && a[row - 1][col - 1] == a[row - 2][col - 2] && a[row - 2][col - 2] == a[row - 3][col - 3])
			{
				flag = 1;
				break;
			}
		}
	}
	return flag;
}

int fill(int a[][8], int col, int player)
{
	int flag = 0;
	for (int i = 6; i >= 1; i--)
	{
		if (a[i][col] == 0)
		{
			a[i][col] = player;
			flag = 1;
			break;
		}
	}
	return flag;
}

void display()
{
	for (int row = 1; row <= 6; row++)
	{
		for (int col = 1; col <= 7; col++)
		{
			if (a[row][col] == 0)
				cout << " . ";
			else if (a[row][col] == 1)
				cout << " o ";
			else if (a[row][col] == 2)
				cout << " x ";
		}
		cout << endl;
	}

}

int main()
{
	int i;
	int x, temp = 0;
	while (!temp)
	{

		//---------------player 1's turn

		cout << "player 1's turn ( o ):: enter the column number -  ";
		cin >> x;
		cout << endl;

	    i = fill(a, x, 1);
		while (!i)
		{
			cout << "error, enter different column number -  ";
			cin >> x;
			cout << endl;
			i = fill(a, x, 1);
		}

		temp = sol(a);
		display();
		if (temp == 1)
		{
			cout <<endl<< "**WINNER WINNER CHICKEN DINNER**" << endl<<" player 1 wins ";
			break;
		}

		//---------------player 2's turn

		cout << "player 2's turn ( x ) :: enter the column number -  ";
		cin >> x;
		cout << endl;

	    i = fill(a, x, 2);
		while (!i)
		{
			cout << "error, enter different column number -  ";
			cin >> x;
			cout << endl;
			i = fill(a, x, 2);
		}

		temp = sol(a);
		display();
		if (temp == 1)
		{
			cout << endl << "**WINNER WINNER CHICKEN DINNER**" << endl << " player 2 wins ";
			break;
		}
		
	}

	return 0;
}
```
