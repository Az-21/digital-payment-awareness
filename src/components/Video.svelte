<script lang="ts">
	export let title: string = 'err: title prop not passed';
	export let subtitle: string = 'err: subtitle prop not passed';
	export let link: string = 'err: video link prop not passed';
	export let time: string = 'err: time to read prop not passed';
</script>

<div class="w-full">
	<div class="bg-gray-900 shadow-md rounded-lg mb-6 tracking-wide">
		<div class="md:flex-shrink-0 lg:h-96 h-56">
			<iframe {title} width="100%" height="100%" src={link} frameborder="0" allowfullscreen />
		</div>
		<div class="px-4 py-2 mt-2">
			<div class="flex items-top">
				<i class="fab fa-youtube text-red-500 mr-2 transform fa-2x" />
				<h2 class="font-bold text-2xl tracking-normal">{title}</h2>
			</div>
			<p class="text-sm text-gray-300 overflow-hidden">{subtitle}</p>
			<div class="pl-1 mt-4 flex items-center">
				<i class="fas fa-clock text-red-500 mr-2 transform scale-150" />
				<p class="text-gray-500 text-xs">{time}</p>
			</div>
		</div>
	</div>
</div>
