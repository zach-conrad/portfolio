<script lang="ts">
    import { onMount, onDestroy } from 'svelte';
    import { browser } from '$app/environment';
  
    let x = 0;
    let y = 0;
  
    function updateMousePosition(e: MouseEvent) {
      x = e.clientX;
      y = e.clientY;
    }
  
    onMount(() => {
      if (browser) {
        window.addEventListener('mousemove', updateMousePosition);
      }
    });
  
    onDestroy(() => {
      if (browser) {
        window.removeEventListener('mousemove', updateMousePosition);
      }
    });
  </script>
  
  {#if browser}
    <div
      class="pointer-events-none fixed top-0 left-0 w-32 h-32 rounded-full bg-blue-500 opacity-30 blur-3xl z-50 transition-transform duration-100"
      style="transform: translate(calc({x}px - 50%), calc({y}px - 50%));"
    ></div>
  {/if}
  