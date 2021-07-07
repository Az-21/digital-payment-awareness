<script lang="ts" context="module">
	// JSON Data
	import { article } from '../../content/ArticleJSON.svelte';

	// Dynamic routing + load data based on slug
	export async function load(context) {
		let slug = context.page.params.slug;
		let post = article[parseInt(slug)];
		let pageID: number = parseInt(slug);
		let numberOfArticles: number = article.length;
		return { props: { slug, post, pageID, numberOfArticles } };
	}
</script>

<script lang="ts">
	export let pageID: number;
	export let numberOfArticles: number;
	export let post: { content: string; title: any; date: any; img: string };

	// Components
	import Footer from '../../components/Footer.svelte';
	import { estimateTimeToRead } from '../../components/Functions.svelte';

	// Create array of paragraphs
	const listContent = post.content.split('\n\n');
</script>

<!-- Title of Tab -->
<svelte:head><title>Article | Payment Awareness</title></svelte:head>

<!-- HTML -->
<div class="w-5/6 lg:w-3/5 mx-auto pb-24">
	<p class="text-5xl pt-12 lg:pt-24 font-bold">{post.title}</p>
	<p class="pt-4 text-sm font-medium text-yellow-500">
		{estimateTimeToRead(post.content)} • Published {post.date}
	</p>
	<img class="pt-4 h-64 w-full object-cover" src={post.img} alt="" />
	{#each listContent as paragraph}
		<p class="pt-8 font-serif text-xl tracking-wide">{paragraph}</p>
	{/each}
</div>

<!-- Next/Previous Section -->
<div class="w-5/6 lg:w-3/5 mx-auto pb-24 flex justify-between">
	<div>
		{#if pageID != 0}
			<a href="./{pageID - 1}" class="cursor-pointer pl-2 mt-4 flex items-center">
				<i class="fas fa-angle-left text-yellow-500 mr-2 transform scale-150" />
				<p class="text-yellow-500">Previous Article</p>
			</a>
		{/if}
	</div>

	<div>
		<a href="../" class="cursor-pointer pl-2 mt-4 flex items-center">
			<i class="fas fa-home text-yellow-500 mr-2 transform scale-150" />
			<p class="text-yellow-500">Home</p>
		</a>
	</div>

	<div>
		{#if pageID + 1 != numberOfArticles}
			<a href="./{pageID + 1}" class="cursor-pointer pl-2 mt-4 flex items-center">
				<i class="fas fa-angle-right text-yellow-500 mr-2 transform scale-150" />
				<p class="text-yellow-500">Next Article</p>
			</a>
		{/if}
	</div>
</div>

<Footer />

<!-- CSS -->
<style>
	:global(body) {
		background-color: #1a1a1a;
		color: #fff;
	}
</style>
