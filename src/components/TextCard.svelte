<script lang="ts">
	export let routeID: string = 'err: routing id prop not passed';
	export let title: string = 'err: title prop not passed';
	export let subtitle: string = 'err: subtitle prop not passed';
	export let img: string = 'err: image prop not passed';
	export let time: string = 'err: time to read prop not passed';
	export let color: string = 'text-pink-500';
	export let icon: string = 'fa-question'
</script>

<div class="mx-auto">
	<div class="bg-gray-900 shadow-md rounded-lg mb-6 tracking-wide">
		<div class="md:flex-shrink-0">
			<img src={img} alt="cover" class="w-full h-64 object-cover" />
		</div>
		<div class="px-4 py-2 mt-2">
			<div class="flex items-top">
				<i class="fas {icon} {color} mr-2 transform fa-2x" />
				<h2 class="font-bold text-2xl tracking-normal">{title}</h2>
			</div>
			<p class="text-sm text-gray-300 h-32 overflow-hidden">{subtitle}</p>
			<div class="pl-1 mt-4 flex items-center">
				<i class="fas fa-clock {color} mr-2" />
				<p class="text-gray-500 text-xs">{time}</p>
			</div>
			<a href={routeID} class="cursor-pointer pl-2 mt-4 flex items-center">
				<i class="fas fa-angle-down {color} mr-2 transform scale-150" />
				<p class="{color}">Read More</p>
			</a>
		</div>
	</div>
</div>
