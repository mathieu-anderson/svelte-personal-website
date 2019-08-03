<script>
  import Icons from "./Icons.svelte";
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
    margin-bottom: 2em;
  }

  .container {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr;
    grid-template-rows: 0.5fr 0.7fr 0.7fr 0.7fr 0.7fr;
    grid-template-areas:
      ". header header header header header header ."
      ". section-1 section-1 section-1 section-1 section-1 section-1 ."
      ". section-2 section-2 section-2 section-2 section-2 section-2 ."
      ". section-3 section-3 section-3 section-3 section-3 section-3 ."
      ". section-4 section-4 section-4 section-4 section-4 section-4 .";
  }

  header {
    grid-area: header;
    display: flex;
    flex-flow: column nowrap;
  }

  h3 {
    text-align: center;
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
        <p>here are some fun projects : project cards</p>
      </section>

      <section class="section-2" transition:fly={{ x: 30, delay: 40 }}>
        <h3>Where I did it</h3>
        <ul>
          <li>Talon.One</li>
          <li>WooRank</li>
          <li>Dev Academy</li>
        </ul>
      </section>

      <section class="section-3" transition:fly={{ x: 30, delay: 60 }}>
        <h3>How I do it</h3>
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
