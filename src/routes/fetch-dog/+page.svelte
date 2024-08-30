<script>
	let dogImage = '';
	let showImage = false;
	let error = null;

	async function fetchDogImage() {
		try {
			dogImage = '';
			error = null;
			const response = await fetch('https://dog.ceo/api/breeds/image/random');
			const data = await response.json();
			if (data.status === 'success') {
				dogImage = data.message;
			} else {
				error = data.message;
			}
		} catch (error) {
			error = error;
		}
	}

	$: {
		if (showImage) {
			fetchDogImage();
		}
	}
</script>

<main class="space-y-4">
	<h1 class="text-3xl">Fetch Dog</h1>

	{#if showImage}
		<button on:click={() => (showImage = false)} class="bg-red-500 btn"> Hide Image </button>
	{:else}
		<button on:click={() => (showImage = true)} class="bg-blue-500 btn"> Show Image </button>
	{/if}

	<br />

	{#if showImage}
		{#if dogImage}
			<img src={dogImage} alt="Random Dog" class="rounded-md" />
		{:else if error}
			<p class="text-red-500">Error: {error.toString()}</p>
		{:else}
			<p>Loading...</p>
		{/if}
	{/if}
</main>

<style lang="postcss">
	.btn {
		@apply text-white px-4 py-2 rounded-md;
	}
</style>
