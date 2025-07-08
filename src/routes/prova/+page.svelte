<script>
    let board = Array(9).fill(null);
    let currentPlayer = 'X';
    let clickedIndex = null;
    function handleClick(index) {
      if (board[index]) {
        clickedIndex = index;
        setTimeout(() => (clickedIndex = null), 300);
        return;
      }
      board[index] = currentPlayer;
      currentPlayer = currentPlayer === 'X' ? 'O' : 'X';
    }
  
    function resetGame() {
      board = Array(9).fill(null);
      currentPlayer = 'X';
      clickedIndex = null;
    }
  </script>
  
  <style>
    .game-container {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      min-height: 100vh;
      font-family: sans-serif;
      background: #f2f2f2;
      padding: 1rem;
    }
  
    .board {
      display: grid;
      grid-template-columns: repeat(3, 80px);
      gap: 10px;
    }
  
    .cell {
      width: 80px;
      height: 80px;
      background: white;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 2rem;
      border: 2px solid #ccc;
      border-radius: 10px;
    }
  
    .cell:hover {
      cursor: pointer;
    }
  d {
      animation: shake 0.3s ease-in-out;
      background: #ffcdd2;
    }
  
    @keyframes shake {
      0% { transform: translateX(0px); }
      25% { transform: translateX(-4px); }
      50% { transform: translateX(4px); }
      75% { transform: translateX(-4px); }
      100% { transform: translateX(0px); }
    }
  
    button {
      margin-top: 20px;
      padding: 10px 20px;
      background: #1976d2;
      color: white;
      border: none;
      border-radius: 8px;
      font-size: 1rem;
    }
  
    button:hover {
      background: #1565c0;
      cursor: pointer;
    }
  
    .turn {
      margin-top: 1rem;
      font-size: 1.2rem;
      color: #b8219f;
    }
  </style>
    .occupie
  
  <div class="game-container">
    <div class="board">
      {#each board as cell, index}
        <div
          class="cell {clickedIndex === index ? 'occupied' : ''}"
          on:click={() => handleClick(index)}
        >
          {cell}
        </div>
      {/each}
    </div>
  
    <button on:click={resetGame}>jogar novamente</button>
    <div class="turn">Vez de: {currentPlayer}</div>
  </div>
