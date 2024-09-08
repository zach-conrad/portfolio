<script>
    let isMenuOpen = false;
    import { fly } from 'svelte/transition';
</script>

<!--Main Navbar-->
<header class="sticky top-0 z-50 bg-white shadow-lg font-roboto">
    <nav class="container mx-auto p-4 flex justify-between items-center">
        <div class="text-1xl font-bold z-50">
            Zach <span class="text-blue-500">Conrad</span>
        </div>

        <ul class="hidden md:flex space-x-10">
            <li><a href="#about" class="hover:text-gray-400">About</a></li>
            <li><a href="#projects" class="hover:text-gray-400">Projects</a></li>
            <li><a href="#work" class="hover:text-gray-400">Work</a></li>
        </ul>

        <!--Mobile Navbar (Hamburger to X)-->
        <button class="md:hidden focus:outline-none z-50" on:click={() => isMenuOpen = !isMenuOpen}>
            <div class="hamburger-icon">
                <span class="line top" class:open={isMenuOpen}></span>
                <span class="line middle" class:open={isMenuOpen}></span>
                <span class="line bottom" class:open={isMenuOpen}></span>
            </div>
        </button>
    </nav>

    <!--Mobile menu-->
    {#if isMenuOpen}
    <ul class="md:hidden p-4 space-y-20 fixed top-0 left-0 w-full min-h-screen bg-white font-roboto font-bold flex flex-col justify-center items-start z-40">
        <li><a href="#about" class="block hover:text-gray-400 text-2xl text-left pl-6 drop-shadow-lg" on:click={() => isMenuOpen = false} transition:fly={{duration: 500, x: -500}}>About</a></li>
        <li><a href="#projects" class="block hover:text-gray-400 text-2xl text-left pl-6 drop-shadow-lg" on:click={() => isMenuOpen = false} transition:fly={{duration: 600, x: -500}}>Projects</a></li>
        <li><a href="#work" class="block hover:text-gray-400 text-2xl text-left pl-6 drop-shadow-lg" on:click={() => isMenuOpen = false} transition:fly={{duration: 700, x: -500}}>Work</a></li>
    </ul>
    {/if}
</header>

<style>
    header {
        background: #ffffff;
        box-shadow: 100px;
        padding: 20px;
        border-bottom: solid 1px #ddd;
    }

    :global(html) {
        scroll-behavior: smooth;
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
