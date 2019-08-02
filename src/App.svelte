<script>
  import Icons from "./Icons.svelte";
</script>

<style>
  :global(html) {
    box-sizing: border-box;
    font-size: 16px;
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

  header {
    font-size: 3em;
    font-weight: bold;
    text-align: center;
  }

  section {
    padding: 1em;
    border: 1px solid grey;
    box-shadow: 10px 15px 0px black;
  }

  div {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr;
    grid-template-rows: 0.5fr 1fr 1fr 1fr 1fr;
    grid-template-areas: ". header header header header header header ." ". . section-1 section-1 section-1 section-1 . ." ". . section-2 section-2 section-2 section-2 . ." ". . section-3 section-3 section-3 section-3 . ." ". . section-4 section-4 section-4 section-4 . .";
  }

  header {
    grid-area: header;
    display: flex;
    flex-flow: column nowrap;
  }

  section {
    margin-bottom: 2em;
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
</style>

<div>
  <header>
    Hello, my name is Mathieu.
    <Icons />
  </header>

  <section class="section-1">
    <h3>What I do</h3>
    <p>
      I am a web developer, specialized in the front-end. I love being the
      logical glue between API architects and database analysts -> Ux
      researcher, UI designer in cross functional teams.
    </p>
    <p>here are some fun projects : project cards</p>
  </section>

  <section class="section-2">
    <h3>Where I did it</h3>
    <ul>
      <li>Talon.One</li>
      <li>WooRank</li>
      <li>Dev Academy</li>
    </ul>
  </section>

  <section class="section-3">
    <h3>How I do it</h3>
    <p>
      JavaScript is my language of choice. My favourtie tool these days is
      React, but I love anything that allows to build UIs in a declarative way,
      like Vue or Svelte. Or whatever tool is consensual in the team I am in!
    </p>
    <p>
      I also come from a fullstack background, so I keep things interesting by
      learning Rust and Go on the side.
    </p>
  </section>

  <section class="section-4">
    <h3>Writings</h3>
    <ul>
      <li>
        <a
          href="https://itnext.io/using-reacts-context-api-to-provide-a-localization-toolbox-for-your-components-48915f04bb54">
          Using React’s context API to provide a localization toolbox for your
          components -
        </a>
      </li>
    </ul>
  </section>

</div>

<!--
	Ideas:
	- pills for technology and keywords
	- animation
	- boxy ?
 -->
