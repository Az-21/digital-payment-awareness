<script lang="ts">
	export let text: string = 'todo: pass section title text';
    export let textColor: string = 'text-white';
    export let divColor: string = 'divide-white';
</script>

<div class="divide-y-4 {divColor} w-5/6 mx-auto">
	<div class="flex text-3xl font-black pt-6 {textColor} uppercase">
		{text}
	</div>
	<div class="pb-10"/>
</div>
