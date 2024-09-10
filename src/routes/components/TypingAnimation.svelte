<script>
	import { onMount } from 'svelte';

	export let texts = ["I'm a web developer.", "I'm a student.", "I'm a software developer."];

	let displayText = '';
	let index = 0;
	let textIndex = 0;

	const typingSpeed = 200;
	const pauseBetweenTexts = 2000;
	const deleteSpeed = 50;

	function typeWriter() {
		let currentText = texts[textIndex];

		if (index < currentText.length) {
			displayText += currentText.charAt(index);
			index++;
			setTimeout(typeWriter, typingSpeed);
		} else {
			setTimeout(() => deleteText(), pauseBetweenTexts);
		}
	}

	function deleteText() {
		if (index > 0) {
			displayText = displayText.slice(0, -1);
			index--;
			setTimeout(deleteText, deleteSpeed);
		} else {
			textIndex = (textIndex + 1) % texts.length;
			setTimeout(typeWriter, typingSpeed);
		}
	}

	onMount(() => {
		typeWriter();
	});
</script>

<div class="text-2xl font-mono inline-block">
	{displayText}
	<span class="border-r-2 border-white animate-typing-cursor"></span>
</div>

<style>
	@keyframes blink {
		0%,
		50% {
			opacity: 1;
		}
		50%,
		100% {
			opacity: 0;
		}
	}

	.animate-typing-cursor {
		animation: blink 1s steps(1) infinite;
	}
</style>
