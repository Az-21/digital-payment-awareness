<script lang="ts">
	export let title: string = 'err: title prop not passed';
	export let subtitle: string = 'err: subtitle prop not passed';
	export let img: string = 'err: image prop not passed';
	export let time: string = 'err: time to read prop not passed';
</script>

<div class="mx-auto">
	<div class="bg-gray-900 shadow-md rounded-lg mb-6 tracking-wide">
		<div class="md:flex-shrink-0">
			<img src={img} alt="cover" class="w-full h-64 object-cover" />
		</div>
		<div class="px-4 py-2 mt-2">
			<h2 class="font-bold text-2xl tracking-normal">{title}</h2>
			<p class="text-sm text-gray-300 h-32 overflow-hidden">{subtitle}</p>
			<p class="text-gray-500 text-xs pt-2">{time}</p>
			<div class="mt-4 flex items-center">
				<i class="fas fa-angle-down text-blue-500 mr-2 transform scale-150" />
				<a href="#todo:route" class="text-blue-500">Read More</a>
			</div>
		</div>
	</div>
</div>
