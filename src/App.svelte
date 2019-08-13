<script>
  import SocialIcons from "./SocialIcons.svelte";
  import Pill from "./Pill.svelte";
  import { onMount } from "svelte";
  import { fly, fade } from "svelte/transition";
  import { spring } from "svelte/motion";

  let visible = false;
  onMount(() => (visible = true));

  const getInitialTheme = () => {
    let hour = new Date(Date.now()).getHours();
    return hour >= 19 && hour <= 7;
  };

  $: darkTheme = getInitialTheme();
  $: showPillInfo = {
    JavaScript: false,
    TypeScript: false,
    Sass: false,
    CSS: false,
    React: false,
    Vue: false,
    Webpack: false,
    Node: false,
    Docker: false,
    Git: false,
    CircleCi: false,
    VSCode: false,
    Slack: false
  };
</script>

<style>
  /* Webfonts */
  @import url("https://fonts.googleapis.com/css?family=Bitter:700");
  @import url("https://fonts.googleapis.com/css?family=Lato");

  /* CSS reset */
  :global(html) {
    box-sizing: border-box;
  }

  *,
  *:before,
  *:after {
    box-sizing: inherit;
  }

  :global(body, button, h1, h2, h3, h4, h5, h6, p, ol, ul) {
    margin: 0;
    padding: 0;
  }

  :global(ol, ul) {
    list-style: none;
  }

  /* Styles */

  a {
    font-weight: bold;
    color: #1488c6;
    text-decoration: none;
  }

  a:hover {
    border-bottom: 2px solid #1488c6;
  }

  section {
    font-family: "Lato", Helvetica, Arial, sans-serif;
    padding: 0 1em 0.7em 1em;
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
      ". header header header header header header ."
      ". section-1 section-1 section-1 section-3 section-3 section-3 ."
      ". section-2 section-2 section-2 section-4 section-4 section-4 .";
  }

  header {
    grid-area: header;
    font-size: 2.5em;
    margin-right: 10px;
    display: flex;
    flex-flow: column nowrap;
  }

  h1 {
    color: #333;
    font-family: "Bitter", Helvetica, sans-serif;
    font-size: 1em;
  }

  h1:hover {
    cursor: default;
    animation: flow 5s ease-in-out infinite;
    background: linear-gradient(
      to left,
      #4a154b,
      #ecd209,
      #007acc,
      #61dafb,
      #4fc08d,
      #8dd6f9,
      #339933,
      #1488c6,
      #343434
    );
    background-size: 300%;
    -webkit-background-clip: text;
    background-clip: text;
    -webkit-text-fill-color: transparent;
  }

  @keyframes flow {
    0% {
      background-position: 0 50%;
    }
    50% {
      background-position: 100% 50%;
    }
    100% {
      background-position: 0 50%;
    }
  }

  h3 {
    color: #333;
    font-family: "Bitter", Helvetica, sans-serif;
    text-align: center;
    font-size: 1.5em;
    font-weight: bold;
    border-bottom: 2px solid #333;
    padding-bottom: 0.1em;
    margin-bottom: 0.5em;
    line-height: 1.5em;
  }

  p {
    color: #333;
    margin-bottom: 0.3em;
  }

  ul {
    color: #333;
  }

  b {
    font-size: 1.1em;
  }

  .blog-posts-list {
    list-style: square;
  }

  .blog-posts-list-item {
    margin-left: 1em;
    padding: 0.5em 0;
  }

  .title-icons {
    display: flex;
    flex-flow: row nowrap;
    justify-content: space-between;
  }

  .section-1 {
    grid-area: section-1;
  }

  .section-2 {
    grid-area: section-2;
  }

  .section-3 {
    grid-area: section-3;
    display: flex;
    flex-flow: column nowrap;
  }

  .pills {
    display: flex;
    flex-flow: row wrap;
  }

  .pill-container {
    cursor: pointer;
  }

  .section-4 {
    grid-area: section-4;
  }

  .title-icons {
    display: flex;
    flex-flow: row nowrap;
    justify-content: space-between;
  }

  .darkTheme {
    height: 100%;
    background-color: black;
    transition: 300ms;
  }

  .darkTheme > div > header > h1 {
    transition: 300ms;
    color: gainsboro;
  }

  .darkTheme > div > section > h3 {
    transition: 300ms;
    color: gainsboro;
  }

  .darkTheme > div > section > p {
    transition: 300ms;
    color: gainsboro;
  }

  .darkTheme > div > section > ul {
    transition: 300ms;
    color: gainsboro;
  }

  .darkTheme > .container {
    background-color: black;
  }

  .darkTheme-button {
    background: transparent;
    cursor: pointer;
    border: 0;
    font-size: 0.6em;
    padding: 0.1em 0.2em 0.3em 0.2em;
    color: transparent;
    height: 1em;
    width: 1em;
    overflow: hidden;
    border-radius: 50%;
    transition: 150ms;
  }

  .darkTheme-button:hover {
    transform: scale(1.1);
  }

  .darkTheme-button-light-color {
    text-shadow: 0 0 0 gainsboro;
  }
  .darkTheme-button-light-color:focus {
    outline: 0;
    box-shadow: 0 0 10px 0px gainsboro;
  }

  .darkTheme-button-dark-color {
    text-shadow: 0 0 0 #333;
  }
  .darkTheme-button-dark-color:focus {
    outline: 0;
    box-shadow: 0 0 10px 0px #333;
  }

  @media screen and (max-width: 950px) {
    .container {
      grid-template-columns: 0.5fr 1fr 1fr 1fr 1fr 1fr 1fr 0.5fr;
      grid-template-areas:
        ". header header header header header header ."
        ". section-1 section-1 section-1 section-1 section-1 section-1 ."
        ". section-3 section-3 section-3 section-3 section-3 section-3 ."
        ". section-2 section-2 section-2 section-2 section-2 section-2 ."
        ". section-4 section-4 section-4 section-4 section-4 section-4 .";
    }
  }
</style>

{#if visible}
  <div class:darkTheme>
    <div class="container">
      <header transition:fly={{ x: 30, delay: 50 }}>
        <h1>Mathieu Anderson is a web dev</h1>
        <div class="title-icons">
          <SocialIcons {darkTheme} />
          <button
            class="darkTheme-button"
            class:darkTheme-button-light-color={darkTheme}
            class:darkTheme-button-dark-color={!darkTheme}
            title="Switch to {darkTheme ? 'light' : 'dark'} theme"
            on:click={() => (darkTheme = !darkTheme)}>
            {#if !darkTheme}🌙{:else}☀️{/if}
          </button>
        </div>
      </header>

      <section class="section-1" transition:fly={{ x: 30, delay: 80 }}>
        <h3>What I do</h3>
        <p>
          I am a
          <b>front-end</b>
          specialist. I love being part of cross-functional teams and being the
          <b>logical glue</b>
          between the back-end devs and the designers.
        </p>
        <p>
          My favourite tool is
          <b>React</b>
          , but I love anything that allows to build UIs in a
          <b>declarative way</b>
          . And I always adopt whatever is consensual in the team!
        </p>
        <p>
          I also come from a
          <b>fullstack background</b>
          , so I am familiar with back-end tech (Node and Go). And I keep things
          interesting by learning Rust on the side!
        </p>
      </section>

      <section class="section-2" transition:fly={{ x: 30, delay: 140 }}>
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

      <section class="section-3" transition:fly={{ x: 30, delay: 110 }}>
        <h3>How I get it done</h3>
        <!-- TODO : Show / Hide all behaviour
        <div class="pills">
          <div
            class="pill-container"
            on:click={() => {
              (showPillInfo.JavaScript = !showPillInfo.JavaScript), (showPillInfo.TypeScript = !showPillInfo.TypeScript), (showPillInfo.React = !showPillInfo.React), (showPillInfo.Vue = !showPillInfo.Vue), (showPillInfo.Webpack = !showPillInfo.Webpack), (showPillInfo.Node = !showPillInfo.Node), (showPillInfo.Docker = !showPillInfo.Docker), (showPillInfo.Git = !showPillInfo.Git), (showPillInfo.CircleCi = !showPillInfo.CircleCi), (showPillInfo.VSCode = !showPillInfo.VSCode), (showPillInfo.Slack = !showPillInfo.Slack), (showPillInfo.JavaScript = !showPillInfo.JavaScript), (showPillInfo.JavaScript = !showPillInfo.JavaScript);
            }}>
            <Pill
              name={'Show all'}
              icon=""
              color="0, 0%, 0%"
              {darkTheme}
              pillInfo="" />
          </div>
        </div> -->
        <div class="pills">
          <div
            class="pill-container"
            on:click={() => {
              showPillInfo.JavaScript = !showPillInfo.JavaScript;
            }}>
            <Pill
              name="JavaScript"
              icon={`<svg role="img" viewBox="0 0 24 24" fill="#ECD209" height="1em" xmlns="http://www.w3.org/2000/svg"><title>JavaScript icon</title><path d="M0 0h24v24H0V0zm22.034 18.276c-.175-1.095-.888-2.015-3.003-2.873-.736-.345-1.554-.585-1.797-1.14-.091-.33-.105-.51-.046-.705.15-.646.915-.84 1.515-.66.39.12.75.42.976.9 1.034-.676 1.034-.676 1.755-1.125-.27-.42-.404-.601-.586-.78-.63-.705-1.469-1.065-2.834-1.034l-.705.089c-.676.165-1.32.525-1.71 1.005-1.14 1.291-.811 3.541.569 4.471 1.365 1.02 3.361 1.244 3.616 2.205.24 1.17-.87 1.545-1.966 1.41-.811-.18-1.26-.586-1.755-1.336l-1.83 1.051c.21.48.45.689.81 1.109 1.74 1.756 6.09 1.666 6.871-1.004.029-.09.24-.705.074-1.65l.046.067zm-8.983-7.245h-2.248c0 1.938-.009 3.864-.009 5.805 0 1.232.063 2.363-.138 2.711-.33.689-1.18.601-1.566.48-.396-.196-.597-.466-.83-.855-.063-.105-.11-.196-.127-.196l-1.825 1.125c.305.63.75 1.172 1.324 1.517.855.51 2.004.675 3.207.405.783-.226 1.458-.691 1.811-1.411.51-.93.402-2.07.397-3.346.012-2.054 0-4.109 0-6.179l.004-.056z"/></svg>`}
              color="53, 93%, 48%"
              {darkTheme}
              showPillInfo={showPillInfo.JavaScript}
              pillInfo={`<ul>
                  <li>Used for 3 years</li>
                  <li>
                    Love the flexibility to be used in the front-end and the
                    back-end, the speed and ease of development
                  </li>
                </ul>`} />
          </div>
          <div
            class="pill-container"
            on:click={() => {
              showPillInfo.TypeScript = !showPillInfo.TypeScript;
            }}>
            <Pill
              name="TypeScript"
              icon={`<svg role="img" viewBox="0 0 24 24" fill="#007ACC" height="1em" xmlns="http://www.w3.org/2000/svg"><title>TypeScript icon</title><path d="M0 12v12h24V0H0zm19.341-.956c.61.152 1.074.423 1.501.865.221.236.549.666.575.77.008.03-1.036.73-1.668 1.123-.023.015-.115-.084-.217-.236-.31-.45-.633-.644-1.128-.678-.728-.05-1.196.331-1.192.967a.88.88 0 0 0 .102.45c.16.331.458.53 1.39.933 1.719.74 2.454 1.227 2.911 1.92.51.773.625 2.008.278 2.926-.38.998-1.325 1.676-2.655 1.9-.411.073-1.386.062-1.828-.018-.964-.172-1.878-.648-2.442-1.273-.221-.243-.652-.88-.625-.925.011-.016.11-.077.22-.141.108-.061.511-.294.892-.515l.69-.4.145.214c.202.308.643.731.91.872.766.404 1.817.347 2.335-.118a.883.883 0 0 0 .313-.72c0-.278-.035-.4-.18-.61-.186-.266-.567-.49-1.649-.96-1.238-.533-1.771-.864-2.259-1.39a3.165 3.165 0 0 1-.659-1.2c-.091-.339-.114-1.189-.042-1.531.255-1.197 1.158-2.03 2.461-2.278.423-.08 1.406-.05 1.821.053zm-5.634 1.002l.008.983H10.59v8.876H8.38v-8.876H5.258v-.964c0-.534.011-.98.026-.99.012-.016 1.913-.024 4.217-.02l4.195.012z"/></svg>`}
              color="204, 100%, 40%"
              showPillInfo={showPillInfo.TypeScript}
              pillInfo={`<ul>
                  <li>Used for 1 years</li>
                  <li>
                    Love the productivity boost it brings to large projects and
                    complex projects.
                  </li>
                </ul>`}
              {darkTheme} />
          </div>
        </div>
        <div class="pills">
          <div
            class="pill-container"
            on:click={() => {
              showPillInfo.React = !showPillInfo.React;
            }}>
            <Pill
              name="React"
              icon={`<svg role="img" viewBox="0 0 24 24" fill="#61DAFB" height="1em" xmlns="http://www.w3.org/2000/svg"><title>React icon</title><path d="M12 9.861A2.139 2.139 0 1 0 12 14.139 2.139 2.139 0 1 0 12 9.861zM6.008 16.255l-.472-.12C2.018 15.246 0 13.737 0 11.996s2.018-3.25 5.536-4.139l.472-.119.133.468a23.53 23.53 0 0 0 1.363 3.578l.101.213-.101.213a23.307 23.307 0 0 0-1.363 3.578l-.133.467zM5.317 8.95c-2.674.751-4.315 1.9-4.315 3.046 0 1.145 1.641 2.294 4.315 3.046a24.95 24.95 0 0 1 1.182-3.046A24.752 24.752 0 0 1 5.317 8.95zM17.992 16.255l-.133-.469a23.357 23.357 0 0 0-1.364-3.577l-.101-.213.101-.213a23.42 23.42 0 0 0 1.364-3.578l.133-.468.473.119c3.517.889 5.535 2.398 5.535 4.14s-2.018 3.25-5.535 4.139l-.473.12zm-.491-4.259c.48 1.039.877 2.06 1.182 3.046 2.675-.752 4.315-1.901 4.315-3.046 0-1.146-1.641-2.294-4.315-3.046a24.788 24.788 0 0 1-1.182 3.046zM5.31 8.945l-.133-.467C4.188 4.992 4.488 2.494 6 1.622c1.483-.856 3.864.155 6.359 2.716l.34.349-.34.349a23.552 23.552 0 0 0-2.422 2.967l-.135.193-.235.02a23.657 23.657 0 0 0-3.785.61l-.472.119zm1.896-6.63c-.268 0-.505.058-.705.173-.994.573-1.17 2.565-.485 5.253a25.122 25.122 0 0 1 3.233-.501 24.847 24.847 0 0 1 2.052-2.544c-1.56-1.519-3.037-2.381-4.095-2.381zM16.795 22.677c-.001 0-.001 0 0 0-1.425 0-3.255-1.073-5.154-3.023l-.34-.349.34-.349a23.53 23.53 0 0 0 2.421-2.968l.135-.193.234-.02a23.63 23.63 0 0 0 3.787-.609l.472-.119.134.468c.987 3.484.688 5.983-.824 6.854a2.38 2.38 0 0 1-1.205.308zm-4.096-3.381c1.56 1.519 3.037 2.381 4.095 2.381h.001c.267 0 .505-.058.704-.173.994-.573 1.171-2.566.485-5.254a25.02 25.02 0 0 1-3.234.501 24.674 24.674 0 0 1-2.051 2.545zM18.69 8.945l-.472-.119a23.479 23.479 0 0 0-3.787-.61l-.234-.02-.135-.193a23.414 23.414 0 0 0-2.421-2.967l-.34-.349.34-.349C14.135 1.778 16.515.767 18 1.622c1.512.872 1.812 3.37.824 6.855l-.134.468zM14.75 7.24c1.142.104 2.227.273 3.234.501.686-2.688.509-4.68-.485-5.253-.988-.571-2.845.304-4.8 2.208A24.849 24.849 0 0 1 14.75 7.24zM7.206 22.677A2.38 2.38 0 0 1 6 22.369c-1.512-.871-1.812-3.369-.823-6.854l.132-.468.472.119c1.155.291 2.429.496 3.785.609l.235.02.134.193a23.596 23.596 0 0 0 2.422 2.968l.34.349-.34.349c-1.898 1.95-3.728 3.023-5.151 3.023zm-1.19-6.427c-.686 2.688-.509 4.681.485 5.254.987.563 2.843-.305 4.8-2.208a24.998 24.998 0 0 1-2.052-2.545 24.976 24.976 0 0 1-3.233-.501zM12 16.878c-.823 0-1.669-.036-2.516-.106l-.235-.02-.135-.193a30.388 30.388 0 0 1-1.35-2.122 30.354 30.354 0 0 1-1.166-2.228l-.1-.213.1-.213a30.3 30.3 0 0 1 1.166-2.228c.414-.716.869-1.43 1.35-2.122l.135-.193.235-.02a29.785 29.785 0 0 1 5.033 0l.234.02.134.193a30.006 30.006 0 0 1 2.517 4.35l.101.213-.101.213a29.6 29.6 0 0 1-2.517 4.35l-.134.193-.234.02c-.847.07-1.694.106-2.517.106zm-2.197-1.084c1.48.111 2.914.111 4.395 0a29.006 29.006 0 0 0 2.196-3.798 28.585 28.585 0 0 0-2.197-3.798 29.031 29.031 0 0 0-4.394 0 28.477 28.477 0 0 0-2.197 3.798 29.114 29.114 0 0 0 2.197 3.798z"/></svg>`}
              color="193, 95%, 68%"
              showPillInfo={showPillInfo.React}
              pillInfo={`<ul>
                  <li>Used for XXXXX years</li>
                  <li>
                    Lorem ipsum this is sample text the hardest part of a personal website is the content
                  </li>
                </ul>`}
              {darkTheme} />
          </div>
          <div
            class="pill-container"
            on:click={() => {
              showPillInfo.Vue = !showPillInfo.Vue;
            }}>
            <Pill
              name="Vue"
              icon={`<svg role="img" viewBox="0 0 24 24" fill="#4FC08D" height="1em" xmlns="http://www.w3.org/2000/svg"><title>Vue.js icon</title><path d="M19.197 1.608l.003-.006h-4.425L12 6.4v.002l-2.772-4.8H4.803v.005H0l12 20.786L24 1.608"/></svg>`}
              color="153, 47%, 53%"
              showPillInfo={showPillInfo.Vue}
              pillInfo={`<ul>
                  <li>Used for XXXXX years</li>
                  <li>
                    Lorem ipsum this is sample text the hardest part of a personal website is the content
                  </li>
                </ul>`}
              {darkTheme} />
          </div>
          <div
            class="pill-container"
            on:click={() => {
              showPillInfo.CSS = !showPillInfo.CSS;
            }}>
            <Pill
              name="CSS"
              icon={`<svg role="img" viewBox="0 0 24 24" fill="#1572B6" height="1em" xmlns="http://www.w3.org/2000/svg"><title>CSS3 icon</title><path d="M1.5 0h21l-1.91 21.563L11.977 24l-8.565-2.438L1.5 0zm17.09 4.413L5.41 4.41l.213 2.622 10.125.002-.255 2.716h-6.64l.24 2.573h6.182l-.366 3.523-2.91.804-2.956-.81-.188-2.11h-2.61l.29 3.855L12 19.288l5.373-1.53L18.59 4.414z"/></svg>`}
              color="205, 79%, 40%"
              showPillInfo={showPillInfo.CSS}
              pillInfo={`<ul>
                  <li>Used for XXXXX years</li>
                  <li>
                    Lorem ipsum this is sample text the hardest part of a personal website is the content
                  </li>
                </ul>`}
              {darkTheme} />
          </div>

          <div
            class="pill-container"
            on:click={() => {
              showPillInfo.Sass = !showPillInfo.Sass;
            }}>
            <Pill
              name="Sass"
              icon={`<svg role="img" viewBox="0 0 24 24" fill="#CC6699" height="1em" xmlns="http://www.w3.org/2000/svg"><title>Sass icon</title><path d="M12 0c6.627 0 12 5.373 12 12s-5.373 12-12 12S0 18.627 0 12 5.373 0 12 0zM9.615 15.998c.175.645.156 1.248-.024 1.792l-.065.18c-.024.061-.052.12-.078.176-.14.29-.326.56-.555.81-.698.759-1.672 1.047-2.09.805-.45-.262-.226-1.335.584-2.19.871-.918 2.12-1.509 2.12-1.509v-.003l.108-.061zm9.911-10.861c-.542-2.133-4.077-2.834-7.422-1.645-1.989.707-4.144 1.818-5.693 3.267C4.568 8.48 4.275 9.98 4.396 10.607c.427 2.211 3.457 3.657 4.703 4.73v.006c-.367.18-3.056 1.529-3.686 2.925-.675 1.47.105 2.521.615 2.655 1.575.436 3.195-.36 4.065-1.649.84-1.261.766-2.881.404-3.676.496-.135 1.08-.195 1.83-.104 2.101.24 2.521 1.56 2.43 2.1-.09.539-.523.854-.674.944-.15.091-.195.12-.181.181.015.09.091.09.21.075.165-.03 1.096-.45 1.141-1.471.045-1.29-1.186-2.729-3.375-2.7-.9.016-1.471.091-1.875.256-.03-.045-.061-.075-.105-.105-1.35-1.455-3.855-2.475-3.75-4.41.03-.705.285-2.564 4.8-4.814 3.705-1.846 6.661-1.335 7.171-.21.733 1.604-1.576 4.59-5.431 5.024-1.47.165-2.235-.404-2.431-.615-.209-.225-.239-.24-.314-.194-.12.06-.045.255 0 .375.12.3.585.825 1.396 1.095.704.225 2.43.359 4.5-.45 2.324-.899 4.139-3.405 3.614-5.505l.073.067z"/></svg>`}
              color="330, 50%, 60%"
              showPillInfo={showPillInfo.Sass}
              pillInfo={`<ul>
                  <li>Used for XXXXX years</li>
                  <li>
                    Lorem ipsum this is sample text the hardest part of a personal website is the content
                  </li>
                </ul>`}
              {darkTheme} />
          </div>
          <div
            class="pill-container"
            on:click={() => {
              showPillInfo.Webpack = !showPillInfo.Webpack;
            }}>
            <Pill
              name="Webpack"
              icon={`<svg role="img" viewBox="0 0 24 24" fill="#8DD6F9" height="1em" xmlns="http://www.w3.org/2000/svg"><title>Webpack icon</title><path d="M21.0157 18.1202L12.351 23v-3.8007l5.3986-2.9567 3.266 1.8776zm.5927-.5344V7.3805l-3.1708 1.822v6.5593l3.1708 1.824zm-18.6827.5344L11.5904 23v-3.8007l-5.3986-2.9567-3.266 1.8776zm-.5927-.5344V7.3805l3.1707 1.822v6.5593l-3.1707 1.824zm.371-10.8656l8.8864-5.0056v3.6748L5.8974 8.507l-.0434.0248-3.15-1.8116zm18.5335 0L12.351 1.7146v3.6748l5.693 3.1177.0434.0248 3.15-1.8116zm-9.647 11.6146l-5.3262-2.9155V9.642l5.326 3.062v5.6308zm.7605 0l5.326-2.9155V9.642l-5.326 3.062v5.6308zM6.625 8.9734l5.3467-2.928 5.3468 2.928-5.3468 3.0744L6.625 8.9734z"/></svg>`}
              color="199, 90%, 76%"
              showPillInfo={showPillInfo.Webpack}
              pillInfo={`<ul>
                  <li>Used for XXXXX years</li>
                  <li>
                    Lorem ipsum this is sample text the hardest part of a personal website is the content
                  </li>
                </ul>`}
              {darkTheme} />
          </div>
          <div
            class="pill-container"
            on:click={() => {
              showPillInfo.Node = !showPillInfo.Node;
            }}>
            <Pill
              name="Node"
              icon={`<svg role="img" viewBox="0 0 24 24" fill="#339933" height="1em" xmlns="http://www.w3.org/2000/svg"><title>Node.js icon</title><path d="M11.435.153l-9.37 5.43c-.35.203-.564.578-.563.983V17.43c0 .404.215.78.564.982l9.37 5.435c.35.203.78.203 1.13 0l9.366-5.433c.35-.205.564-.578.565-.982V6.566c0-.404-.216-.78-.566-.984L12.567.152c-.35-.203-.782-.203-1.13 0"/></svg>`}
              color="120, 50%, 40%"
              showPillInfo={showPillInfo.Node}
              pillInfo={`<ul>
                  <li>Used for XXXXX years</li>
                  <li>
                    Lorem ipsum this is sample text the hardest part of a personal website is the content
                  </li>
                </ul>`}
              {darkTheme} />
          </div>

        </div>
        <div class="pills">
          <div
            class="pill-container"
            on:click={() => {
              showPillInfo.Git = !showPillInfo.Git;
            }}>
            <Pill
              name="Git"
              icon={`<svg role="img" viewBox="0 0 24 24" fill="#F05032" height="1em" xmlns="http://www.w3.org/2000/svg"><title>Git icon</title><path d="M23.546 10.93L13.067.452c-.604-.603-1.582-.603-2.188 0L8.708 2.627l2.76 2.76c.645-.215 1.379-.07 1.889.441.516.515.658 1.258.438 1.9l2.658 2.66c.645-.223 1.387-.078 1.9.435.721.72.721 1.884 0 2.604-.719.719-1.881.719-2.6 0-.539-.541-.674-1.337-.404-1.996L12.86 8.955v6.525c.176.086.342.203.488.348.713.721.713 1.883 0 2.6-.719.721-1.889.721-2.609 0-.719-.719-.719-1.879 0-2.598.182-.18.387-.316.605-.406V8.835c-.217-.091-.424-.222-.6-.401-.545-.545-.676-1.342-.396-2.009L7.636 3.7.45 10.881c-.6.605-.6 1.584 0 2.189l10.48 10.477c.604.604 1.582.604 2.186 0l10.43-10.43c.605-.603.605-1.582 0-2.187"/></svg>`}
              color="9, 86%, 57%"
              showPillInfo={showPillInfo.Git}
              pillInfo={`<ul>
                  <li>Used for XXXXX years</li>
                  <li>
                    Lorem ipsum this is sample text the hardest part of a personal website is the content
                  </li>
                </ul>`}
              {darkTheme} />
          </div>

          <div
            class="pill-container"
            on:click={() => {
              showPillInfo.Docker = !showPillInfo.Docker;
            }}>
            <Pill
              name="Docker"
              icon={`<svg role="img" viewBox="0 0 24 24" fill="#1488C6" height="1em" xmlns="http://www.w3.org/2000/svg"><title>Docker icon</title><path d="M4.82 17.275c-.684 0-1.304-.56-1.304-1.24s.56-1.243 1.305-1.243c.748 0 1.31.56 1.31 1.242s-.622 1.24-1.305 1.24zm16.012-6.763c-.135-.992-.75-1.8-1.56-2.42l-.315-.25-.254.31c-.494.56-.69 1.553-.63 2.295.06.562.24 1.12.554 1.554-.254.13-.568.25-.81.377-.57.187-1.124.25-1.68.25H.097l-.06.37c-.12 1.182.06 2.42.562 3.54l.244.435v.06c1.5 2.483 4.17 3.6 7.078 3.6 5.594 0 10.182-2.42 12.357-7.633 1.425.062 2.864-.31 3.54-1.676l.18-.31-.3-.187c-.81-.494-1.92-.56-2.85-.31l-.018.002zm-8.008-.992h-2.428v2.42h2.43V9.518l-.002.003zm0-3.043h-2.428v2.42h2.43V6.48l-.002-.003zm0-3.104h-2.428v2.42h2.43v-2.42h-.002zm2.97 6.147H13.38v2.42h2.42V9.518l-.007.003zm-8.998 0H4.383v2.42h2.422V9.518l-.01.003zm3.03 0h-2.4v2.42H9.84V9.518l-.015.003zm-6.03 0H1.4v2.42h2.428V9.518l-.03.003zm6.03-3.043h-2.4v2.42H9.84V6.48l-.015-.003zm-3.045 0H4.387v2.42H6.8V6.48l-.016-.003z"/></svg>`}
              color="201, 82%, 43%"
              showPillInfo={showPillInfo.Docker}
              pillInfo={`<ul>
                  <li>Used for XXXXX years</li>
                  <li>
                    Lorem ipsum this is sample text the hardest part of a personal website is the content
                  </li>
                </ul>`}
              {darkTheme} />
          </div>
          <div
            class="pill-container"
            on:click={() => {
              showPillInfo.CircleCi = !showPillInfo.CircleCi;
            }}>
            <Pill
              name="CircleCi"
              icon={`<svg role="img" viewBox="0 0 24 24" fill="#343434" height="1em" xmlns="http://www.w3.org/2000/svg"><title>CircleCI icon</title><path d="M8.963 12c0-1.584 1.284-2.855 2.855-2.855 1.572 0 2.856 1.284 2.856 2.855 0 1.572-1.284 2.856-2.856 2.856-1.57 0-2.855-1.284-2.855-2.856zm2.855-12C6.215 0 1.522 3.84.19 9.025c-.01.036-.01.07-.01.12 0 .313.252.576.575.576H5.59c.23 0 .433-.13.517-.333.997-2.16 3.18-3.672 5.712-3.672 3.466 0 6.286 2.82 6.286 6.287 0 3.47-2.82 6.29-6.29 6.29-2.53 0-4.714-1.5-5.71-3.673-.097-.19-.29-.336-.517-.336H.755c-.312 0-.575.253-.575.576 0 .037.014.072.014.12C1.514 20.16 6.214 24 11.818 24c6.624 0 12-5.375 12-12 0-6.623-5.376-12-12-12z"/></svg>`}
              color="0, 0%, 20%"
              showPillInfo={showPillInfo.CircleCi}
              pillInfo={`<ul>
                  <li>Used for XXXXX years</li>
                  <li>
                    Lorem ipsum this is sample text the hardest part of a personal website is the content
                  </li>
                </ul>`}
              {darkTheme} />
          </div>
        </div>
        <div class="pills">

          <div
            class="pill-container"
            on:click={() => {
              showPillInfo.VSCode = !showPillInfo.VSCode;
            }}>
            <Pill
              name="VSCode"
              icon={`<svg role="img" viewBox="0 0 24 24" fill="#007ACC" height="1em" xmlns="http://www.w3.org/2000/svg"><title>Visual Studio Code icon</title><path d="M23.15 2.587L18.21.21a1.494 1.494 0 0 0-1.705.29l-9.46 8.63-4.12-3.128a.999.999 0 0 0-1.276.057L.327 7.261A1 1 0 0 0 .326 8.74L3.899 12 .326 15.26a1 1 0 0 0 .001 1.479L1.65 17.94a.999.999 0 0 0 1.276.057l4.12-3.128 9.46 8.63a1.492 1.492 0 0 0 1.704.29l4.942-2.377A1.5 1.5 0 0 0 24 20.06V3.939a1.5 1.5 0 0 0-.85-1.352zm-5.146 14.861L10.826 12l7.178-5.448v10.896z"/></svg>`}
              color="204, 100%, 40%"
              showPillInfo={showPillInfo.VSCode}
              pillInfo={`<ul>
                  <li>Used for XXXXX years</li>
                  <li>
                    Lorem ipsum this is sample text the hardest part of a personal website is the content
                  </li>
                </ul>`}
              {darkTheme} />
          </div>
          <div
            class="pill-container"
            on:click={() => {
              showPillInfo.Slack = !showPillInfo.Slack;
            }}>
            <Pill
              name="Slack"
              icon={`<svg role="img" viewBox="0 0 24 24" fill="#4A154B" height="1em" xmlns="http://www.w3.org/2000/svg"><title>Slack icon</title><path d="M5.042 15.165a2.528 2.528 0 0 1-2.52 2.523A2.528 2.528 0 0 1 0 15.165a2.527 2.527 0 0 1 2.522-2.52h2.52v2.52zM6.313 15.165a2.527 2.527 0 0 1 2.521-2.52 2.527 2.527 0 0 1 2.521 2.52v6.313A2.528 2.528 0 0 1 8.834 24a2.528 2.528 0 0 1-2.521-2.522v-6.313zM8.834 5.042a2.528 2.528 0 0 1-2.521-2.52A2.528 2.528 0 0 1 8.834 0a2.528 2.528 0 0 1 2.521 2.522v2.52H8.834zM8.834 6.313a2.528 2.528 0 0 1 2.521 2.521 2.528 2.528 0 0 1-2.521 2.521H2.522A2.528 2.528 0 0 1 0 8.834a2.528 2.528 0 0 1 2.522-2.521h6.312zM18.956 8.834a2.528 2.528 0 0 1 2.522-2.521A2.528 2.528 0 0 1 24 8.834a2.528 2.528 0 0 1-2.522 2.521h-2.522V8.834zM17.688 8.834a2.528 2.528 0 0 1-2.523 2.521 2.527 2.527 0 0 1-2.52-2.521V2.522A2.527 2.527 0 0 1 15.165 0a2.528 2.528 0 0 1 2.523 2.522v6.312zM15.165 18.956a2.528 2.528 0 0 1 2.523 2.522A2.528 2.528 0 0 1 15.165 24a2.527 2.527 0 0 1-2.52-2.522v-2.522h2.52zM15.165 17.688a2.527 2.527 0 0 1-2.52-2.523 2.526 2.526 0 0 1 2.52-2.52h6.313A2.527 2.527 0 0 1 24 15.165a2.528 2.528 0 0 1-2.522 2.523h-6.313z"/></svg>`}
              color="299, 56%, 19%"
              showPillInfo={showPillInfo.Slack}
              pillInfo={`<ul>
                  <li>Used for XXXXX years</li>
                  <li>
                    Lorem ipsum this is sample text the hardest part of a personal website is the content
                  </li>
                </ul>`}
              {darkTheme} />
          </div>
        </div>
      </section>

      <section class="section-4" transition:fly={{ x: 30, delay: 160 }}>
        <h3>Writings</h3>
        <p>
          I love sharing knowledge, insights and learning journeys through blog
          posts and talks!
        </p>
        <ul class="blog-posts-list">
          <li class="blog-posts-list-item">
            <a
              style={darkTheme ? `color: hsl(201, 82%, 40%)` : ''}
              href="https://itnext.io/using-reacts-context-api-to-provide-a-localization-toolbox-for-your-components-48915f04bb54">
              Using React’s context API to provide a localization toolbox for
              your components
            </a>
          </li>
        </ul>
      </section>
    </div>
  </div>
{/if}
