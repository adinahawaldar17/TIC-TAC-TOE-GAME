# TIC-TAC-TOE-GAME
"Play the classic game of Tic-Tac-Toe in your console with this C++ implementation. Challenge a friend to a match, take turns, and aim to be the first to get three in a row. Enjoy hours of fun and sharpen your strategic thinking with this simple yet engaging game."

#include <iostream>

using namespace std;

char board[3][3] = { {' ', ' ', ' '}, {' ', ' ', ' '}, {' ', ' ', ' '} };
char player1 = 'X';
char player2 = 'O';
char currentPlayer = player1;

bool isGameOver() {
  for (int i = 0; i < 3; i++) {
    if (board[i][0] == board[i][1] && board[i][1] == board[i][2] && board[i][0] != ' ') {
      return true;
    }
    if (board[0][i] == board[1][i] && board[1][i] == board[2][i] && board[0][i] != ' ') {
      return true;
    }
  }
  if (board[0][0] == board[1][1] && board[1][1] == board[2][2] && board[0][0] != ' ') {
    return true;
  }
  if (board[2][0] == board[1][1] && board[1][1] == board[0][2] && board[2][0] != ' ') {
    return true;
  }
  for (int i = 0; i < 3; i++) {
    for (int j = 0; j < 3; j++) {
      if (board[i][j] == ' ') {
        return false;
      }
    }
  }
  return true;
}

int main() {

  cout << "Tic Tac Toe" << endl;
  cout << "player 1: " << player1 << endl;
  cout << "Player 2: " << player2 << endl;
  cout << endl;
  cout << "  1 2 3" << endl;
  cout << "A | " << board[0][0] << " | " << board[0][1] << " | " << board[0][2] << " |" << endl;
  cout << "B | " << board[1][0] << " | " << board[1][1] << " | " << board[1][2] << " |" << endl;
  cout << "C | " << board[2][0] << " | " << board[2][1] << " | " << board[2][2] << " |" << endl;

  while (!isGameOver()) {
    int row, column;
    cout << endl << "Player " << currentPlayer << ", enter your move (row column): ";
    cin >> row >> column;
    if (row < 1 || row > 3 || column < 1 || column > 3) {
      cout << "Invalid move. Please try again." << endl;
      continue;
    }
    if (board[row - 1][column - 1] != ' ') {
      cout << "That space is already taken. Please try again." << endl;
      continue;
    }
    board[row - 1][column - 1] = currentPlayer;
    cout << endl << "  1 2 3" << endl;
    cout << "A | " << board[0][0] << " | " << board[0][1] << " | " << board[0][2] << " |" << endl;
    cout << "B | " << board[1][0] << " | " << board[1][1] << " | " << board[1][2] << " |" << endl;
    cout << "C | " << board[2][0] << " | " << board[2][1] << " | " << board[2][2] << " |" << endl;

    if (currentPlayer == player1) {
      currentPlayer = player2;
    } else {
      currentPlayer = player1;
    }
  }

  if (currentPlayer == player1) {
    cout << "Player 1 wins!" << endl;
  } else {
    cout << "Player 2 wins!" << endl;
  }

  return 0;
}
