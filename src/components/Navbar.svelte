<script lang="ts">
	export let shown = true;
	function toggleMenu() {
		shown = !shown;
	}
</script>

<nav class="shadow bg-gray-900 fixed z-50 w-full">
	<div class="container px-6 py-2 mx-auto md:flex md:justify-between md:items-center">
		<div class="flex items-center justify-between">
			<div>
				<p class="text-md font-medium uppercase md:place-content-center">
					Digital Payment Awareness
				</p>
			</div>

			<!-- Mobile menu button -->
			<div class="flex md:hidden">
				<button on:click={() => toggleMenu()}>
					<i class="fas fa-bars" />
				</button>
			</div>
		</div>

		<!-- Mobile Menu open: "block", Menu closed: "hidden" -->
		{#if shown}
			<div class="items-center md:flex">
				<div class="flex flex-col md:flex-row md:mx-6">
					<a class="text-sm font-medium hover:text-blue-500 md:mx-4 md:my-0" href="#blog">Blogs</a>
					<a class="text-sm font-medium hover:text-yellow-500 md:mx-4 md:my-0" href="#tutorial"
						>Tutorials</a
					>
					<a class="text-sm font-medium hover:text-red-500 md:mx-4 md:my-0" href="#video">Videos</a>
					<a
						class="text-sm font-medium hover:text-gray-400 md:mx-4 md:my-0"
						href="https://github.com/Az-21/digital-payment-awareness">GitHub</a
					>
				</div>
			</div>
		{/if}
	</div>
</nav>
