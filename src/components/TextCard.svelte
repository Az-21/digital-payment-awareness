<script lang="ts">
	export let routeID: string = 'err: routing id prop not passed';
	export let title: string = 'err: title prop not passed';
	export let subtitle: string = 'err: subtitle prop not passed';
	export let img: string = 'err: image prop not passed';
	export let time: string = 'err: time to read prop not passed';
	export let color: string = 'text-pink-500';
	// export let icon: string = 'fa-question';
</script>

<div class="mx-auto min-w-full">
	<div class="bg-gray-900 shadow-md mb-6 tracking-wide">
		<div class="md:flex-shrink-0">
			<img src={img} alt="cover" class="w-full h-64 object-cover" />
		</div>
		<div class="px-4 py-2 mt-2">
			<div class="flex items-center">
				<!-- <i class="fas {icon} {color} mr-2 transform fa-2x" /> -->
				<h2 class="font-bold text-lg tracking-normal h-12">{title}</h2>
			</div>
			<div class="pt-4 flex flex-row mt-2">
				<i class="fas fa-clock {color} mr-2" />
				<p class="text-gray-500 text-xs">{time}</p>
			</div>
			{#if subtitle != '...'}
				<p class="text-sm text-gray-300 h-32 overflow-hidden">{subtitle}</p>
				<a href={routeID} class="cursor-pointer mt-4 flex items-center justify-center">
					<i class="fas fa-angle-down {color} mr-2 transform scale-150" />
					<p class={color}>Read More</p>
				</a>
			{:else}
				<a href={routeID} class="cursor-pointer mt-2 flex items-center justify-center">
					<i class="fas fa-angle-down {color} mr-2 transform scale-150" />
					<p class={color}>Read</p>
				</a>
			{/if}
		</div>
	</div>
</div>
