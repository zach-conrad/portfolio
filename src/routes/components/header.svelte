<script>
	let isMenuOpen = false;
	import { fly, fade } from 'svelte/transition';
</script>

<!--Main Navbar-->
<header class="sticky top-0 z-50 bg-white shadow-lg font-roboto">
	<nav class="container mx-auto p-4 flex justify-between items-center">
		<a href="/">
			<div class="text-1xl font-bold z-50">
				Zach <span class="text-blue-500">Conrad</span>
			</div>
		</a>

		<ul class="hidden md:flex space-x-10">
			<li><a href="#about" class="hover:text-gray-400 transition-colors duration-300">About</a></li>
			<li>
				<a href="#projects" class="hover:text-gray-400 transition-colors duration-300">Projects</a>
			</li>
			<li><a href="#work" class="hover:text-gray-400 transition-colors duration-300">Work</a></li>
		</ul>

		<!--Mobile Navbar (Hamburger to X)-->
		<button class="md:hidden focus:outline-none z-50" on:click={() => (isMenuOpen = !isMenuOpen)}>
			<div class="hamburger-icon">
				<span class="line top" class:open={isMenuOpen}></span>
				<span class="line middle" class:open={isMenuOpen}></span>
				<span class="line bottom" class:open={isMenuOpen}></span>
			</div>
		</button>
	</nav>

	<!--Mobile menu-->
	{#if isMenuOpen}
		<div class="menu" in:fade={{ duration: 300 }}>
			<ul
				class="md:hidden p-4 space-y-20 fixed top-0 left-0 w-full min-h-screen bg-white font-roboto font-bold flex flex-col justify-center items-start z-40"
			>
				<li>
					<a
						href="#about"
						class="block hover:text-gray-400 text-2xl text-left pl-6 drop-shadow-lg"
						on:click={() => (isMenuOpen = false)}
						transition:fly={{ duration: 500, x: -500 }}>About</a
					>
				</li>
				<li>
					<a
						href="#projects"
						class="block hover:text-gray-400 text-2xl text-left pl-6 drop-shadow-lg"
						on:click={() => (isMenuOpen = false)}
						transition:fly={{ duration: 600, x: -500 }}>Projects</a
					>
				</li>
				<li>
					<a
						href="#work"
						class="block hover:text-gray-400 text-2xl text-left pl-6 drop-shadow-lg"
						on:click={() => (isMenuOpen = false)}
						transition:fly={{ duration: 700, x: -500 }}>Work</a
					>
				</li>
			</ul>
		</div>
	{/if}
</header>

<style>
	header {
		background: #ffffff;
		padding: 20px;
		box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
		border-bottom: solid 1px #ddd;
	}

	:global(html) {
		scroll-behavior: smooth;
	}

	.menu {
		position: fixed;
		top: 0;
		left: 0;
		right: 0;
		bottom: 0;
		background-color: white;
		z-index: 49;
		transition: opacity 0.3s ease-in-out;
	}

	.hamburger-icon {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		width: 40px;
		height: 24px;
		cursor: pointer;
		position: relative;
		z-index: 50;
	}

	.line {
		background-color: black;
		height: 2px;
		width: 36px;
		transition: all 0.3s ease-in-out;
		position: absolute;
		transform-origin: center;
	}

	/* Set initial positions for top and bottom lines */
	.top {
		top: 0;
	}

	.middle {
		top: 50%;
		transform: translateY(-50%);
	}

	.bottom {
		bottom: 0;
	}

	/* Rotate and animate into "X" */
	:global(.open.top) {
		transform: translateY(11px) rotate(45deg);
	}

	:global(.open.middle) {
		opacity: 0;
	}

	:global(.open.bottom) {
		transform: translateY(-11px) rotate(-45deg);
	}

	/* Z-index of the full menu should be lower than the button */
	ul {
		z-index: 40;
	}
</style>
