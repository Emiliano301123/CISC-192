Tic-Tac-Toe Game Assignment (C++)

// Name: Emiliano Cardoso Aguiniga

// Course: CISC 192 - C++ Programming

// Date: 11/16/2025

// Assignment: Tic Tac Toe


    #include <iostream>
    using namespace std;

    class TicTacToe {
    private:
    char board[3][3];        
    char currentPlayer;      
    int moveCount;          
    bool gameOver;          
    
    public:
        TicTacToe() {
            initializeBoard();
            currentPlayer = 'X'; 
            moveCount = 0;
            gameOver = false;
        }

    void initializeBoard() {
        for(int i = 0; i < 3; i++) {
            for(int j = 0; j < 3; j++) {
                board[i][j] = ' ';
            }
        }
    }

    // Display of the game
    void displayBoard() {
        cout << "\n  1   2   3" << endl; 
        for(int i = 0; i < 3; i++) {
            cout << i + 1 << " "; 
            for(int j = 0; j < 3; j++) {
                cout << board[i][j];
                if(j < 2) cout << " | ";
            }
            cout << endl;
            if(i < 2) cout << "  ---------" << endl;
        }
        cout << endl;
    }

    bool isValidMove(int row, int col) {
        int r = row - 1;
        int c = col - 1;

        if(r < 0 || r > 2 || c < 0 || c > 2) {
            cout << "Invalid move! Row and column must be between 1 and 3.\n";
            return false;
        }
        if(board[r][c] != ' ') {
            cout << "That position is already taken! Choose another.\n";
            return false;
        }

        return true;
    }

    // Place the move on the display
    void makeMove(int row, int col) {
        int r = row - 1;
        int c = col - 1;

        board[r][c] = currentPlayer;
        moveCount++;

        cout << "Player " << currentPlayer << " placed at (" << row << "," << col << ")\n";
    }

    // Check if there's a winner
    bool checkWinner() {
        // Check all rows
        for(int i = 0; i < 3; i++) {
            if(board[i][0] != ' ' && board[i][0] == board[i][1] && board[i][1] == board[i][2]) {
                return true;
            }
        }

        for(int j = 0; j < 3; j++) {
            if(board[0][j] != ' ' && board[0][j] == board[1][j] && board[1][j] == board[2][j]) {
                return true;
            }
        }

        if(board[0][0] != ' ' && board[0][0] == board[1][1] && board[1][1] == board[2][2]) {
            return true;
        }
        if(board[0][2] != ' ' && board[0][2] == board[1][1] && board[1][1] == board[2][0]) {
            return true;
        }

        return false;
    }

    bool isDraw() {
        return (moveCount == 9 && !checkWinner());
    }

    // Switch to other user
    void switchPlayer() {
        currentPlayer = (currentPlayer == 'X') ? 'O' : 'X';
    }

    void playGame() {
        cout << "Tic-Tac-Toe" << endl;
        cout << "Player 1: X" << endl;
        cout << "Player 2: O" << endl;
        cout << "Enter row and column numbers (1-3) to make your move.\n" << endl;

        displayBoard();

        while(!gameOver) {
            int row, col;
            bool validMove = false;

            // Get the move from user
            while(!validMove) {
                cout << "Player " << currentPlayer << "'s turn." << endl;
                cout << "Enter Row (1-3): ";
                cin >> row;
                cout << "Enter Column (1-3): ";
                cin >> col;

                validMove = isValidMove(row, col);
            }

            makeMove(row, col);
            displayBoard();

            // Check for a winner
            if(checkWinner()) {
                cout << "Player " << currentPlayer << " wins! " << endl;
                gameOver = true;
            }
            // Check if there is a  draw
            else if(isDraw()) {
                cout << "It's a draw" << endl;
                gameOver = true;
            }
            else {
                switchPlayer();
            }
        }

        cout << "\nGame Over" << endl;
    }
    };
    
    // Main function
    int main() {
        TicTacToe game;
        game.playGame();
        return 0;
    }
