<script>
  export let direction = null;

  const getStyle = direction => {
    switch (direction) {
      case "left":
        return "transform: rotate(180deg);";
      case "top":
        return "transform: rotate(-90deg);";
      case "down":
        return "transform: rotate(90deg);";
      default:
        return null;
    }
  };
</script>

<style>
  svg {
    width: 100%;
    height: 100%;
    pointer-events: none;
    filter: drop-shadow(3px 3px 5px rgba(0, 0, 0, 0.6));
  }
</style>

<svg
  style={getStyle(direction)}
  xmlns="http://www.w3.org/2000/svg"
  viewBox="0 0 360 450">
  <path
    d="M345.44,248.29,151.15,442.57a31.64,31.64,0,0,1-44.75-44.74L278.32,225.92,106.41,54A31.64,31.64,0,0,1,151.16,9.27L345.45,203.55a31.64,31.64,0,0,1,0,44.74Z" />
</svg>
