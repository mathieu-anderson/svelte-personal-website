<script>
  export let name;
  export let icon;
  export let color;

  let backgroundColor = `${color.slice(0, 11)}95% `;
</script>

<style>
  div {
    padding: 0.3em;
    margin: 0.5em;
    width: min-content;
  }
</style>

<div
  style="border: 2px solid hsl({color}); background-color: hsl({backgroundColor});
  color: hsl({color}); box-shadow: 4px 6px 0px hsl({color});">
  {icon}{name}
</div>
