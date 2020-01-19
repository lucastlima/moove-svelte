<script>
  export let startsCount = 10;
  const startsArr = Array(startsCount).fill("start");
</script>

<style>
  svg {
    width: 100%;
    height: 100%;
  }

  svg:not(:first-child) {
    margin-left: 5px;
  }
</style>

{#each startsArr as star}
  <svg viewBox="0 0 126.7 126.7">
    <g>
      <path
        d="M121.2,44.2l-34.9-3.3c-2.2-0.2-4.1-1.6-5-3.7L68.8,6.9c-2-5-9.1-5-11.1,0L45.3,37.2c-0.8,2.1-2.8,3.5-5,3.7L5.4,44.2
        c-5.2,0.5-7.3,7-3.4,10.5l26.3,23.1c1.7,1.5,2.4,3.7,1.9,5.9l-7.9,32.4c-1.2,5.1,4.3,9.3,8.9,6.6l29.1-17.1c1.9-1.1,4.2-1.1,6.1,0
        l29.1,17.1c4.6,2.7,10.1-1.4,8.9-6.6l-7.8-32.4c-0.5-2.2,0.2-4.4,1.9-5.9l26.3-23.1C128.6,51.2,126.4,44.7,121.2,44.2z" />
    </g>
  </svg>
{/each}
