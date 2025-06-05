<script>
	import '../app.css';
	import CursorGlow from './components/cursorGlow.svelte';
	import { injectAnalytics } from '@vercel/analytics/sveltekit'
	injectAnalytics();
</script>

<CursorGlow />


<slot />
