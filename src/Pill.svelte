<script>
  export let name;
  export let icon;
  export let color;

  let backgroundColor = `${color.slice(0, 11)}95% `;
</script>

<style>
  div {
    padding: 0.3em 0.3em 0.2em 0.3em;
    margin: 0.5em;
    display: flex;
    flex-flow: row nowrap;
  }
  .name {
    margin-left: 0.3em;
  }
</style>

<div
  style="border: 2px solid hsl({color}); background-color: hsl({backgroundColor});
  color: hsl({color}); box-shadow: 4px 6px 0px hsl({color});">
  <span class="icon">
    {@html icon}
  </span>
  <span class="name">{name}</span>
</div>
