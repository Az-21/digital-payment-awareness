<!-- Typescript -->
<script lang="ts">
	import Navbar from '../components/Navbar.svelte';
	import Hero from '../components/Hero.svelte';
	import CTA from '../components/CTA.svelte';
	import SectionHeader from '../components/SectionHeader.svelte';
</script>

<!-- HTML Components -->
<Navbar />
<Hero />
<CTA />

<!-- Blog section -->
<SectionHeader text="Blog" textColor="text-blue-500" divColor="divide-blue-500" />

<!-- CSS -->
<style>
	:global(body) {
		background-color: #1a1a1a;
		color: #fff;
	}
</style>
