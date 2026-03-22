<script lang="ts">
  import {
    Button,
    FloatingLabelInput,
    Heading,
    Input,
    Label,
    P,
    Textarea,
  } from "flowbite-svelte";
  import MePhoto from "$lib/assets/me.png";

  import TymnAboutUs from "$lib/assets/tymn/about-us.png";
  import TymnAddStudent from "$lib/assets/tymn/add-student.png";
  import TymnScan from "$lib/assets/tymn/scan-2.png";
  import TymnAttendance from "$lib/assets/tymn/attendance.png";

  import VoyagersMainMenu from "$lib/assets/voyagers/mainmenu.png";
  import VoyagersMission from "$lib/assets/voyagers/mission.png";
  import VoyagersStart from "$lib/assets/voyagers/start.png";
  import VoyagersGame from "$lib/assets/voyagers/game.png";

  import IGarcianMenu from "$lib/assets/igarcian/main-menu.png";
  import IGarcianCharacterCreate from "$lib/assets/igarcian/character-create.png"
  import IGarcianMinigame from "$lib/assets/igarcian/minigame.png"
  import IGarcianQuiz from "$lib/assets/igarcian/quiz.png"
  import IGarcianRoom from "$lib/assets/igarcian/room.png"
  import IGarcianStartQuiz from "$lib/assets/igarcian/start-quiz.png"

  import Project from "../components/Project.svelte";
  import {
    EnvelopeSolid,
    FacebookSolid,
    GithubSolid,
    LinkedinSolid,
    PhoneSolid,
  } from "flowbite-svelte-icons";
  import { onMount } from "svelte";

  import { MediaQuery } from "svelte/reactivity";
  const mediumMediaQuery = new MediaQuery("min-width: 768px");

  // const showOnPx: number = 1;
  // let shadow: boolean = $state(false);
  let switchElement: HTMLButtonElement;
  let currentTheme: "frontend" | "game" = $state("game");
  let cursorPath: HTMLElement;
  let activeProject: string = $state("");

  let labelClass: string = $state(`
    font-bold w-full w-full
  `);

  let inputClass: string = $state(`
    border rounded-2xl px-2 py-3 font-normal
  `);

  onMount(() => {
    cursorPath = document.getElementById("cursorPath") as HTMLElement;
    switchElement = document.getElementById(
      "switchElement",
    ) as HTMLButtonElement;
  });

  function switchTitle() {
    switchElement.classList.toggle(
      mediumMediaQuery.current ? "-translate-y-15" : "-translate-y-9",
    );
    currentTheme = currentTheme === "frontend" ? "game" : "frontend";
    cursorPath.setAttribute(
      "fill",
      currentTheme === "game" ? "rgb(247, 119, 84)" : "rgb(44, 104, 123)",
    );
  }

  function onHeaderClick(headerId: number) {
    const id: string = `project_${headerId}`;
    activeProject = activeProject === id ? "" : id;
  }
</script>

<!-- <svelte:window onscroll={handleOnScroll} /> -->

{#snippet github()}
  <a href="https://github.com/cjlangreo" target="_blank">
    <GithubSolid class="size-10" />
  </a>
{/snippet}

{#snippet linkedin()}
  <a href="https://www.linkedin.com/in/cjlangreo/" class="transition-colors">
    <LinkedinSolid class="size-10" />
  </a>
{/snippet}

{#snippet facebook()}
  <a href="https://www.facebook.com/gboy.ra.1" target="_blank">
    <FacebookSolid class="size-10" />
  </a>
{/snippet}

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
  <div class="absolute right-3 hidden md:flex gap-x-2">
    {@render github()}
    {@render linkedin()}
    {@render facebook()}
  </div>
</div>

<div class="flex flex-col items-center">
  <section
    id="home"
    class="bg-background-main w-full flex flex-col items-center py-24 px-5 gap-y-32"
  >
    <div class="flex flex-col lg:flex-row items-center gap-x-10">
      <p
        class="lg:hidden text-4xl md:text-6xl text-center text-nowrap transition-colors {currentTheme ===
        'game'
          ? 'text-game'
          : 'text-frontend'}"
      >
        chanz jryko langreo
      </p>
      <div
        class="rounded-full overflow-clip transition-colors mt-16 lg:mt-0 {currentTheme ===
        'game'
          ? 'shadow-game bg-game'
          : 'shadow-frontend bg-frontend'} shadow-2xl w-fit h-auto"
      >
        <img src={MePhoto} alt="" class="w-96" />
      </div>

      <div class="font-semibold flex items-start gap-x-3 mt-24 lg:mt-0">
        <button
          id="switchElement"
          class="flex flex-col *:text-end cursor-pointer transition-transform"
          onclick={switchTitle}
        >
          <Heading id="game" class="text-3xl sm:text-6xl text-game"
            >Game</Heading
          >
          <Heading id="frontend" class="text-3xl sm:text-6xl text-frontend"
            >Frontend</Heading
          >
        </button>
        <div class="flex flex-col">
          <Heading class="text-primary text-3xl sm:text-6xl">Developer</Heading>
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
    <div class="">
      <p class="text-2xl text-center text-nowrap">
        <span class="text-frontend"
          >Frontend Developer by <strong>profession</strong>.</span
        ><br />
        <span class="text-game"
          >Game Developer by <strong>passion</strong>.</span
        >
      </p>
    </div>
  </section>

  <div class="p-5 w-full">
    <section
      id="projects"
      class="flex flex-col justify-center gap-y-16 bg-background-alt items-center rounded-4xl py-5 px-5 w-full"
    >
      <Heading
        tag="h2"
        class="text-6xl {currentTheme === 'game'
          ? 'text-game'
          : 'text-frontend'} transition-colors">PROJECTS</Heading
      >
      <div class="flex flex-col gap-y-16 items-center w-full">
        <Project
          introText="I, Garcian: An Educational Game for Enhancing Student Engagement"
          image={IGarcianMenu}
          type="game"
          open={activeProject === "project_1"}
          onHeaderClick={() => onHeaderClick(1)}
          projectName="I, Garcian"
          position="Project Manager / Lead Developer"
        >
        <div class="flex flex-col px-3 my-3">
          <iframe
            class="w-full aspect-video"
            src="https://www.youtube.com/embed/AGUGJzNJFLk"
            title="I, Garcian | Trailer"
            frameborder="0"
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
            referrerpolicy="strict-origin-when-cross-origin"
            allowfullscreen
          ></iframe>
          <p>I, Garcian's Trailer</p>

          <img src={IGarcianMenu} alt="" class="w-full mt-10">
          <h2>Main Menu</h2>
          
          <img src={IGarcianCharacterCreate} alt="" class="w-full mt-10">
          <h2>Character Creation</h2>

          <img src={IGarcianRoom} alt="" class="w-full mt-10">
          <h2>Player Room</h2>

          <img src={IGarcianStartQuiz} alt="" class="w-full mt-10">
          <h2>Starting a quiz</h2>

          <img src={IGarcianQuiz} alt="" class="w-full mt-10">
          <h2>Quiz Time</h2>
          
          <img src={IGarcianMinigame} alt="" class="w-full mt-10">
          <h2>One of the several available minigames</h2>
          
          
        </div>
        </Project>

        <Project
          image={VoyagersMainMenu}
          open={activeProject === "project_2"}
          position="Project Manager / Lead Developer"
          type="game"
          onHeaderClick={() => onHeaderClick(2)}
          projectName="Voyagers"
          introText="Voyagers, a Space Adventure"
        >
          <div class="px-3 my-3 flex flex-col">
            <p class="text-lg">
              Voyagers is an educational game that aims to teach elementary grade students
              about various scientific terminologies. This project was commissioned to us
              to assist in this goal.
            </p>
            
            <img src={VoyagersMainMenu} alt="" class="w-full rounded-2xl mt-10">
            <h2>Main Menu</h2>
            
            <img src={VoyagersStart} alt="" class="w-full rounded-2xl mt-10">
            <h2>Game Start</h2>

            <img src={VoyagersMission} alt="" class="w-full rounded-2xl mt-10">
            <h2>Mission Node</h2>

            <img src={VoyagersGame} alt="" class="w-full rounded-2xl mt-10">
            <h2>Mission</h2>
            
          </div>
        </Project>

        <Project
          image={TymnAboutUs}
          open={activeProject === "project_3"}
          onHeaderClick={() => onHeaderClick(3)}
          position="Co-developer"
          introText="TYMN, A Facial Recognition Student Attendance Checker"
          type="frontend"
          github="https://github.com/cjlangreo/tymn-attendance-checker"
          projectName="Tymn"
        >
          <div class="px-3 my-3 flex flex-col">
            <p class="text-lg">
              Developed as a school project. Tymn uses a pre-trained AI to
              recognize students' faces recorded in a database to take their
              attendance if previous records are found, if not, uses their
              facial data to register them as a new student. Also has the
              ability to use your Android phone's camera for the facial
              recognition.
            </p>
            
            <img src={TymnScan} alt="" class="w-full scale-[107%] mt-10">
            <h2>Scanning</h2>

            <img src={TymnAttendance} alt="" class="w-full scale-[107%] mt-10">
            <h2>Attendance</h2>

            <img src={TymnAddStudent} alt="" class="w-full scale-[107%] mt-10">
            <h2>Add Student</h2>
            
            <img src={TymnAboutUs} alt="" class="w-full scale-[107%] mt-10">
            <h2>About Us</h2>
            
          </div>
        </Project>
      </div>
    </section>
  </div>

  <section
    id="contact"
    class="my-36 flex flex-col gap-y-8 items-center w-full max-w-[700px] px-5"
  >
    <Heading
      tag="h2"
      class="text-6xl {currentTheme === 'game' ? 'text-game' : 'text-frontend'}"
    >
      CONTACT ME
    </Heading>
    <form
      method="POST"
      action="https://api.web3forms.com/submit"
      class="flex flex-col gap-y-3 w-full"
    >
      <input
        type="hidden"
        name="access_key"
        value="3fa294c4-6b0e-4b6c-be22-e004095070d0"
      />
      <Label class="{labelClass} ">
        Name
        <Input
          maxlength={30}
          class="{inputClass} "
          type="text"
          name="name"
          required
        />
      </Label>
      <Label class="{labelClass} ">
        Email
        <Input
          maxlength={50}
          class="{inputClass} "
          type="email"
          required
          name="email"
        />
      </Label>
      <Label class="{labelClass} ">
        Message
        <Textarea
          maxlength={200}
          class="{inputClass} w-full"
          name="message"
          required
        />
      </Label>
      <Button
        type="submit"
        class="{currentTheme === 'game'
          ? 'bg-game'
          : 'bg-frontend'} rounded-full text-2xl text-background-alt font-bold py-1 cursor-pointer w-fit"
        >Submit</Button
      >
    </form>
  </section>
  <footer class="py-5">
    <ul
      class="flex w-full gap-y-5 md:gap-y-0 md:flex-row flex-col gap-x-5 *:flex *:flex-col *:justify-center *:items-center {currentTheme ===
      'game'
        ? 'text-game'
        : 'text-frontend'}"
    >
      <li class="">
        <EnvelopeSolid class="size-8 " />
        langreo.grim@gmail.com
      </li>
      <li class="">
        <PhoneSolid class="size-8 " />
        (+63) 908 242 9838
      </li>

      <li>
        <div class="flex gap-x-5">
          {@render github()}
          {@render linkedin()}
          {@render facebook()}
        </div>
      </li>
    </ul>
  </footer>
  <div class="bg-white w-full text-center text-gray-600">
    Portfolio is a work in progress.
  </div>
</div>
