<script lang="ts">
	/// Show/hide extra navbar items on mobile devices
	function toggleNavbar(collapseID) {
		document.getElementById(collapseID).classList.toggle('hidden');
		document.getElementById(collapseID).classList.toggle('block');
	}
</script>

<nav class="top-0 absolute z-50 w-full flex flex-wrap items-center justify-between px-2 py-3 ">
	<div class="container px-4 mx-auto flex flex-wrap items-center justify-between">
		<div class="w-full relative flex justify-between lg:w-auto lg:static lg:block lg:justify-start items-end">
			<div>
				<i class="text-green-500 pr-2 fas fa-money-check-alt fa-2x" />
				<a
					class="font-extrabold leading-relaxed inline-block mr-4 py-2 whitespace-nowrap uppercase hover:text-green-500"
					href="#todo"
					>Digital Payment Awareness</a
				>
			</div>
			<button
				class="cursor-pointer text-xl leading-none px-3 py-1 border border-solid border-transparent rounded bg-transparent block lg:hidden outline-none focus:outline-none"
				type="button"
				on:click={() => toggleNavbar('mobile-hamburger-menu')}
			>
				<i class="text-green-500 fas fa-caret-down fa-2x" />
			</button>
		</div>
		<div
			class="lg:flex flex-grow items-center lg:bg-transparent bg-gray-800 lg:ring-0 ring-1 ring-white rounded-lg"
			id="mobile-hamburger-menu"
		>
			<ul class="flex flex-col lg:flex-row list-none lg:ml-auto">
				<li class="flex items-center">
					<a class="px-3 py-4 lg:py-2 flex items-center text-xs uppercase font-bold" href="#todo"
						><i class="text-blue-500 fas fa-file-alt text-lg leading-lg " /><span
							class="inline-block lg:ml-2 ml-6 mr-6">Blogs</span
						></a
					>
				</li>
				<li class="flex items-center">
					<a class="px-3 py-4 lg:py-2 flex items-center text-xs uppercase font-bold" href="#todo"
						><i class="text-yellow-500 fas fa-newspaper text-lg leading-lg" /><span
							class="inline-block lg:ml-2 ml-4 mr-6">Articles</span
						></a
					>
				</li>
				<li class="flex items-center">
					<a class="px-3 py-4 lg:py-2 flex items-center text-xs uppercase font-bold" href="#todo"
						><i class="text-red-500 fab fa-youtube text-lg leading-lg " /><span
							class="inline-block lg:ml-2 ml-4">Videos</span
						></a
					>
				</li>
			</ul>
		</div>
	</div>
</nav>
