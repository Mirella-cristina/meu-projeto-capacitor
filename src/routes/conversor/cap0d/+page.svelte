<script>
	let valor = 0;
	let unidadeOrigem = 'Celsius';
	let unidadeDestino = 'Fahrenheit';
	let tipoUnidade = 'Temperatura';
	let resultado = 0;

	const unidadesTemperatura = ['Celsius', 'Fahrenheit', 'Kelvin'];
	const unidadesDistancia = ['Metro', 'Quilômetro', 'Centímetro'];

	function converterTemperatura() {
		if (unidadeOrigem === unidadeDestino) {
			resultado = valor;
			return;
		}

		if (unidadeOrigem === 'Celsius') {
			if (unidadeDestino === 'Fahrenheit') {
				resultado = (valor * 9) / 5 + 32;
			} else if (unidadeDestino === 'Kelvin') {
				resultado = valor + 273.15;
			}
		} else if (unidadeOrigem === 'Fahrenheit') {
			if (unidadeDestino === 'Celsius') {
				resultado = ((valor - 32) * 5) / 9;
			} else if (unidadeDestino === 'Kelvin') {
				resultado = ((valor - 32) * 5) / 9 + 273.15;
			}
		} else if (unidadeOrigem === 'Kelvin') {
			if (unidadeDestino === 'Celsius') {
				resultado = valor - 273.15;
			} else if (unidadeDestino === 'Fahrenheit') {
				resultado = ((valor - 273.15) * 9) / 5 + 32;
			}
		}
	}

	function converterDistancia() {
		if (unidadeOrigem === unidadeDestino) {
			resultado = valor;
			return;
		}

		if (unidadeOrigem === 'Metro') {
			if (unidadeDestino === 'Quilômetro') {
				resultado = valor / 1000;
			} else if (unidadeDestino === 'Centímetro') {
				resultado = valor * 100;
			}
		} else if (unidadeOrigem === 'Quilômetro') {
			if (unidadeDestino === 'Metro') {
				resultado = valor * 1000;
			} else if (unidadeDestino === 'Centímetro') {
				resultado = valor * 100000;
			}
		} else if (unidadeOrigem === 'Centímetro') {
			if (unidadeDestino === 'Metro') {
				resultado = valor / 100;
			} else if (unidadeDestino === 'Quilômetro') {
				resultado = valor / 100000;
			}
		}
	}

	function converter() {
		if (tipoUnidade === 'Temperatura') {
			converterTemperatura();
		} else if (tipoUnidade === 'Distância') {
			converterDistancia();
		}
	}
</script>

<main>
	<h1>Conversor de Temperatura e Distância</h1>

	<div class="control-container">
		<label for="tipoUnidade">Tipo de Unidade: </label>
		<select id="tipoUnidade" bind:value={tipoUnidade} on:change={converter}>
			<option value="Temperatura">Temperatura</option>
			<option value="Distância">Distância</option>
		</select>
	</div>

	<div class="control-container">
		<label for="valor">Valor: </label>
		<input
			type="number"
			id="valor"
			bind:value={valor}
			on:input={converter}
			placeholder="Insira o valor"
		/>
	</div>

	{#if tipoUnidade === 'Temperatura'}
		<div class="control-container">
			<label for="unidade">Unidade: </label>
			<select id="unidade" bind:value={unidadeOrigem} on:change={converter}>
				{#each unidadesTemperatura as unidade}
					<option value={unidade}>{unidade}</option>
				{/each}
			</select>
		</div>

		<div class="control-container">
			<label for="unidadeDestino">Unidade de destino: </label>
			<select id="unidadeDestino" bind:value={unidadeDestino} on:change={converter}>
				{#each unidadesTemperatura as unidade}
					<option value={unidade}>{unidade}</option>
				{/each}
			</select>
		</div>
	{/if}

	{#if tipoUnidade === 'Distância'}
		<div class="control-container">
			<label for="unidadeOrigem">Unidade de origem: </label>
			<select id="unidadeOrigem" bind:value={unidadeOrigem} on:change={converter}>
				{#each unidadesDistancia as unidade}
					<option value={unidade}>{unidade}</option>
				{/each}
			</select>
		</div>

		<div class="control-container">
			<label for="unidadeDestino">Unidade de destino: </label>
			<select id="unidadeDestino" bind:value={unidadeDestino} on:change={converter}>
				{#each unidadesDistancia as unidade}
					<option value={unidade}>{unidade}</option>
				{/each}
			</select>
		</div>
	{/if}

	<div class="result-container">
		<h2>{resultado}</h2>
	</div>
</main>

<style>
	main {
		padding: 2rem;
		font-family: 'Arial', sans-serif;
		max-width: 500px;
		margin: 10vh auto;
		background-color: #f4f4f9;
		border-radius: 12px;
		box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
		text-align: center;
	}

	h1 {
		text-align: center;
		color: #333;
		font-size: 2rem;
	}

	.control-container {
		margin-bottom: 1.5rem;
		display: flex;
		justify-content: space-between;
		align-items: center;
	}

	label {
		font-size: 1rem;
		color: #444;
	}

	input,
	select {
		padding: 0.75rem;
		font-size: 1rem;
		width: 65%;
		border-radius: 4px;
		border: 1px solid #ddd;
	}

	input:focus,
	select:focus {
		border-color: #0056b3;
		outline: none;
	}

	.result-container {
		text-align: center;
		margin-top: 2rem;
		font-size: 1.5rem;
		font-weight: bold;
		color: #333;
	}

	@media (max-width: 600px) {
		main {
			padding: 1rem;
		}

		.control-container {
			flex-direction: column;
		}

		input,
		select {
			width: 100%;
			margin-bottom: 0.5rem;
		}
	}
</style>
