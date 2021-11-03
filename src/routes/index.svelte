<!-- Typescript -->
<script lang="ts">
	// Svelte Components
	import Navbar from '../components/Navbar.svelte';
	import BackToTop from '../components/BackToTop.svelte';
	import Hero from '../components/Hero.svelte';
	import CTA from '../components/CTA.svelte';
	import SectionHeader from '../components/SectionHeader.svelte';
	import TextCard from '../components/TextCard.svelte';
	import Video from '../components/Video.svelte';
	import Footer from '../components/Footer.svelte';

	// JSON Data
	import { blog } from '../content/BlogJSON.svelte';
	import { tutorial } from '../content/TutorialJSON.svelte';
	import { video } from '../content/VideoJSON.svelte';

	// External functions
	import { estimateTimeToRead, truncateText } from '../components/Functions.svelte';
</script>

<!-- Title of Tab -->
<svelte:head><title>Digital Payment Awareness</title></svelte:head>

<!-- HTML Components -->
<Navbar />
<BackToTop />
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
			color="text-blue-500"
		/>
	{/each}
</div>

<!-- Tutorial section -->
<div id="tutorial" />
<SectionHeader text="Read Tutorials" textColor="text-yellow-500" divColor="divide-yellow-500" />
<div class="w-5/6 mx-auto grid md:grid-cols-3 gap-4">
	{#each tutorial as tutorial, index}
		<TextCard
			routeID={`/tutorial/${index}`}
			title={tutorial.title}
			subtitle={truncateText(tutorial.preview)}
			img={tutorial.img}
			time={estimateTimeToRead(tutorial.content)}
			color="text-yellow-500"
		/>
	{/each}
</div>

<!-- YouTube section -->
<div id="video" />
<SectionHeader text="Watch Videos" textColor="text-red-500" divColor="divide-red-500" />
<div class="w-5/6 mx-auto grid md:grid-cols-2 gap-4">
	{#each video as video}
		<Video title={video.title} link={video.link} time={video.time} />
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
