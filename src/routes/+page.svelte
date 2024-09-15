<script>
	import Header from './components/header.svelte';
	import Footer from './components/footer.svelte';
	import { fade } from 'svelte/transition';

	import TypingAnimation from './components/TypingAnimation.svelte';
	let texts = ['software developer.', 'website developer.', 'student.'];
</script>

<Header />

<main>
	<div
		class="hero-section h-screen w-screen flex bg-slate-50 items-center font-roboto"
		id="about"
		transition:fade
	>
		<div class="container mx-auto">
			<h1 class="text-4xl font-bold">Hello, I'm Zach.</h1>
			<p class="font-mono text-2xl">I'm a <TypingAnimation {texts} /></p>
		</div>
	</div>
	<div id="projects"></div>
	<p>Projects</p>
	<div id="work"></div>
	<p>Work</p>
</main>

<Footer />

<style>
	main {
		max-width: 960px;
		margin: 0 auto;
		padding-top: 0;
	}
	.hero-section {
		width: 100vw;
		margin-left: calc(-50vw + 50%);
	}
</style>
