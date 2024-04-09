Build a simple console-based Tic-Tac-Toe game that
allows two players to play against each other

TASK 3

TIC-TAC-TOE GAME

Game Board: Create a 3x3 grid as the game board.
Players: Assign
"X"
and "O" to two players.

Display Board: Show the current state of the board.
Player Input: Prompt the current player to enter their move.
Update Board: Update the game board with the player
'
s move.

Check for Win: Check if the current player has won.
Check for Draw: Determine if the game is a draw.
Switch Players: Alternate turns between
"X"
and "O"

players.

Display Result: Show the result of the game (win, draw, or ongoing).
Play Again: Ask if the players want to play another game.

#include <iostream>
#include <array>

using namespace std;

// Function to display the Tic-Tac-Toe board
void display_board(const array<array<char, 3>, 3>& board) {
    for (const auto& row : board) {
        for (char cell : row) {
            cout << cell << " ";
        }
        cout << endl;
    }
}

// Function to check if the current player has won
bool check_win(const array<array<char, 3>, 3>& board, char player) {
    // Check rows and columns
    for (int i = 0; i < 3; ++i) {
        if (board[i][0] == player && board[i][1] == player && board[i][2] == player) return true;
        if (board[0][i] == player && board[1][i] == player && board[2][i] == player) return true;
    }
    // Check diagonals
    if (board[0][0] == player && board[1][1] == player && board[2][2] == player) return true;
    if (board[0][2] == player && board[1][1] == player && board[2][0] == player) return true;
    return false;
}

// Function to check if the game is a draw
bool check_draw(const array<array<char, 3>, 3>& board) {
    for (const auto& row : board) {
        for (char cell : row) {
            if (cell == ' ') return false;
        }
    }
    return true;
}

int main() {
    array<array<char, 3>, 3> board = { ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ' };
    char player = 'X';
    bool game_over = false;

    cout << "Welcome to Tic-Tac-Toe!" << endl;
    cout << "Player 1: X, Player 2: O" << endl;

    while (!game_over) {
        // Display the board
        display_board(board);

        // Get player's move
        int row, col;
        cout << "Player " << player << ", enter your move (row and column): ";
        cin >> row >> col;

        // Update the board
        if (row >= 1 && row <= 3 && col >= 1 && col <= 3 && board[row - 1][col - 1] == ' ') {
            board[row - 1][col - 1] = player;

            // Check for win
            if (check_win(board, player)) {
                display_board(board);
                cout << "Player " << player << " wins!" << endl;
                game_over = true;
            }
            // Check for draw
            else if (check_draw(board)) {
                display_board(board);
                cout << "It's a draw!" << endl;
                game_over = true;
            }
            // Switch players
            else {
                player = (player == 'X') ? 'O' : 'X';
            }
        } else {
            cout << "Invalid move! Please enter again." << endl;
        }
    }

    char play_again;
    cout << "Do you want to play again? (Y/N): ";
    cin >> play_again;

    if (play_again == 'Y' || play_again == 'y') {
        // Reset the board and player
        board = { ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ' };
        player = 'X';
        game_over = false;
        main();
    } else {
        cout << "Thanks for playing!" << endl;
    }

    return 0;
}


This code implements a basic console-based Tic-Tac-Toe game with features such as displaying the board, player input, updating the board, checking for a win or draw, switching players, displaying the result, and allowing players to play again.
