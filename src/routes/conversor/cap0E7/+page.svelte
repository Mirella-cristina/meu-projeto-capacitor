<script>
    let city = '';
    let usuarios = [];

    async function buscarUsuariosPorCidade(event) {
        event.preventDefault(); 
        let resposta = await fetch(`https://jsonplaceholder.typicode.com/users?%{city}`);
        let todosUsuarios = await resposta.json();

        usuarios = todosUsuarios.filter(user => user.address.city.toLowerCase() === cidade.toLowerCase());
    }
</script>

<form on:submit={buscarUsuariosPorCidade}>
    <input type="text" placeholder="Nome da cidade" bind:value={city} />
    <button>Buscar usuários</button>
</form>

{#if usuarios.length > 0}
    <h2>Usuários em {city}</h2>
    <ul>
        {#each usuarios as usuario}
            <li>
                <strong>{usuario.name}</strong> - {usuario.email}
            </li>
        {/each}
    </ul>
{:else if city}
    <p>Nenhum usuário encontrado em "{city}".</p>
{/if}
