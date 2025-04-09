<script>
    let contador = 10;

    import { onMount } from 'svelte';

    let confetti;

    onMount(() => {
        confetti = window.confetti;
    });

    function bloquear(segundos) {
        return new Promise((resolve) => {
            setTimeout(() => {
                console.log('Desbloqueando...');
                resolve();
            }, segundos * 1000);
        });
    }

    async function iniciarContagem() {
        for (let i = 10; i > 0; i--) {
            contador = i;
            await bloquear(1);
        }
        contador = 0;
        estourarConfetes(); 
    }

    function estourarConfetes() {
        if (confetti) {
            confetti({
                particleCount: 500, 
                spread: 70, 
                origin: { y: 0.6 } 
            });
        }
    }

    iniciarContagem();
</script>

<svelte:head>
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
    <link rel="icon" href="/favicon.ico" />
</svelte:head>

<style>
    
    body {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh; 
        margin: 0; 
        background-color: #f0f0f0; 
        font-family: Arial, sans-serif; 
    }

    h1 {
        font-size: 2.5rem;
        text-align: center;
        margin-bottom: 20px;
        color: #333;
    }

    h3 {
        font-size: 3rem;
        text-align: center;
        color: #ff4500; 
    }
</style>

<h1>Contagem Regressiva</h1>

{#if contador > 0}
    <h3>{contador}</h3>
{:else}
    <h3>🎉 Tempo esgotado! 🎉</h3>
{/if}
