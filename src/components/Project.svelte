<script lang="ts">
  import { Heading } from "flowbite-svelte";
  import { GithubSolid } from "flowbite-svelte-icons";
  import { slide } from "svelte/transition";

  let {
    projectName,
    type,
    children,
    github = "",
    position,
    open = false,
    image,
    introText = "[Intro text goes here]",
    onHeaderClick,
  } = $props();
</script>

<div
  class="flex flex-col rounded-2xl overflow-clip bg-background-main text-center w-full max-w-[800px]"
>
  <!-- Header -->
  <button
    class="projectComponent flex text-background-alt font-bold text-lg px-3 py-3 items-center w-full cursor-pointer {type ===
    'frontend'
      ? 'bg-frontend'
      : 'bg-game'}"
    onclick={onHeaderClick}
  >
    <div class="w-full">
      {#if github}
        <a href={github} target="_blank">
          <GithubSolid class="size-10" />
        </a>
      {/if}
    </div>
    <div class="flex flex-col gap-y-2 w-full">
      <Heading class="w-full text-2xl md:text-4xl font-extrabold">{projectName}</Heading>
      <Heading
        class="w-full text-nowrap text-sm md:text-xl px-3 {type == 'frontend'
          ? 'bg-game'
          : 'bg-frontend'} rounded-full"
        tag="h2">{position}</Heading
      >
    </div>
    <div class="w-full"></div>
  </button>

  <div class="flex flex-col h-full">
    <img src={image} alt="" class="h-full" />
    <div class="p-3 w-full flex flex-col justify-center">
      <p>{introText}</p>
    </div>
  </div>

  
  {#if open}
    <hr class=" my-5 {type === "game" ? "border-game" : "border-frontend"}">
    <div class="" transition:slide>
      {@render children()}
    </div>
  {/if}
</div>
