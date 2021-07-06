<script lang="ts">
    // Get the routeID
    const url = window.location.href.split('/');
    const id = url[url.length - 1].split('-')[1];

    // JSON Data
	import { blog } from '../content/BlogJSON.svelte';
</script>

<p>
    {blog[id].title}
</p>
