<script lang="ts">
	import "./layout.css";
	import favicon from "$lib/assets/favicon.svg";
	import Logo from "$lib/assets/favicon.ico"

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={Logo} />
	<title>cjlangreo</title>
</svelte:head>



<div class="justify-center min-h-full w-full bg-background-main">
	{@render children()}
</div>
