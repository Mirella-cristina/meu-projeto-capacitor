<script>
	let display = $state('');
	function clear() {
		display = '';
	}

	function calc() {
		display = eval(display);
	}

	function press(c) {
		display += c;
	}

	function backspace() {
		display = str.slice(0, -1);
	}
</script>

<div class="text-center mt-3">
	<input type="text" class="form-control form-control-lg" readonly bind:value={display} />
	<table class="table table-sm table-borderless">
		<tbody>
			<tr>
				<td
					><button
						type="button"
						class="btn btn-danger w-100"
						style="background-color: #ca1444; border-color: #ca1444; "
						onclick={() => clear()}>C</button
					></td
				>
				<td
					><button
						type="button"
						class="btn btn-primary w-100"
						style="background-color: #ca1444; border-color: #ca1444; "
						onclick={() => press('(')}>&lpar;</button
					></td
				>

				<td
					><button
						type="button"
						class="btn btn-primary w-100"
						style="background-color: #ca1444; border-color: #ca1444; "
						onclick={() => press(')')}>&rpar;</button
					></td
				>
				<td
					><button
						type="button"
						class="btn btn-info w-100"
						style="background-color: #fcae11; border-color: #fcae11; "
						onclick={() => press('/')}>/</button
					></td
				>
			</tr>
			<tr>
				<td
					><button
						type="button"
						class="btn btn-primary w-100"
						style="background-color: #142738; border-color: #142738; "
						onclick={() => press(7)}>7</button
					></td
				>
				<td
					><button
						type="button"
						class="btn btn-primary w-100"
						style="background-color: #142738; border-color: #142738; "
						onclick={() => press(8)}>8</button
					></td
				>
				<td
					><button
						type="button"
						class="btn btn-primary w-100"
						style="background-color: #142738; border-color: #142738; "
						onclick={() => press(9)}>9</button
					></td
				>
				<td
					><button
						type="button"
						class="btn btn-info w-100"
						style="background-color: #fcae11; border-color: #fcae11; "
						onclick={() => press('*')}>X</button
					></td
				>
			</tr>
			<tr>
				<td
					><button
						type="button"
						class="btn btn-primary w-100"
						style="background-color: #142738; border-color: #142738; "
						onclick={() => press(4)}>4</button
					></td
				>
				<td
					><button
						type="button"
						class="btn btn-primary w-100"
						style="background-color: #142738; border-color: #142738; "
						onclick={() => press(5)}>5</button
					></td
				>
				<td
					><button
						type="button"
						class="btn btn-primary w-100"
						style="background-color: #142738; border-color: #142738; "
						onclick={() => press(6)}>6</button
					></td
				>
				<td
					><button
						type="button"
						class="btn btn-info w-100"
						style="background-color: #fcae11; border-color: #fcae11; "
						onclick={() => press('-')}>-</button
					></td
				>
			</tr>
			<tr>
				<td
					><button
						type="button"
						class="btn btn-primary w-100"
						style="background-color: #142738; border-color: #142738; "
						onclick={() => press(1)}>1</button
					></td
				>
				<td
					><button
						type="button"
						class="btn btn-primary w-100"
						style="background-color: #142738; border-color: #142738; "
						onclick={() => press(2)}>2</button
					></td
				>
				<td
					><button
						type="button"
						class="btn btn-primary w-100"
						style="background-color: #142738; border-color: #142738; "
						onclick={() => press(3)}>3</button
					></td
				>
				<td rowspan="2" style="height: 0px"
					><button
						type="button"
						class="btn btn-info w-100 h-100"
						style="background-color: #fcae11; border-color: #fcae11"
						onclick={() => press('+')}>+</button
					></td
				>
			</tr>
			<tr>
				<td
					><button
						type="button"
						class="btn btn-primary w-100"
						style="background-color: #142738; border-color: #142738; "
						onclick={() => press(0)}>0</button
					></td
				>
				<td
					><button
						type="button"
						class="btn btn-info w-100"
						style="background-color: #142738; border-color: #142738; ; color: white"
						onclick={() => press('.')}>.</button
					></td
				>
				<td
					><button
						type="button"
						class="btn btn-info w-100"
						style="background-color: #fcae11; border-color: #fcae11; "
						onclick={() => calc()}>=</button
					></td
				>
			</tr>
		</tbody>
	</table>
</div>
