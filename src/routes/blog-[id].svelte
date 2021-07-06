<script lang="ts">
	// Get the routeID
	const url = window.location.href.split('/');
	const id = url[url.length - 1].split('-')[1];

	// JSON Data
	import { blog } from '../content/BlogJSON.svelte';

    // External functions
	import { estimateTimeToRead } from '../components/Functions.svelte';

    import Footer from '../components/Footer.svelte'

	// Create array of paragraphs
	const listContent = blog[id].content.split('\n\n');
</script>

<div class="w-3/5 mx-auto pb-24">
    <p class="text-5xl pt-24 font-bold">{blog[id].title}</p>
	<p class= "pt-4 text-sm font-medium text-blue-500">{estimateTimeToRead(blog[id].content)} • Published {blog[id].date}</p>
	<img class="pt-4 h-64 w-full object-cover" src={blog[id].img} alt="" />
	{#each listContent as paragraph}
		<p class="pt-8">{paragraph}</p>
	{/each}
</div>

<Footer />