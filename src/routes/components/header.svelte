<script>
    import { slide } from "svelte/transition";
    let isMenuOpen = false;
</script>
<!--Main Navbar-->
<header class="sticky top-0 z-50 bg-white shadow-lg font-roboto">
    <nav class="container mx-auto p-4 flex justify-between items-center">
        <div class="text-1xl font-bold">
            Zach <span class="text-blue-500">Conrad</span>
        </div>

        <ul class="hidden md:flex space-x-10">
            <li><a href="#about" class="hover:text-gray-400">About</a></li>
            <li><a href="#projects" class="hover:text-gray-400">Projects</a></li>
            <li><a href="#work" class="hover:text-gray-400">Work</a></li>
        </ul>
<!--Mobile Navbar-->
        <button class="md:hidden focus:outline-none"
        on:click={() => (isMenuOpen = !isMenuOpen)}
        >
        <svg
        xmlns="http://www.w3.org/2000/svg"
        class="h-6 w-6"
        fill="none"
        viewBox="0 0 24 24"
        stroke="currentColor"
      >
      <path
      stroke-linecap="round"
      stroke-linejoin="round"
      stroke-width="2"
      d="M4 6h16M4 12h16M4 18h16"
    />
        </svg>
        </button>
    </nav>
    {#if isMenuOpen}
    <ul class="md:hidden p-4 space-y-1 fixed top-0 left-0 w-full h-ful min-h-screen bg-white flex flex-col justify-center items-start" transition:slide>
      <li><a href="#about" class="block hover:text-gray-400 text-2l text-left pl-6" on:click={() => setTimeout(() => isMenuOpen = false, 300)}>About</a></li>
      <li><a href="#projects" class="block hover:text-gray-400 text-2l text-left pl-6" on:click={() => setTimeout(() => isMenuOpen = false, 300)}>Projects</a></li>
      <li><a href="#work" class="block hover:text-gray-400 text-left pl-6" on:click={() => setTimeout(() => isMenuOpen = false, 300)}>Work</a></li>
    </ul>
  {/if}
</header>

<style>
    header{
        background: #ffffff;
        box-shadow: 100px;
        padding: 20px;
        border-bottom: solid 1px #ddd;
    }
    :global(html){
        scroll-behavior: smooth;
    }
</style>