<script>
	let isMenuOpen = false;
	import { fly, fade } from 'svelte/transition';
</script>

<!--Main Navbar-->
<header class="sticky top-0 z-50 bg-white shadow-lg font-roboto">
	<nav class="container mx-auto p-4 flex justify-between items-center">
		<a href="/">
			<!--Logo-->
			<div class="text-1xl font-bold z-50 sticky">
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
			<svg
				class="md:hidden p-4 space-y-20 fixed font-roboto font-bold flex flex-col justify-end items-center z-40"
				xmlns="http://www.w3.org/2000/svg"
				x="0px"
				y="0px"
				width="24"
				height="24"
				viewBox="0 0 24 24"
			>
				<path
					d="M10.9,2.1c-4.6,0.5-8.3,4.2-8.8,8.7c-0.6,5,2.5,9.3,6.9,10.7v-2.3c0,0-0.4,0.1-0.9,0.1c-1.4,0-2-1.2-2.1-1.9 c-0.1-0.4-0.3-0.7-0.6-1C5.1,16.3,5,16.3,5,16.2C5,16,5.3,16,5.4,16c0.6,0,1.1,0.7,1.3,1c0.5,0.8,1.1,1,1.4,1c0.4,0,0.7-0.1,0.9-0.2 c0.1-0.7,0.4-1.4,1-1.8c-2.3-0.5-4-1.8-4-4c0-1.1,0.5-2.2,1.2-3C7.1,8.8,7,8.3,7,7.6C7,7.2,7,6.6,7.3,6c0,0,1.4,0,2.8,1.3 C10.6,7.1,11.3,7,12,7s1.4,0.1,2,0.3C15.3,6,16.8,6,16.8,6C17,6.6,17,7.2,17,7.6c0,0.8-0.1,1.2-0.2,1.4c0.7,0.8,1.2,1.8,1.2,3 c0,2.2-1.7,3.5-4,4c0.6,0.5,1,1.4,1,2.3v3.3c4.1-1.3,7-5.1,7-9.5C22,6.1,16.9,1.4,10.9,2.1z"
				></path>
			</svg>
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
		z-index: 40;
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
