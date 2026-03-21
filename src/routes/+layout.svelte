<script lang="ts">
	import "./layout.css";
	import favicon from "$lib/assets/favicon.svg";

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
	<title>cjlangreo</title>
</svelte:head>



<div class="justify-center min-h-full w-full bg-background-main">
	{@render children()}
</div>
