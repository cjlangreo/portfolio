<script lang="ts">
  import { Heading } from "flowbite-svelte";
  import { GithubSolid } from "flowbite-svelte-icons";

  let { projectName, type, children, github = "" , position} = $props();
  
</script>

<div class="rounded-2xl overflow-clip bg-background-main text-center w-[50%]">
  <div
    class="flex text-background-alt font-bold text-lg px-3 py-3 items-center {type === 'frontend'
      ? 'bg-frontend'
      : 'bg-game'}"
  >
    <div class="w-full">
      {#if github}
        <a href={github} target="_blank">
          <GithubSolid class="size-10" />
        </a>
      {/if}
    </div>
    <div class="flex flex-col w-full">
      <Heading class="w-full text-nowrap text-2xl font-extrabold">{projectName}</Heading>
      <Heading class="w-full text-nowrap text-md" tag="h2">{position}</Heading>
    </div>
    <div class="w-full"></div>
  </div>

  <div class="">
    {@render children()}
  </div>
</div>
