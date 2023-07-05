//ttt
<template>
    <div class="tic-tac-toe">
      <h1>Tic Tac Toe</h1>
      <div class="board-container">
        <div class="board">
          <div class="row" v-for="(row, rowIndex) in board" :key="rowIndex">
            <div
              class="cell"
              v-for="(cell, colIndex) in row"
              :key="colIndex"
              @click="makeMove(rowIndex, colIndex)"
            >
              {{ cell }}
            </div>
          </div>
        </div>
      </div>
      <div class="reset-container">
        <button @click="resetBoard">Reset</button>
      </div>
      <p class="message">{{ message }}</p>
    </div>
  </template>
  <script>
  export default {
    name: 'TicTacToe',
    data() {
      return {
        currentPlayer: 'X',
        board: [
          ['', '', ''],
          ['', '', ''],
          ['', '', '']
        ],
        message: ''
      };
    },
    methods: {
      makeMove(rowIndex, colIndex) {
        if (this.board[rowIndex][colIndex] === '') {
          this.board[rowIndex][colIndex] = this.currentPlayer;
          this.checkGameStatus();
          this.currentPlayer = this.currentPlayer === 'X' ? 'O' : 'X';
        }
      },
      checkGameStatus() {
        const winningCombinations = [
          [[0, 0], [0, 1], [0, 2]],
          [[1, 0], [1, 1], [1, 2]],
          [[2, 0], [2, 1], [2, 2]],
          [[0, 0], [1, 0], [2, 0]],
          [[0, 1], [1, 1], [2, 1]],
          [[0, 2], [1, 2], [2, 2]],
          [[0, 0], [1, 1], [2, 2]],
          [[0, 2], [1, 1], [2, 0]]
        ];
  
        for (let combination of winningCombinations) {
          const [a, b, c] = combination;
          const [rowA, colA] = a;
          const [rowB, colB] = b;
          const [rowC, colC] = c;
  
          if (
            this.board[rowA][colA] &&
            this.board[rowA][colA] === this.board[rowB][colB] &&
            this.board[rowA][colA] === this.board[rowC][colC]
          ) {
            this.message = `${this.board[rowA][colA]} wins!`;
            return;
          }
        }
  
        if (this.checkBoardFilled()) {
          this.message = "It's a tie!";
        }
      },
      checkBoardFilled() {
        for (let row of this.board) {
          for (let cell of row) {
            if (cell === '') {
              return false;
            }
          }
        }
        return true;
      },
      resetBoard() {
        this.board = [
          ['', '', ''],
          ['', '', ''],
          ['', '', '']
        ];
        this.currentPlayer = 'X';
        this.message = '';
      }
    }
  };
  </script>
  <style>
  .tic-tac-toe {
    background-color: rgb(89, 178, 234);
    text-align: center;
    margin-top: 80px;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  }
  h1 {
  font-size: 32px;
  margin-bottom: 20px;
  color: rgb(19, 42, 97);
  margin-bottom: 120px;
  }
  .board-container {
    display: flex;
    justify-content: center;
    margin-bottom: 60px;
  }
  
  .board {
  border: 2px solid #ccc;
  border-radius: 8px;
  padding: 10px;
  display: flex;
  flex-wrap: wrap;
  width: 154px;
  }
  
  .row {
    display: flex;
    width: 100%;
  }
  
  .cell {
 width: 50px;
  height: 50px;
  border: 1px solid #ccc;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 24px;
  cursor: pointer;
  background-color: #efc756; 
  transition: background-color 0.3s ease; /* Tambahkan efek transisi saat dihover */
}
  
  .reset-container {
    display: flex;
    justify-content: center;
    margin-top: 20px;
  }
  .cell.X {
  color: #007bff;
}

.cell.O {
  color: #e11111;
}

.cell:hover {
  background-color: #d1e666; /* Efek latar belakang saat dihover */
}

.reset-container {
  margin-top: 20px;
}
  button {
    padding: 10px 20px;
  background-color: rgb(230, 117, 30);
  color: #fff;
  border: none;
  cursor: pointer;
  border-radius: 4px;
  font-size: 16px;
  transition: background-color 0.3s ease;
  }
  button:hover {
  background-color: #efc756; /* Efek latar belakang saat dihover */
}
  .message {
    margin-top: 20px;
    font-size: 18px;
    font-weight: bold;
  }
  </style>