<script>
	let email = '';
	let postagens = [];
	let erro = '';

	async function buscarPostagens() {
		erro = '';
		postagens = [];

		const resposta = await fetch(`https://jsonplaceholder.typicode.com/users?email=${email}`);
		const usuarios = await resposta.json();

		const usuario = usuarios[0]

		if (!usuario) {
			erro = 'Usuário não encontrado 😢';
			return;
		}

		const respostaPostagens = await fetch(
			`https://jsonplaceholder.typicode.com/posts?userId=${usuario.id}`
		);
		postagens = await respostaPostagens.json();
	}
</script>

<input type="email" bind:value={email} placeholder="Digite o e-mail do usuário" />

<button on:click={buscarPostagens}>Buscar</button>

{#if erro}
	<p style="color: red;">{erro}</p>
{/if}

{#if postagens.length > 0}
	<h3>Postagens de {email}:</h3>
	<ul>
		{#each postagens as p}
			<li>{p.title}</li>
		{/each}
	</ul>
{/if}
