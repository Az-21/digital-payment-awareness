<script lang="ts" context="module">
	// JSON Data
	import { blog } from '../../content/BlogJSON.svelte';

	// Dynamic routing + load data based on slug
	export async function load(context) {
		let slug = context.page.params.slug;
		let post = blog[parseInt(slug)];
		let pageID: number = parseInt(slug);
		let numberOfBlogs: number = blog.length;
		return { props: { slug, post, pageID, numberOfBlogs } };
	}
</script>

<script lang="ts">
	export let pageID: number;
	export let numberOfBlogs: number;
	export let post: { content: string; title: any; date: any; img: string };

	// Components
	import Footer from '../../components/Footer.svelte';
	import { estimateTimeToRead } from '../../components/Functions.svelte';
</script>

<!-- Title of Tab -->
<svelte:head><title>Blog | Payment Awareness</title></svelte:head>

<!-- HTML -->
<div class="w-5/6 lg:w-3/5 mx-auto pb-24">
	<p class="text-5xl pt-12 lg:pt-24 font-bold" id="immersive-reader-content">{post.title}</p>
	<p class="pt-4 text-sm font-medium text-blue-500">
		{estimateTimeToRead(post.content)} • Published {post.date}
	</p>
	<img class="py-4 h-64 w-full object-cover" src={post.img} alt="" />
	<article class="markdown-body" id="immersive-reader-content">
		{@html post.content}
	</article>
</div>

<!-- Next/Previous Section -->
<div class="w-5/6 lg:w-3/5 mx-auto pb-24 flex justify-between">
	<div>
		{#if pageID != 0}
			<a href="./{pageID - 1}" class="cursor-pointer pl-2 mt-4 flex items-center">
				<i class="fas fa-angle-left text-blue-500 mr-2 transform scale-150" />
				<p class="text-blue-500">Previous Blog</p>
			</a>
		{/if}
	</div>

	<div>
		<a href="../" class="cursor-pointer pl-2 mt-4 flex items-center">
			<i class="fas fa-home text-blue-500 mr-2 transform scale-150" />
			<p class="text-blue-500">Home</p>
		</a>
	</div>

	<div>
		{#if pageID + 1 != numberOfBlogs}
			<a href="./{pageID + 1}" class="cursor-pointer pl-2 mt-4 flex items-center">
				<p class="text-blue-500">Next Blog</p>
				<i class="fas fa-angle-right text-blue-500 ml-2 transform scale-150" />
			</a>
		{/if}
	</div>
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

	:global(.markdown-body .octicon) {
		display: inline-block;
		fill: currentColor;
		vertical-align: text-bottom;
	}

	:global(.markdown-body .anchor) {
		float: left;
		line-height: 1;
		margin-left: -20px;
		padding-right: 4px;
	}

	:global(.markdown-body .anchor:focus) {
		outline: none;
	}

	:global(.markdown-body h1 .octicon-link),
	:global(.markdown-body h2 .octicon-link),
	:global(.markdown-body h3 .octicon-link),
	:global(.markdown-body h4 .octicon-link),
	:global(.markdown-body h5 .octicon-link),
	:global(.markdown-body h6 .octicon-link) {
		color: #fff;
		vertical-align: middle;
		visibility: hidden;
	}

	:global(.markdown-body h1:hover .anchor),
	:global(.markdown-body h2:hover .anchor),
	:global(.markdown-body h3:hover .anchor),
	:global(.markdown-body h4:hover .anchor),
	:global(.markdown-body h5:hover .anchor),
	:global(.markdown-body h6:hover .anchor) {
		text-decoration: none;
	}

	:global(.markdown-body h1:hover .anchor .octicon-link),
	:global(.markdown-body h2:hover .anchor .octicon-link),
	:global(.markdown-body h3:hover .anchor .octicon-link),
	:global(.markdown-body h4:hover .anchor .octicon-link),
	:global(.markdown-body h5:hover .anchor .octicon-link),
	:global(.markdown-body h6:hover .anchor .octicon-link) {
		visibility: visible;
	}

	:global(.markdown-body h1:hover .anchor .octicon-link:before),
	:global(.markdown-body h2:hover .anchor .octicon-link:before),
	:global(.markdown-body h3:hover .anchor .octicon-link:before),
	:global(.markdown-body h4:hover .anchor .octicon-link:before),
	:global(.markdown-body h5:hover .anchor .octicon-link:before),
	:global(.markdown-body h6:hover .anchor .octicon-link:before) {
		width: 16px;
		height: 16px;
		content: ' ';
		display: inline-block;
		background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 16 16' version='1.1' width='16' height='16' aria-hidden='true'%3E%3Cpath fill-rule='evenodd' d='M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z'%3E%3C/path%3E%3C/svg%3E");
	}
	:global(.markdown-body) {
		-ms-text-size-adjust: 100%;
		-webkit-text-size-adjust: 100%;
		line-height: 1.5;
		color: #fff;
		font-family: -apple-system, BlinkMacSystemFont, Segoe UI, Helvetica, Arial, sans-serif,
			Apple Color Emoji, Segoe UI Emoji;
		font-size: 16px;
		line-height: 1.5;
		word-wrap: break-word;
	}

	:global(.markdown-body details) {
		display: block;
	}

	:global(.markdown-body summary) {
		display: list-item;
	}

	:global(.markdown-body a) {
		background-color: initial;
	}

	:global(.markdown-body a:active),
	:global(.markdown-body a:hover) {
		outline-width: 0;
	}

	:global(.markdown-body strong) {
		font-weight: inherit;
		font-weight: bolder;
	}

	:global(.markdown-body h1) {
		font-size: 2em;
		margin: 0.67em 0;
	}

	:global(.markdown-body img) {
		border-style: none;
	}

	:global(.markdown-body code),
	:global(.markdown-body kbd),
	:global(.markdown-body pre) {
		font-family: monospace, monospace;
		font-size: 1em;
	}

	:global(.markdown-body hr) {
		box-sizing: initial;
		height: 0;
		overflow: visible;
	}

	:global(.markdown-body input) {
		font: inherit;
		margin: 0;
	}

	:global(.markdown-body input) {
		overflow: visible;
	}

	:global(.markdown-body [type='checkbox']) {
		box-sizing: border-box;
		padding: 0;
	}

	:global(.markdown-body *) {
		box-sizing: border-box;
	}

	:global(.markdown-body input) {
		font-family: inherit;
		font-size: inherit;
		line-height: inherit;
	}

	:global(.markdown-body a) {
		color: #0366d6;
		text-decoration: none;
	}

	:global(.markdown-body a:hover) {
		text-decoration: underline;
	}

	:global(.markdown-body strong) {
		font-weight: 600;
	}

	:global(.markdown-body hr) {
		height: 0;
		margin: 15px 0;
		overflow: hidden;
		background: transparent;
		border: 0;
		border-bottom: 1px solid #dfe2e5;
	}

	:global(.markdown-body hr:after),
	:global(.markdown-body hr:before) {
		display: table;
		content: '';
	}

	:global(.markdown-body hr:after) {
		clear: both;
	}

	:global(.markdown-body table) {
		border-spacing: 0;
		border-collapse: collapse;
	}

	:global(.markdown-body td),
	:global(.markdown-body th) {
		padding: 0;
	}

	:global(.markdown-body details summary) {
		cursor: pointer;
	}

	:global(.markdown-body kbd) {
		display: inline-block;
		padding: 3px 5px;
		font: 11px SFMono-Regular, Consolas, Liberation Mono, Menlo, monospace;
		line-height: 10px;
		color: #ccc;
		vertical-align: middle;
		background-color: #111;
		border: 1px solid #000;
		border-radius: 3px;
		box-shadow: inset 0 -1px 0 #444;
	}

	:global(.markdown-body h1),
	:global(.markdown-body h2),
	:global(.markdown-body h3),
	:global(.markdown-body h4),
	:global(.markdown-body h5),
	:global(.markdown-body h6) {
		margin-top: 0;
		margin-bottom: 0;
	}

	:global(.markdown-body h1) {
		font-size: 32px;
	}

	:global(.markdown-body h1),
	:global(.markdown-body h2) {
		font-weight: 600;
	}

	:global(.markdown-body h2) {
		font-size: 24px;
	}

	:global(.markdown-body h3) {
		font-size: 20px;
	}

	:global(.markdown-body h3),
	:global(.markdown-body h4) {
		font-weight: 600;
	}

	:global(.markdown-body h4) {
		font-size: 16px;
	}

	:global(.markdown-body h5) {
		font-size: 14px;
	}

	:global(.markdown-body h5),
	:global(.markdown-body h6) {
		font-weight: 600;
	}

	:global(.markdown-body h6) {
		font-size: 12px;
	}

	:global(.markdown-body p) {
		margin-top: 0;
		margin-bottom: 10px;
	}

	:global(.markdown-body blockquote) {
		margin: 0;
	}

	:global(.markdown-body ol),
	:global(.markdown-body ul) {
		padding-left: 0;
		margin-top: 0;
		margin-bottom: 0;
	}

	:global(.markdown-body ol ol),
	:global(.markdown-body ul ol) {
		list-style-type: lower-roman;
	}

	:global(.markdown-body ol ol ol),
	:global(.markdown-body ol ul ol),
	:global(.markdown-body ul ol ol),
	:global(.markdown-body ul ul ol) {
		list-style-type: lower-alpha;
	}

	:global(.markdown-body dd) {
		margin-left: 0;
	}

	:global(.markdown-body code),
	:global(.markdown-body pre) {
		font-family: SFMono-Regular, Consolas, Liberation Mono, Menlo, monospace;
		font-size: 12px;
	}

	:global(.markdown-body pre) {
		margin-top: 0;
		margin-bottom: 0;
	}

	:global(.markdown-body input::-webkit-inner-spin-button),
	:global(.markdown-body input::-webkit-outer-spin-button) {
		margin: 0;
		-webkit-appearance: none;
		appearance: none;
	}

	:global(.markdown-body :checked + .radio-label) {
		position: relative;
		z-index: 1;
		border-color: #0366d6;
	}

	:global(.markdown-body .border) {
		border: 1px solid #e1e4e8 !important;
	}

	:global(.markdown-body .border-0) {
		border: 0 !important;
	}

	:global(.markdown-body .border-bottom) {
		border-bottom: 1px solid #e1e4e8 !important;
	}

	:global(.markdown-body .rounded-1) {
		border-radius: 3px !important;
	}

	:global(.markdown-body .bg-white) {
		background-color: #fff !important;
	}

	:global(.markdown-body .bg-gray-light) {
		background-color: #fafbfc !important;
	}

	:global(.markdown-body .text-gray-light) {
		color: #6a737d !important;
	}

	:global(.markdown-body .mb-0) {
		margin-bottom: 0 !important;
	}

	:global(.markdown-body .my-2) {
		margin-top: 8px !important;
		margin-bottom: 8px !important;
	}

	:global(.markdown-body .pl-0) {
		padding-left: 0 !important;
	}

	:global(.markdown-body .py-0) {
		padding-top: 0 !important;
		padding-bottom: 0 !important;
	}

	:global(.markdown-body .pl-1) {
		padding-left: 4px !important;
	}

	:global(.markdown-body .pl-2) {
		padding-left: 8px !important;
	}

	:global(.markdown-body .py-2) {
		padding-top: 8px !important;
		padding-bottom: 8px !important;
	}

	:global(.markdown-body .pl-3),
	:global(.markdown-body .px-3) {
		padding-left: 16px !important;
	}

	:global(.markdown-body .px-3) {
		padding-right: 16px !important;
	}

	:global(.markdown-body .pl-4) {
		padding-left: 24px !important;
	}

	:global(.markdown-body .pl-5) {
		padding-left: 32px !important;
	}

	:global(.markdown-body .pl-6) {
		padding-left: 40px !important;
	}

	:global(.markdown-body .f6) {
		font-size: 12px !important;
	}

	:global(.markdown-body .lh-condensed) {
		line-height: 1.25 !important;
	}

	:global(.markdown-body .text-bold) {
		font-weight: 600 !important;
	}

	:global(.markdown-body .pl-c) {
		color: #6a737d;
	}

	:global(.markdown-body .pl-c1),
	:global(.markdown-body .pl-s .pl-v) {
		color: #005cc5;
	}

	:global(.markdown-body .pl-e),
	:global(.markdown-body .pl-en) {
		color: #6f42c1;
	}

	:global(.markdown-body .pl-s .pl-s1),
	:global(.markdown-body .pl-smi) {
		color: #24292e;
	}

	:global(.markdown-body .pl-ent) {
		color: #22863a;
	}

	:global(.markdown-body .pl-k) {
		color: #d73a49;
	}

	:global(.markdown-body .pl-pds),
	:global(.markdown-body .pl-s),
	:global(.markdown-body .pl-s .pl-pse .pl-s1),
	:global(.markdown-body .pl-sr),
	:global(.markdown-body .pl-sr .pl-cce),
	:global(.markdown-body .pl-sr .pl-sra),
	:global(.markdown-body .pl-sr .pl-sre) {
		color: #032f62;
	}

	:global(.markdown-body .pl-smw),
	:global(.markdown-body .pl-v) {
		color: #e36209;
	}

	:global(.markdown-body .pl-bu) {
		color: #b31d28;
	}

	:global(.markdown-body .pl-ii) {
		color: #fafbfc;
		background-color: #b31d28;
	}

	:global(.markdown-body .pl-c2) {
		color: #fafbfc;
		background-color: #d73a49;
	}

	:global(.markdown-body .pl-c2:before) {
		content: '^M';
	}

	:global(.markdown-body .pl-sr .pl-cce) {
		font-weight: 700;
		color: #22863a;
	}

	:global(.markdown-body .pl-ml) {
		color: #735c0f;
	}

	:global(.markdown-body .pl-mh),
	:global(.markdown-body .pl-mh .pl-en),
	:global(.markdown-body .pl-ms) {
		font-weight: 700;
		color: #005cc5;
	}

	:global(.markdown-body .pl-mi) {
		font-style: italic;
		color: #24292e;
	}

	:global(.markdown-body .pl-mb) {
		font-weight: 700;
		color: #24292e;
	}

	:global(.markdown-body .pl-md) {
		color: #b31d28;
		background-color: #ffeef0;
	}

	:global(.markdown-body .pl-mi1) {
		color: #22863a;
		background-color: #f0fff4;
	}

	:global(.markdown-body .pl-mc) {
		color: #e36209;
		background-color: #ffebda;
	}

	:global(.markdown-body .pl-mi2) {
		color: #222;
		background-color: #005cc5;
	}

	:global(.markdown-body .pl-mdr) {
		font-weight: 700;
		color: #6f42c1;
	}

	:global(.markdown-body .pl-ba) {
		color: #586069;
	}

	:global(.markdown-body .pl-sg) {
		color: #959da5;
	}

	:global(.markdown-body .pl-corl) {
		text-decoration: underline;
		color: #032f62;
	}

	:global(.markdown-body .mb-0) {
		margin-bottom: 0 !important;
	}

	:global(.markdown-body .my-2) {
		margin-bottom: 8px !important;
	}

	:global(.markdown-body .my-2) {
		margin-top: 8px !important;
	}

	:global(.markdown-body .pl-0) {
		padding-left: 0 !important;
	}

	:global(.markdown-body .py-0) {
		padding-top: 0 !important;
		padding-bottom: 0 !important;
	}

	:global(.markdown-body .pl-1) {
		padding-left: 4px !important;
	}

	:global(.markdown-body .pl-2) {
		padding-left: 8px !important;
	}

	:global(.markdown-body .py-2) {
		padding-top: 8px !important;
		padding-bottom: 8px !important;
	}

	:global(.markdown-body .pl-3) {
		padding-left: 16px !important;
	}

	:global(.markdown-body .pl-4) {
		padding-left: 24px !important;
	}

	:global(.markdown-body .pl-5) {
		padding-left: 32px !important;
	}

	:global(.markdown-body .pl-6) {
		padding-left: 40px !important;
	}

	:global(.markdown-body .pl-7) {
		padding-left: 48px !important;
	}

	:global(.markdown-body .pl-8) {
		padding-left: 64px !important;
	}

	:global(.markdown-body .pl-9) {
		padding-left: 80px !important;
	}

	:global(.markdown-body .pl-10) {
		padding-left: 96px !important;
	}

	:global(.markdown-body .pl-11) {
		padding-left: 112px !important;
	}

	:global(.markdown-body .pl-12) {
		padding-left: 128px !important;
	}

	:global(.markdown-body hr) {
		border-bottom-color: #eee;
	}

	:global(.markdown-body kbd) {
		display: inline-block;
		padding: 3px 5px;
		font: 11px SFMono-Regular, Consolas, Liberation Mono, Menlo, monospace;
		line-height: 10px;
		color: #444d56;
		vertical-align: middle;
		background-color: #fafbfc;
		border: 1px solid #d1d5da;
		border-radius: 3px;
		box-shadow: inset 0 -1px 0 #d1d5da;
	}

	:global(.markdown-body:after),
	:global(.markdown-body:before) {
		display: table;
		content: '';
	}

	:global(.markdown-body:after) {
		clear: both;
	}

	:global(.markdown-body > :first-child) {
		margin-top: 0 !important;
	}

	:global(.markdown-body > :last-child) {
		margin-bottom: 0 !important;
	}

	:global(.markdown-body a:not([href])) {
		color: inherit;
		text-decoration: none;
	}

	:global(.markdown-body blockquote),
	:global(.markdown-body details),
	:global(.markdown-body dl),
	:global(.markdown-body ol),
	:global(.markdown-body p),
	:global(.markdown-body pre),
	:global(.markdown-body table),
	:global(.markdown-body ul) {
		margin-top: 0;
		margin-bottom: 16px;
	}

	:global(.markdown-body hr) {
		height: 0.25em;
		padding: 0;
		margin: 24px 0;
		background-color: #e1e4e8;
		border: 0;
	}

	:global(.markdown-body blockquote) {
		padding: 0 1em;
		color: #2aff9f;
		border-left: 0.25em solid #555;
	}

	:global(.markdown-body blockquote > :first-child) {
		margin-top: 0;
	}

	:global(.markdown-body blockquote > :last-child) {
		margin-bottom: 0;
	}

	:global(.markdown-body h1),
	:global(.markdown-body h2),
	:global(.markdown-body h3),
	:global(.markdown-body h4),
	:global(.markdown-body h5),
	:global(.markdown-body h6) {
		margin-top: 24px;
		margin-bottom: 16px;
		font-weight: 600;
		line-height: 1.25;
	}

	:global(.markdown-body h1) {
		font-size: 2em;
	}

	:global(.markdown-body h1),
	:global(.markdown-body h2) {
		padding-bottom: 0.3em;
		border-bottom: 1px solid #eaecef;
	}

	:global(.markdown-body h2) {
		font-size: 1.5em;
	}

	:global(.markdown-body h3) {
		font-size: 1.25em;
	}

	:global(.markdown-body h4) {
		font-size: 1em;
	}

	:global(.markdown-body h5) {
		font-size: 0.875em;
	}

	:global(.markdown-body h6) {
		font-size: 0.85em;
		color: #6a737d;
	}

	:global(.markdown-body ol),
	:global(.markdown-body ul) {
		padding-left: 2em;
	}

	:global(.markdown-body ol ol),
	:global(.markdown-body ol ul),
	:global(.markdown-body ul ol),
	:global(.markdown-body ul ul) {
		margin-top: 0;
		margin-bottom: 0;
	}

	:global(.markdown-body li) {
		word-wrap: break-all;
	}

	:global(.markdown-body li > p) {
		margin-top: 16px;
	}

	:global(.markdown-body li + li) {
		margin-top: 0.25em;
	}

	:global(.markdown-body dl) {
		padding: 0;
	}

	:global(.markdown-body dl dt) {
		padding: 0;
		margin-top: 16px;
		font-size: 1em;
		font-style: italic;
		font-weight: 600;
	}

	:global(.markdown-body dl dd) {
		padding: 0 16px;
		margin-bottom: 16px;
	}

	:global(.markdown-body table) {
		display: block;
		width: 100%;
		overflow: auto;
	}

	:global(.markdown-body table th) {
		font-weight: 600;
	}

	:global(.markdown-body table td),
	:global(.markdown-body table th) {
		padding: 6px 13px;
		border: 1px solid #dfe2e5;
	}

	:global(.markdown-body table tr) {
		background-color: #fff;
		border-top: 1px solid #c6cbd1;
	}

	:global(.markdown-body table tr:nth-child(2n)) {
		background-color: #222;
	}

	:global(.markdown-body img) {
		max-width: 100%;
		box-sizing: initial;
		background-color: #fff;
		display: block;
		margin-left: auto;
		margin-right: auto;
	}

	:global(.markdown-body img[align='right']) {
		padding-left: 20px;
	}

	:global(.markdown-body img[align='left']) {
		padding-right: 20px;
	}

	:global(.markdown-body code) {
		padding: 0.2em 0.4em;
		margin: 0;
		font-size: 85%;
		background-color: #555;
		border-radius: 3px;
	}

	:global(.markdown-body pre) {
		word-wrap: normal;
	}

	:global(.markdown-body pre > code) {
		padding: 0;
		margin: 0;
		font-size: 100%;
		word-break: normal;
		white-space: pre;
		background: transparent;
		border: 0;
	}

	:global(.markdown-body .highlight) {
		margin-bottom: 16px;
	}

	:global(.markdown-body .highlight pre) {
		margin-bottom: 0;
		word-break: normal;
	}

	:global(.markdown-body .highlight pre),
	:global(.markdown-body pre) {
		padding: 16px;
		overflow: auto;
		font-size: 85%;
		line-height: 1.45;
		background-color: #222;
		border-radius: 3px;
	}

	:global(.markdown-body pre code) {
		display: inline;
		max-width: auto;
		padding: 0;
		margin: 0;
		overflow: visible;
		line-height: inherit;
		word-wrap: normal;
		background-color: initial;
		border: 0;
	}

	:global(.markdown-body .commit-tease-sha) {
		display: inline-block;
		font-family: SFMono-Regular, Consolas, Liberation Mono, Menlo, monospace;
		font-size: 90%;
		color: #444d56;
	}

	:global(.markdown-body .full-commit .btn-outline:not(:disabled):hover) {
		color: #005cc5;
		border-color: #005cc5;
	}

	:global(.markdown-body .blob-wrapper) {
		overflow-x: auto;
		overflow-y: hidden;
	}

	:global(.markdown-body .blob-wrapper-embedded) {
		max-height: 240px;
		overflow-y: auto;
	}

	:global(.markdown-body .blob-num) {
		width: 1%;
		min-width: 50px;
		padding-right: 10px;
		padding-left: 10px;
		font-family: SFMono-Regular, Consolas, Liberation Mono, Menlo, monospace;
		font-size: 12px;
		line-height: 20px;
		color: rgba(27, 31, 35, 0.3);
		text-align: right;
		white-space: nowrap;
		vertical-align: top;
		cursor: pointer;
		-webkit-user-select: none;
		-moz-user-select: none;
		-ms-user-select: none;
		user-select: none;
	}

	:global(.markdown-body .blob-num:hover) {
		color: rgba(27, 31, 35, 0.6);
	}

	:global(.markdown-body .blob-num:before) {
		content: attr(data-line-number);
	}

	:global(.markdown-body .blob-code) {
		position: relative;
		padding-right: 10px;
		padding-left: 10px;
		line-height: 20px;
		vertical-align: top;
	}

	:global(.markdown-body .blob-code-inner) {
		overflow: visible;
		font-family: SFMono-Regular, Consolas, Liberation Mono, Menlo, monospace;
		font-size: 12px;
		color: #24292e;
		word-wrap: normal;
		white-space: pre;
	}

	:global(.markdown-body .pl-token.active),
	:global(.markdown-body .pl-token:hover) {
		cursor: pointer;
		background: #ffea7f;
	}

	:global(.markdown-body .tab-size[data-tab-size='1']) {
		-moz-tab-size: 1;
		tab-size: 1;
	}

	:global(.markdown-body .tab-size[data-tab-size='2']) {
		-moz-tab-size: 2;
		tab-size: 2;
	}

	:global(.markdown-body .tab-size[data-tab-size='3']) {
		-moz-tab-size: 3;
		tab-size: 3;
	}

	:global(.markdown-body .tab-size[data-tab-size='4']) {
		-moz-tab-size: 4;
		tab-size: 4;
	}

	:global(.markdown-body .tab-size[data-tab-size='5']) {
		-moz-tab-size: 5;
		tab-size: 5;
	}

	:global(.markdown-body .tab-size[data-tab-size='6']) {
		-moz-tab-size: 6;
		tab-size: 6;
	}

	:global(.markdown-body .tab-size[data-tab-size='7']) {
		-moz-tab-size: 7;
		tab-size: 7;
	}

	:global(.markdown-body .tab-size[data-tab-size='8']) {
		-moz-tab-size: 8;
		tab-size: 8;
	}

	:global(.markdown-body .tab-size[data-tab-size='9']) {
		-moz-tab-size: 9;
		tab-size: 9;
	}

	:global(.markdown-body .tab-size[data-tab-size='10']) {
		-moz-tab-size: 10;
		tab-size: 10;
	}

	:global(.markdown-body .tab-size[data-tab-size='11']) {
		-moz-tab-size: 11;
		tab-size: 11;
	}

	:global(.markdown-body .tab-size[data-tab-size='12']) {
		-moz-tab-size: 12;
		tab-size: 12;
	}

	:global(.markdown-body .task-list-item) {
		list-style-type: none;
	}

	:global(.markdown-body .task-list-item + .task-list-item) {
		margin-top: 3px;
	}

	:global(.markdown-body .task-list-item input) {
		margin: 0 0.2em 0.25em -1.6em;
		vertical-align: middle;
	}
</style>
