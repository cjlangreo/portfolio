<script lang="ts">
  import { Heading, P } from "flowbite-svelte";
  import MePhoto from "$lib/assets/me.png";

  
  import TymnAboutUs from "$lib/assets/tymn/about-us.png";
  import TymnAddStudent from "$lib/assets/tymn/add-student.png";
  import TymnScan from "$lib/assets/tymn/scan-2.png";
  import TymnAttendance from "$lib/assets/tymn/attendance.png";
  
  import VoyagersMainMenu from "$lib/assets/voyagers/mainmenu.png";
  import VoyagersMission from "$lib/assets/voyagers/mission.png"
  import VoyagersStart from "$lib/assets/voyagers/start.png"
  import VoyagersGame from "$lib/assets/voyagers/game.png"

  import Project from "../components/Project.svelte";
  import { fade } from "svelte/transition";
  import { GithubSolid, LinkedinSolid } from "flowbite-svelte-icons";

  // const showOnPx: number = 1;
  // let shadow: boolean = $state(false);
  var currentTheme = $state();
  currentTheme = "game";

  function switchTitle(element: HTMLButtonElement) {
    element.classList.toggle("-translate-y-15");
    currentTheme = currentTheme === "frontend" ? "game" : "frontend";
    const cursorPath: HTMLElement = document.getElementById(
      "cursorPath",
    ) as HTMLElement;
    cursorPath.setAttribute(
      "fill",
      currentTheme === "game" ? "rgb(247, 119, 84)" : "rgb(44, 104, 123)",
    );
  }

  // function scrollContainer() {
  //   return document.documentElement || document.body;
  // }

  // function handleOnScroll() {
  //   if (!scrollContainer()) {
  //     return;
  //   }

  //   if (scrollContainer().scrollTop > showOnPx) {
  //     shadow = true;
  //   } else {
  //     shadow = false;
  //   }
  // }
</script>

<!-- <svelte:window onscroll={handleOnScroll} /> -->

<div
  class="{currentTheme === 'game' ? 'text-game' : 'text-frontend'}
    drop-shadow-2xl py-4 flex justify-center items-center bg-background-alt rounded-2xl mx-5 top-5 transition-colors sticky z-20 text-2xl font-semibold"
>
  <span class="absolute left-3 hidden lg:block">chanz jryko langreo</span>
  <ul class="flex justify-center gap-x-5">
    <li><a href="#home">Home</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
  <div class="absolute right-3 flex gap-x-2">
    <a href="https://github.com/cjlangreo" target="_blank">
      <GithubSolid class="size-10" />
    </a>
    <a
      href="https://www.linkedin.com/in/cjlangreo/"
      class="{currentTheme === 'game'
        ? 'bg-game'
        : 'bg-frontend'} text-background-main transition-colors"
    >
      <LinkedinSolid class="size-10" />
    </a>
  </div>
</div>

<div class="flex flex-col items-center">
  <section
    id="home"
    class="bg-background-main w-full flex flex-col items-center py-24 px-5 gap-y-32"
  >
    <div class="flex flex-col lg:flex-row items-center gap-x-10">
      <p class="lg:hidden text-6xl transition-colors {currentTheme === "game" ? "text-game" : "text-frontend"}">chanz jryko langreo</p>
      <div
        class="rounded-full overflow-clip transition-colors mt-16 lg:mt-0 {currentTheme ===
        'game'
          ? 'shadow-game bg-game'
          : 'shadow-frontend bg-frontend'} shadow-2xl w-fit h-auto"
      >
        <img src={MePhoto} alt="" class="w-96" />
      </div>
      <div
        class="font-semibold flex items-start gap-x-3 mt-10 lg:mt-0"
      >
        <button
          class="flex flex-col *:text-6xl *:text-end cursor-pointer transition-transform"
          onclick={() => switchTitle(this)}
        >
          <Heading id="game" class="text-game">Game</Heading>
          <Heading id="frontend" class="text-frontend">Frontend</Heading>
        </button>
        <div class="flex flex-col">
          <Heading class="text-primary text-6xl">Developer</Heading>
          <svg
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 640 640"
            class="w-14 -translate-x-2 animate-wiggle"
          >
            <!--!Font Awesome Free v7.2.0 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license/free Copyright 2026 Fonticons, Inc.-->
            <path
              id="cursorPath"
              fill="rgb(247, 119, 84)"
              d="M173.3 66.5C181.4 62.4 191.2 63.3 198.4 68.8L518.4 308.7C526.7 314.9 530 325.7 526.8 335.5C523.6 345.3 514.4 351.9 504 351.9L351.7 351.9L440.6 529.6C448.5 545.4 442.1 564.6 426.3 572.5C410.5 580.4 391.3 574 383.4 558.2L294.5 380.5L203.2 502.3C197 510.6 186.2 513.9 176.4 510.7C166.6 507.5 160 498.3 160 488L160 88C160 78.9 165.1 70.6 173.3 66.5z"
            />
          </svg>
        </div>
      </div>
    </div>
    <div class="max-w-[50%]">
      <p class="text-2xl text-center">
        <span class="text-frontend">Frontend Developer by <strong>profession</strong>.</span><br
        />
        <span class="text-game">Game Developer by <strong>passion</strong>.</span>
      </p>
    </div>
  </section>

  <div class="p-5 w-full">
    <section
      id="projects"
      class="flex flex-col justify-center gap-y-16 bg-background-alt items-center rounded-4xl py-5 "
    >
      <Heading
        tag="h2"
        class="text-6xl {currentTheme === 'game'
          ? 'text-game'
          : 'text-frontend'} transition-colors">PROJECTS</Heading
      >
      <div class="flex flex-col gap-y-16 items-center">
        <Project
          type="game"
          projectName="I, Garcian"
          position="Project Manager / Leader Developer"
        >
          <iframe
            class="w-full aspect-video"
            src="https://www.youtube.com/embed/AGUGJzNJFLk"
            title="I, Garcian | Trailer"
            frameborder="0"
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
            referrerpolicy="strict-origin-when-cross-origin"
            allowfullscreen
          ></iframe>
        </Project>
        <Project
          position="Project Manager / Lead Developer"
          type="game"
          projectName="Voyagers"
        >
          <div class="grid grid-cols-2 gap-5 p-5">
            <img class=" rounded-2xl h-full" src={VoyagersMainMenu} alt="" />
            <img class=" rounded-2xl h-full" src={VoyagersGame} alt="" />
            <img class=" rounded-2xl h-full" src={VoyagersStart} alt="" />
            <img class=" rounded-2xl h-full" src={VoyagersStart} alt="" />
          </div>
        </Project>
        <Project
          position="Co-developer"
          type="frontend"
          github="https://github.com/cjlangreo/tymn-attendance-checker"
          projectName="Tymn, Attendance Checker"
        >
          <div class="grid grid-cols-2 gap-5 ">
            <img class="w-full" src={TymnAboutUs} alt="" />
            <img class="w-full" src={TymnAddStudent} alt="" />
            <img class="w-full" src={TymnScan} alt="" />
            <img class="w-full" src={TymnAttendance} alt="" />
          </div>
        </Project>
      </div>
    </section>
  </div>

  <!-- <div class="w-32 h-[3000px] br-red-600"></div> -->
</div>
