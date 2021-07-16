<script>
	export let showOnPx = 150;
	let hidden = true;

	function goTop() {
		document.body.scrollIntoView();
	}

	function scrollContainer() {
		return document.documentElement || document.body;
	}

	function handleOnScroll() {
		if (!scrollContainer()) {
			return;
		}

		if (scrollContainer().scrollTop > showOnPx) {
			hidden = false;
		} else {
			hidden = true;
		}
	}
</script>

<svelte:window on:scroll={handleOnScroll} />

<button class="back-to-top w-12 h-12 align-middle justify-center" on:click={goTop} class:hidden
	><i class="fas fa-angle-up fa-4x text-red-500" /></button
>

<style>
	.back-to-top {
		opacity: 1;
		transition: opacity 1s, visibility 1s;
		position: fixed;
		z-index: 99;
		user-select: none;
		right: 1rem;
		bottom: 1rem;
	}

	.back-to-top.hidden {
		opacity: 0;
		visibility: hidden;
	}
</style>
