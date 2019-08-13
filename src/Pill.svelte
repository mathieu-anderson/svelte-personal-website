<script>
  export let name;
  export let icon;
  export let color;
  export let darkTheme;
  export let showPillInfo;
  export let pillInfo;

  $: scale = !showPillInfo;
  $: darkTheme = darkTheme;
  $: boxColor = darkTheme ? "0, 0%, 20%" : color;
  $: fontColor = darkTheme ? "0, 0%, 86%" : color;
  $: infoFontColor = darkTheme ? "0, 0%, 86%" : "0, 0%, 30%";
  $: backgroundColor = darkTheme
    ? "0, 0%, 0%"
    : `${color.slice(0, color.length - 3)}98% `;
</script>

<style>
  .darkTheme {
    transition: 100ms;
  }
  .pill {
    z-index: 1000;
    padding: 0.3em 0.3em 0.2em 0.3em;
    margin: 0.5em;
    display: flex;
    flex-flow: row nowrap;
    height: auto;
    width: auto;
    font-weight: bold;
    font-family: "Lato", Helvetica, Arial, sans-serif;
  }
  .scale:hover {
    transform: scale(1.03);
  }
  .name {
    margin-left: 0.3em;
    line-height: 1em;
  }
  .pill-info {
    font-weight: normal;
    margin: 0 0.3em 0.3em 1em;
    line-height: 1.1em;
  }
</style>

<div
  class="pill"
  class:scale
  class:darkTheme
  style="border: 2px solid hsl({boxColor}); background-color: hsl({backgroundColor});
  color: hsl({fontColor}); box-shadow: 4px 6px 0px hsl({boxColor});"
  title={name}>
  <div class="icon">
    {@html icon}
  </div>
  <div class="name">{name}</div>
  <div class="pill-info" style="color: hsl({infoFontColor})">
    {#if showPillInfo}
      {@html pillInfo}
    {/if}
  </div>
</div>
