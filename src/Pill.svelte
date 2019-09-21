<script>
  export let name;
  export let icon;
  export let color;
  export let darkTheme;
  export let showPillInfo;
  export let pillInfo;
  export let iconOnly;

  $: scale = !showPillInfo;
  $: showName = false;
  $: darkTheme = darkTheme;
  $: boxColor = darkTheme ? "0, 0%, 20%" : color;
  $: fontColor = darkTheme ? "0, 0%, 86%" : color;
  $: infoFontColor = darkTheme ? "0, 0%, 86%" : "0, 0%, 30%";
  $: backgroundColor = darkTheme
    ? "0, 0%, 0%"
    : `${color.slice(0, color.length - 3)}98% `;

  const getClasses = (darkTheme, iconOnly) => {
    if (darkTheme && !iconOnly) {
      return "pill pill-darkTheme";
    } else if (darkTheme && iconOnly) {
      return "iconOnly iconOnly-darkTheme";
    } else if (!darkTheme && !iconOnly) {
      return "pill";
    } else if (!darkTheme && iconOnly) {
      return "iconOnly-pill";
    }
  };
</script>

<style>
  .pill {
    padding: 0.3em;
    margin: 0.5em;
    display: flex;
    flex-flow: row nowrap;
    font-weight: bold;
    font-family: "Lato", Helvetica, Arial, sans-serif;
    transition: box-shadow 100ms linear;
  }
  .pill:hover {
    box-shadow: 4px 6px 0px !important;
  }
  .pill-darkTheme:hover {
    box-shadow: 4px 6px 0px hsl(0, 0%, 20%) !important;
  }
  .name {
    margin-left: 0.3em;
    line-height: 1em;
  }
  .pill-info {
    font-weight: normal;
    margin: 0 0.3em 0.3em 1em;
    line-height: 1.1em;
    width: auto;
  }
  .iconOnly-pill {
    padding: 0.1em 0.2em 0.4em 0.2em;
    margin: 0.3em 0.3em;
    width: 0.8em;
    height: 0.8em;
    transition: box-shadow 100ms linear;
    cursor: pointer;
  }
  .iconOnly-pill:hover {
    box-shadow: 4px 6px 0px !important;
  }
  .iconOnly-darkTheme:hover {
    box-shadow: 4px 6px 0px hsl(0, 0%, 20%) !important;
  }
  .showName {
    padding: 0.3em;
    font-size: 0.8em;
    height: 1em;
    width: auto;
  }
  .showName > div > div {
    margin-left: 0;
  }
</style>

<div
  on:click={() => {
    if (iconOnly) {
      showName = !showName;
    }
  }}
  class={getClasses(darkTheme, iconOnly)}
  class:darkTheme
  class:iconOnly
  class:showName
  style="border: 2px solid hsl({boxColor}); background-color: hsl({backgroundColor});
  color: hsl({fontColor}); box-shadow: 0px 0px 0px hsl({boxColor});"
  title={name}>
  <div style="height: 1em">
    {#if showName}
      <div class="name">{name}</div>
    {:else}
      {@html icon}
    {/if}
  </div>
  {#if !iconOnly}
    <div class="name">{name}</div>
    {#if showPillInfo}
      <div class="pill-info" style="color: hsl({infoFontColor})">
        {@html pillInfo}
      </div>
    {/if}
  {/if}
</div>
