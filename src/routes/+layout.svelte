<script>
	import '../app.css';
	import Header from './Header.svelte';
</script>

<div class="flex flex-col min-h-screen">
	<Header />
	<main class="flex-1 flex flex-col p-4 w-full max-w-screen-md mx-auto">
		<slot />
	</main>
</div>
