<!-- Typescript -->
<script lang="ts">
	import Navbar from '../components/Navbar.svelte';
	import Hero from '../components/Hero.svelte';
	import CTA from '../components/CTA.svelte';
	import SectionHeader from '../components/SectionHeader.svelte';
	import TextCard from '../components/TextCard.svelte';
	import { blog } from '../content/BlogJSON.svelte';
	import { article } from '../content/ArticleJSON.svelte';
	import { estimateTimeToRead, truncateText } from '../components/Functions.svelte';
</script>

<!-- HTML Components -->
<Navbar />
<Hero />
<CTA />

<!-- Blog section -->
<SectionHeader text="Read Blogs" textColor="text-blue-500" divColor="divide-blue-500" />
<div class="w-5/6 mx-auto grid md:grid-cols-3 gap-4">
	{#each blog as blog}
		<TextCard
			title={blog.title}
			subtitle={truncateText(blog.content)}
			img={blog.img}
			time={estimateTimeToRead(blog.content)}
		/>
	{/each}
</div>

<!-- Article section -->
<SectionHeader text="Read Articles" textColor="text-yellow-500" divColor="divide-yellow-500" />
<div class="w-5/6 mx-auto grid md:grid-cols-3 gap-4">
	{#each article as article}
		<TextCard
			title={article.title}
			subtitle={truncateText(article.content)}
			img={article.img}
			time={estimateTimeToRead(article.content)}
		/>
	{/each}
</div>

<!-- CSS -->
<style>
	:global(body) {
		background-color: #1a1a1a;
		color: #fff;
	}
</style>
