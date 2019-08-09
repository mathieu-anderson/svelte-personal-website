<script>
  export let name;
  export let icon;
  export let color;
  export let darkTheme;
  export let showPillInfo;
  export let pillInfo;

  $: scale = !showPillInfo;
  $: boxColor = darkTheme ? "0, 0%, 20%" : color;
  $: fontColor = darkTheme ? "0, 0%, 86%" : color;
  $: infoFontColor = darkTheme ? "0, 0%, 86%" : "#333";
  $: backgroundColor = darkTheme
    ? "0, 0%, 0%"
    : `${color.slice(0, color.length - 3)}98% `;
</script>

<style>
  .pill {
    z-index: 1000;
    padding: 0.3em 0.3em 0.2em 0.3em;
    margin: 0.5em;
    display: flex;
    flex-flow: row nowrap;
    transition: 150ms;
    height: auto;
    width: auto;
    font-weight: bold;
  }
  .scale:hover {
    transform: scale(1.03);
  }
  .name {
    margin-left: 0.3em;
    line-height: 1.1em;
  }

  .pill-info {
    margin-left: 1em;
    color: #333;
  }
</style>

<div
  class="pill"
  class:scale
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
