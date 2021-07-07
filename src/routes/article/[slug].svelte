<script lang="ts" context="module">
	// JSON Data
	import { article } from '../../content/ArticleJSON.svelte';

	// Dynamic routing + load data based on slug
	export async function load(context) {
		let slug = context.page.params.slug;
		let post = article[parseInt(slug)];
		return { props: { slug, post } };
	}
</script>

<script lang="ts">
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

<Footer />

<!-- CSS -->
<style>
	:global(body) {
		background-color: #1a1a1a;
		color: #fff;
	}
</style>