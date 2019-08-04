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

  /* *,
  *:before,
  *:after {
    box-sizing: inherit;
  } */

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
          <Pill name="JavasScript" icon="ICON" color="51, 98%, 48%" />
          <Pill name="TypeScript" icon="ICON" color="214, 51%, 33%" />
        </div>
        Front-end and build tools
        <div class="pills">
          <Pill name="React" icon="ICON" color="193, 95%, 68%" />
          <Pill name="Vue" icon="ICON" color="155, 100%, 40%" />
          <Pill name="Webpack" icon="ICON" color="126, 100%, 40%" />
        </div>
        Back-end
        <div class="pills">
          <Pill name="Node" icon="ICON" color="126, 100%, 40%" />
          <Pill name="Postgresql" icon="ICON" color="126, 100%, 40%" />
          <Pill name="MongoDB" icon="ICON" color="126, 100%, 40%" />
        </div>
        Collaboration and productivity
        <div class="pills">
          <Pill name="Node" icon="ICON" color="126, 100%, 40%" />
          <Pill name="Git" icon="ICON" color="9, 86%, 57%" />
          <Pill name="VSCode" icon="ICON" color="9, 86%, 57%" />
          <Pill name="Slack" icon="ICON" color="9, 86%, 57%" />
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
