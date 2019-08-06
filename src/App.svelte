<script>
  import Icons from "./Icons.svelte";
  import Pill from "./Pill.svelte";
  import { onMount } from "svelte";
  import { fly, fade } from "svelte/transition";
  import { spring } from "svelte/motion";

  let visible = false;
  onMount(() => (visible = true));

  let darkMode = false;
</script>

<style>
  /* CSS reset */
  :global(html) {
    box-sizing: border-box;
    font-family: Helvetica, Arial, sans-serif;
  }

  *,
  *:before,
  *:after {
    box-sizing: inherit;
  }

  :global(body, h1, h2, h3, h4, h5, h6, p, ol, ul) {
    margin: 0;
    padding: 0;
    font-weight: normal;
  }

  :global(ol, ul) {
    list-style: none;
  }

  :global(img) {
    max-width: 100%;
    height: auto;
  }

  /* styles */
  header {
    font-size: 3em;
    font-weight: bold;
    text-align: center;
  }

  section {
    padding: 1em;
    border: 2px solid #333;
    box-shadow: 10px 15px 0px #333;
    margin-right: 10px;
    margin-bottom: 2em;
  }

  .container {
    display: grid;
    grid-gap: 1em;
    grid-template-columns: 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr;
    grid-auto-rows: min-content;

    grid-template-areas:
      ". . header header header header . ."
      ". section-1 section-1 section-1 section-3 section-3 section-3 ."
      ". section-2 section-2 section-2 section-4 section-4 section-4 .";
  }

  header {
    grid-area: header;
    display: flex;
    flex-flow: column nowrap;
  }

  h3 {
    text-align: center;
    font-size: 1.5em;
    font-weight: bold;
    border-bottom: 2px solid #333;
    padding-bottom: 0.7em;
    margin-bottom: 1em;
  }

  .section-1 {
    grid-area: section-1;
  }

  .section-2 {
    grid-area: section-2;
  }

  .section-3 {
    grid-area: section-3;
  }

  .pills {
    display: flex;
    flex-flow: row wrap;
  }

  .section-4 {
    grid-area: section-4;
  }

  .dark {
    height: 100%;
    background-color: black;
    color: gainsboro;
  }

  .dark > .container {
    background-color: black;
  }

  .dark-mode-button {
    width: 2em;
    height: 2em;
    border: 0;
    margin: 0.3em;
    background: transparent;
    cursor: pointer;
    font-size: 1.5em;
  }

  @media screen and (max-width: 950px) {
    .container {
      grid-template-areas:
        ". header header header header header header ."
        ". section-1 section-1 section-1 section-1 section-1 section-1 ."
        ". section-2 section-2 section-2 section-2 section-2 section-2 ."
        ". section-3 section-3 section-3 section-3 section-3 section-3 ."
        ". section-4 section-4 section-4 section-4 section-4 section-4 .";
    }
  }
</style>

{#if visible}
  <div class={darkMode ? 'dark' : ''}>
    <div class="container">
      <div transition:fade={{ duration: 300 }}>
        {#if darkMode}
          <button
            class="dark-mode-button"
            on:click={() => (darkMode = !darkMode)}>
            ☀️
          </button>
        {:else}
          <button
            class="dark-mode-button"
            on:click={() => (darkMode = !darkMode)}>
            🌙
          </button>
        {/if}
      </div>
      <header transition:fly={{ x: 30 }}>
        Hello, my name is Mathieu.
        <Icons {darkMode} />
      </header>

      <section class="section-1" transition:fly={{ x: 30, delay: 20 }}>
        <h3>What I do</h3>
        <p>
          I am a web developer, specialized in the front-end. I love being the
          logical glue between API architects and database analysts -> Ux
          researcher, UI designer in cross functional teams.
        </p>
        <p>
          JavaScript is my language of choice. My favourtie tool these days is
          React, but I love anything that allows to build UIs in a declarative
          way, like Vue or Svelte. Or whatever tool is consensual in the team I
          am in!
        </p>
        <p>
          I also come from a fullstack background, so I keep things interesting
          by learning Rust and Go on the side.
        </p>
        <p>
          And I love absurd little side-project that help me explore new tech!
          project cards
        </p>
      </section>

      <section class="section-2" transition:fly={{ x: 30, delay: 40 }}>
        <h3>Where I did it</h3>
        <ul>
          <li>Talon.One</li>
          - dynamic growth start-up (b2b promotion engine) - role: front-end
          (React) -sophisticated tech around flexible tool to build and evaluate
          ruser-defined rules fast - responsabilities : building new features,
          maintaining - responsabilities : features and UI (geolocation,
          collaboration with UX and UI designers), maintainance (tech debt),
          build tools (webpack), mentoring (other devs)
          <li>WooRank</li>
          - close knit team in a mature start-up (b2c SEO service)- role :
          fullstack javascript (Node + React) - microservices - continuous
          delivery (multiple deploys a day not uncommon) - Main projects : -
          maintenance and expansion of front-end codebase (implementation of a
          maintainable CSS-in-JS solution, removing tech debt while upgrading to
          React 15.6 (legacy lifecycle methods, legacy context API)) - building
          a PDF generation feature (node backend / React front-end).
          <li>Dev Academy</li>
          -
        </ul>
      </section>

      <section class="section-3" transition:fly={{ x: 30, delay: 60 }}>
        <h3>How I get it done</h3>
        Language
        <div class="pills">
          <Pill
            name="JavasScript"
            icon={`<svg role="img" viewBox="0 0 24 24" fill="#F7DF1E" xmlns="http://www.w3.org/2000/svg" height="1em">
          <title>JavaScript icon</title>
          <path d="M0 0h24v24H0V0zm22.034 18.276c-.175-1.095-.888-2.015-3.003-2.873-.736-.345-1.554-.585-1.797-1.14-.091-.33-.105-.51-.046-.705.15-.646.915-.84 1.515-.66.39.12.75.42.976.9 1.034-.676 1.034-.676 1.755-1.125-.27-.42-.404-.601-.586-.78-.63-.705-1.469-1.065-2.834-1.034l-.705.089c-.676.165-1.32.525-1.71 1.005-1.14 1.291-.811 3.541.569 4.471 1.365 1.02 3.361 1.244 3.616 2.205.24 1.17-.87 1.545-1.966 1.41-.811-.18-1.26-.586-1.755-1.336l-1.83 1.051c.21.48.45.689.81 1.109 1.74 1.756 6.09 1.666 6.871-1.004.029-.09.24-.705.074-1.65l.046.067zm-8.983-7.245h-2.248c0 1.938-.009 3.864-.009 5.805 0 1.232.063 2.363-.138 2.711-.33.689-1.18.601-1.566.48-.396-.196-.597-.466-.83-.855-.063-.105-.11-.196-.127-.196l-1.825 1.125c.305.63.75 1.172 1.324 1.517.855.51 2.004.675 3.207.405.783-.226 1.458-.691 1.811-1.411.51-.93.402-2.07.397-3.346.012-2.054 0-4.109 0-6.179l.004-.056z"/>
          </svg>`}
            color="53, 93%, 54%" />
          <Pill name="TypeScript" icon="ICON" color="204, 100%, 40%" />
        </div>
        Front-end and build tools
        <div class="pills">
          <Pill name="React" icon="ICON" color="193, 95%, 68%" />
          <Pill name="Vue" icon="ICON" color="153, 47%, 53%" />
          <Pill name="Webpack" icon="ICON" color="199, 90%, 76%" />
        </div>
        Back-end
        <div class="pills">
          <Pill name="Node" icon="ICON" color="120, 50%, 40%" />
          <Pill name="PostgreSQL" icon="ICON" color="207, 48%, 38%" />
          <Pill name="MongoDB" icon="ICON" color="121, 39%, 46%" />
          <Pill name="Docker" icon="ICON" color="201°, 82%, 43%" />
        </div>
        Collaboration and productivity
        <div class="pills">
          <Pill name="Git" icon="ICON" color="9, 86%, 57%" />
          <Pill name="VSCode" icon="ICON" color="204, 100%, 40%" />
          <Pill name="Slack" icon="ICON" color="299, 56%, 19%" />
        </div>
      </section>

      <section class="section-4" transition:fly={{ x: 30, delay: 80 }}>
        <h3>Writings</h3>
        <ul>
          <li>
            <a
              href="https://itnext.io/using-reacts-context-api-to-provide-a-localization-toolbox-for-your-components-48915f04bb54">
              Using React’s context API to provide a localization toolbox for
              your components -
            </a>
          </li>
        </ul>
      </section>
    </div>
  </div>
{/if}

<!--
	Ideas:
	- pills for technology and keywords
	- animation
	- boxy ?
 -->
