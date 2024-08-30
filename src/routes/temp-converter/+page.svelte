<script>
	let celsius = 0;
	let fahrenheit = 32;

	function handleFahrenheitInput(event) {
		const newFahrenheit = parseInt(event.target.value);
		if (!isNaN(newFahrenheit)) {
			fahrenheit = newFahrenheit;
			celsius = ((fahrenheit - 32) * 5) / 9;
		} else {
			celsius = (-32 * 5) / 9;
		}
	}

	function handleCelsiusInput(event) {
		const newCelsius = parseInt(event.target.value);
		if (!isNaN(newCelsius)) {
			celsius = newCelsius;
			fahrenheit = (celsius * 9) / 5 + 32;
		} else {
			fahrenheit = 32;
		}
	}
</script>

<section class="space-y-4">
	<h1 class="text-3xl">Temperature Converter</h1>

	<div class="flex flex-col">
		<label for="celsius" class="text-xl">Celsius</label>
		<input
			type="number"
			placeholder="Enter temperature in Celsius"
			bind:value={celsius}
			class="border p-2"
			on:input={handleCelsiusInput}
		/>
	</div>

	<div class="flex flex-col">
		<label for="fahrenheit" class="text-xl">Fahrenheit</label>
		<input
			type="number"
			placeholder="Enter temperature in Fahrenheit"
			bind:value={fahrenheit}
			class="border p-2"
			on:input={handleFahrenheitInput}
		/>
	</div>
</section>
