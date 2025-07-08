<script>
	import { dicionario } from '$lib/dicionario.js';
	import { goto } from '$app/navigation';

	let palavra = '';
	let filtradas = dicionario;

	function buscar() {
		const termoBusca = palavra.trim().toLowerCase();

		if (termoBusca === '') {
			filtradas = dicionario;
			return;
		}

		filtradas = dicionario.filter(t =>
			t.palavra.toLowerCase().startsWith(termoBusca)
		);
	}

	function aleatorio() {
		const indiceAleatorio = Math.floor(Math.random() * dicionario.length);
		const termo = dicionario[indiceAleatorio].palavra;
		goto(`/dicionario/${termo}`);
	}
</script>

<style>
	main {
		max-width: 500px;
		margin: 2rem auto;
		padding: 1rem;
		font-family: 'Segoe UI', sans-serif;
	}

	h1 {
		text-align: center;
		font-size: 1.5rem;
		margin-bottom: 1rem;
	}

	input {
		width: 100%;
		padding: 0.6rem;
		font-size: 1rem;
		border: 1px solid #ccc;
		border-radius: 6px;
		margin-bottom: 1rem;
	}

	button {
		width: 100%;
		background-color: #007BFF;
		color: white;
		border: none;
		padding: 0.6rem;
		font-size: 1rem;
		border-radius: 6px;
		cursor: pointer;
		transition: background-color 0.3s ease;
		margin-bottom: 1.5rem;
	}

	button:hover {
		background-color: #0056b3;
	}

	ol {
		padding-left: 1.2rem;
	}

	li {
		margin-bottom: 0.4rem;
	}

	a {
		color: #007BFF;
		text-decoration: none;
	}

	a:hover {
		text-decoration: underline;
	}
</style>

<main>
	<h1>Digite uma palavra</h1>

	<input
		type="text"
		placeholder="Digite uma palavra"
		bind:value={palavra}
		on:input={buscar}
	/>

	<button type="button" on:click={aleatorio}>
		Palavra aleatória do dia
	</button>

	<ol>
		{#each filtradas as termo}
			<li>
				<a href={`/dicionario/${termo.palavra}`}>{termo.palavra}</a>
			</li>
		{/each}
	</ol>
</main>
