<script lang="ts" context="module">
	/// Get the 'n minutes read' estimate
	export function estimateTimeToRead(text: string): string {
		let time = Math.round(text.match(/\s/g).length / 40);
		return `${time} Minute Read`;
	}

	/// Get the first `n` words from a string and append with `...`
	export function truncateText(text: string): string {
		return `${text.substr(0, 265)} ...`;
	}
</script>
