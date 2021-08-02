<script lang="ts">
	export let shown = false;
	function toggleMenu() {
		shown = !shown;
	}
</script>

<nav class="shadow bg-gray-900 fixed z-10 w-full">
	<div class="container px-6 py-2 mx-auto md:flex md:justify-between md:items-center">
		<div class="flex justify-between">
			<div class="text-center">
				<p class="text-md font-medium uppercase tracking-wider">
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
			<div class="flex justify-start text-center md:flex">
				<div class="flex flex-col md:flex-row md:mx-6 pt-4">
					<a href="#blog">
						<button
							class="font-medium hover:text-blue-500 py-1 px-4 border border-transparent hover:border-blue-500 rounded flex flex-row items-center"
						>
							<i class="text-blue-500 fas fa-file-alt mr-2" />
							<p class="text-sm font-medium uppercase">Blogs</p>
						</button>
					</a>
					<a href="#tutorial">
						<button
							class="font-medium hover:text-yellow-500 py-1 px-4 border border-transparent hover:border-yellow-500 rounded flex flex-row items-center"
						>
							<i class="text-yellow-500 fas fa-chalkboard-teacher mr-2" />
							<p class="text-sm font-medium uppercase">Tutorials</p>
						</button>
					</a>
					<a href="#video">
						<button
							class="font-medium hover:text-red-500 py-1 px-4 border border-transparent hover:border-red-500 rounded flex flex-row items-center"
						>
							<i class="text-red-500 fab fa-youtube mr-2" />
							<p class="text-sm font-medium uppercase">Video</p>
						</button>
					</a>
					<a href="https://github.com/Az-21/digital-payment-awareness">
						<button
							class="font-medium hover:text-gray-400 py-1 px-4 border border-transparent hover:border-gray-400 rounded flex flex-row items-center"
						>
							<i class="text-gray-400 fab fa-github mr-2" />
							<p class="text-sm font-medium uppercase">GitHub</p>
						</button>
					</a>
				</div>
			</div>
		{:else}
			<div class="hidden md:flex">
				<div class="flex flex-col md:flex-row md:mx-6">
					<a href="#blog">
						<button
							class="font-medium hover:text-blue-500 py-1 px-4 border border-transparent hover:border-blue-500 rounded flex flex-row items-center"
						>
							<i class="text-blue-500 fas fa-file-alt mr-2" />
							<p class="text-sm font-medium uppercase">Blogs</p>
						</button>
					</a>
					<a href="#tutorial">
						<button
							class="font-medium hover:text-yellow-500 py-1 px-4 border border-transparent hover:border-yellow-500 rounded flex flex-row items-center"
						>
							<i class="text-yellow-500 fas fa-chalkboard-teacher mr-2" />
							<p class="text-sm font-medium uppercase">Tutorials</p>
						</button>
					</a>
					<a href="#video">
						<button
							class="font-medium hover:text-red-500 py-1 px-4 border border-transparent hover:border-red-500 rounded flex flex-row items-center"
						>
							<i class="text-red-500 fab fa-youtube mr-2" />
							<p class="text-sm font-medium uppercase">Video</p>
						</button>
					</a>
					<a href="https://github.com/Az-21/digital-payment-awareness">
						<button
							class="font-medium hover:text-gray-400 py-1 px-4 border border-transparent hover:border-gray-400 rounded flex flex-row items-center"
						>
							<i class="text-gray-400 fab fa-github mr-2" />
							<p class="text-sm font-medium uppercase">GitHub</p>
						</button>
					</a>
				</div>
			</div>
		{/if}
	</div>
</nav>
