<script lang="ts">
	import Header from './components/header.svelte';
	import Footer from './components/footer.svelte';
</script>

<Header />

<main>
	<div class="flex flex-col items-center justify-center text-center mt-8 font-roboto">
		<p class="mt-4 text-xl text-gray-600 font-bold">Error 404</p>
		<a href="/" class="mt-6 px-4 py-2 bg-blue-500 text-white rounded hover:bg-blue-600">
			Go back Home
		</a>
	</div>
</main>

<Footer />

<style>
	main {
		max-width: 960px;
		margin: 40px auto;
	}
</style>
