<script lang="ts">
	// Get the routeID
	const url = window.location.href.split('/');
	const id = url[url.length - 1].split('-')[1];

	// JSON Data
	import { article } from '../content/ArticleJSON.svelte';

    // External functions
	import { estimateTimeToRead } from '../components/Functions.svelte';

    import Footer from '../components/Footer.svelte';

	// Create array of paragraphs
	const listContent = article[id].content.split('\n\n');
</script>

<div class="w-5/6 lg:w-3/5 mx-auto pb-24">
    <p class="text-5xl pt-24 font-bold">{article[id].title}</p>
	<p class= "pt-4 text-sm font-medium text-yellow-500">{estimateTimeToRead(article[id].content)} • Published {article[id].date}</p>
	<img class="pt-4 h-64 w-full object-cover" src={article[id].img} alt="" />
	{#each listContent as paragraph}
		<p class="pt-8 font-serif text-xl tracking-wide">{paragraph}</p>
	{/each}
</div>

<Footer />