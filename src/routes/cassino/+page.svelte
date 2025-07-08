<script>
    import { goto } from "$app/navigation";
  </script>
  
  <!-- Conteúdo centralizado e responsivo -->
  <div class="container-fluid min-vh-100 d-flex flex-column justify-content-center align-items-center bg-light p-4 text-center">
  
    <h1 class="mb-3 fw-bold text-warning d-flex align-items-center justify-content-center gap-2">
      mirellaBET
      <img src="tigrinho.png" alt="Mascote MirellaBET" width="64" height="64">
    </h1>
  
    <p class="fs-5 mb-2">🎰 Bem-vindo ao <strong>mirellaBET</strong>!</p>
    <p class="fs-6 mb-4">Escolha o que deseja gerar:</p>
  
    <!-- Grade de botões responsiva -->
    <div class="w-100" style="max-width: 420px;">
      <div class="d-grid gap-3">
  
        <button class="btn btn-primary btn-lg" on:click={() => goto('/cassino/numeros')}>
          🎲 Números Aleatórios
        </button>
  
        <button class="btn btn-success btn-lg" on:click={() => goto('/cassino/embaralhar')}>
          🔀 Embaralhar Lista
        </button>
  
        <button class="btn btn-danger btn-lg" on:click={() => goto('/cassino/dados')}>
          🎲 Jogar Dados
        </button>
  
        <button class="btn btn-warning btn-lg text-dark" on:click={() => goto('/cassino/roleta')}>
          🎡 Roleta
        </button>
  
        <button class="btn btn-dark btn-lg" on:click={() => goto('/cassino/moeda')}>
          🪙 Cara ou Coroa
        </button>
  
        <button class="btn btn-info btn-lg text-white" on:click={() => goto('/cassino/niquel')}>
          🐯 Caça Níquel
        </button>
  
        <button class="btn btn-secondary btn-lg" on:click={() => goto('/cassino/megasena')}>
          💰 Mega Sena
        </button>
  
      </div>
    </div>
  
  </div>
  