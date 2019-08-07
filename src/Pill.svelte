<script>
  export let name;
  export let icon;
  export let color;
  export let darkTheme;

  $: boxColor = darkTheme ? "0, 0%, 20%" : color;
  $: fontColor = darkTheme ? "0, 0%, 86%" : color;
  $: backgroundColor = darkTheme
    ? "0, 0%, 0%"
    : `${color.slice(0, color.length - 3)}98% `;
</script>

<style>
  div {
    padding: 0.3em 0.3em 0.2em 0.3em;
    margin: 0.5em;
    display: flex;
    flex-flow: row nowrap;
    cursor: default;
  }
  .name {
    margin-left: 0.3em;
    line-height: 1.1em;
  }
</style>

<div
  style="border: 2px solid hsl({boxColor}); background-color: hsl({backgroundColor});
  color: hsl({fontColor}); box-shadow: 4px 6px 0px hsl({boxColor});"
  title={name}>
  <span class="icon">
    {@html icon}
  </span>
  <span class="name">{name}</span>
</div>
