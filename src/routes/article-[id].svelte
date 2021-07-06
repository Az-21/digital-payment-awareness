<script lang="ts">
	// Get the routeID
	const url = window.location.href.split('/');
	const id = url[url.length - 1].split('-')[1];

	// JSON Data
	import { article } from '../content/ArticleJSON.svelte';
</script>

<div class="w-3/5 mx-auto">
	<p class = "pt-12 text-3xl">{article[id].title}</p>
</div>
