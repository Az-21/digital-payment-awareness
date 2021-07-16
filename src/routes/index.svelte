<!-- Typescript -->
<script lang="ts">
	// Svelte Components
	import Navbar from '../components/Navbar.svelte';
	import Hero from '../components/Hero.svelte';
	import CTA from '../components/CTA.svelte';
	import SectionHeader from '../components/SectionHeader.svelte';
	import TextCard from '../components/TextCard.svelte';
	import Video from '../components/Video.svelte';
	import Footer from '../components/Footer.svelte';

	// JSON Data
	import { blog } from '../content/BlogJSON.svelte';
	import { article } from '../content/ArticleJSON.svelte';
	import { video } from '../content/VideoJSON.svelte';

	// External functions
	import { estimateTimeToRead, truncateText } from '../components/Functions.svelte';
</script>

<!-- Title of Tab -->
<svelte:head><title>Digital Payment Awareness</title></svelte:head>

<!-- HTML Components -->
<Navbar />
<Hero />
<CTA />

<!-- Blog section -->
<div id="blog" />
<SectionHeader text="Read Blogs" textColor="text-blue-500" divColor="divide-blue-500" />
<div class="w-5/6 mx-auto grid md:grid-cols-3 gap-4">
	{#each blog as blog, index}
		<TextCard
			routeID={`/blog/${index}`}
			title={blog.title}
			subtitle={truncateText(blog.preview)}
			img={blog.img}
			time={estimateTimeToRead(blog.content)}
			icon="fa-file-alt"
			color="text-blue-500"
		/>
	{/each}
</div>

<!-- Article section -->
<div id="article" />
<SectionHeader text="Read Articles" textColor="text-yellow-500" divColor="divide-yellow-500" />
<div class="w-5/6 mx-auto grid md:grid-cols-3 gap-4">
	{#each article as article, index}
		<TextCard
			routeID={`/article/${index}`}
			title={article.title}
			subtitle={truncateText(article.preview)}
			img={article.img}
			time={estimateTimeToRead(article.content)}
			icon="fa-newspaper"
			color="text-yellow-500"
		/>
	{/each}
</div>

<!-- YouTube section -->
<div id="video" />
<SectionHeader text="Watch Videos" textColor="text-red-500" divColor="divide-red-500" />
<div class="w-5/6 mx-auto grid md:grid-cols-2 gap-4">
	{#each video as video}
		<Video title={video.title} subtitle={video.content} link={video.link} time={video.time} />
	{/each}
</div>

<Footer />

<!-- CSS -->
<style>
	:global(body) {
		background-color: #0a0a0a;
		color: #fff;
	}
	:global(html) {
		scroll-behavior: smooth;
	}
</style>
