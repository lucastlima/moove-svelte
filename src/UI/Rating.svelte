<script>
  import SvgStart from "./SvgStar.svelte";
  export let rating = 0;
</script>

<style>
  .rating-wrapper {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 12rem;
    fill: white;
    margin-left: 0.5rem;
  }
</style>

<div class="rating-wrapper">
  <SvgStart />
</div>
