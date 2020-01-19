<script>
  import SvgArrow from "./SvgArrow.svelte";
  import Rating from "./Rating.svelte";

  let trendingDiv;
  let counter = 0;
  export let movies = [];

  const url = "https://image.tmdb.org/t/p/w500";
  const imgOrginalUrl = "https://image.tmdb.org/t/p/original/";

  const handleLeftArrow = () => {
    if (counter) {
      counter--;
      trendingDiv.style.transform = `translateX(-${counter}00%)`;
    }
  };

  const handleRightArrow = () => {
    if (counter < movies.length - 1) {
      counter++;
      trendingDiv.style.transform = `translateX(-${counter}00%)`;
    }
  };

  const handleKeydown = e => {
    if (e.keyCode === 39) {
      handleRightArrow();
    } else if (e.keyCode === 37) {
      handleLeftArrow();
    }
  };
</script>

<style lang="scss">
  .trending-wrapper {
    display: flex;
    position: relative;
    width: 100%;
    height: min-content;
  }
  .arrow {
    position: absolute;
    width: 3rem;
    z-index: 3;
  }
  .arrow-left {
    fill: rgba(255, 255, 255, 0.05);
    left: 1rem;
    top: 50%;
    transform: translateY(-50%);
  }
  .arrow-right {
    fill: rgba(255, 255, 255, 0.05);
    right: 1rem;
    top: 50%;
    transform: translateY(-50%);
  }

  .trending {
    display: flex;
    width: 100%;
    height: 70vh;
    transition: transform, 0.3s ease-in;
  }

  .trend-item {
    position: relative;
    display: flex;
    min-width: 100%;
    justify-content: center;
    align-items: center;
    background-color: #0d0d1a;
    overflow: hidden;
  }
  .trend-img {
    display: flex;
    height: 100%;
    width: 100%;
    & img {
      object-position: top center;
      object-fit: cover;
      display: block;
      margin: 0 auto;
      width: 100%;
      height: 100%;
    }

    &::after {
      content: " ";
      position: absolute;
      top: 0;
      left: 0;
      z-index: 2;
      width: 100%;
      height: 100%;
      background: linear-gradient(
          to right,
          #0d0d1a,
          transparent 40%,
          transparent 60%,
          #0d0d1a
        ),
        linear-gradient(to bottom, transparent, transparent 50%, #0d0d1a 100%);
    }
  }

  .tend-info {
    position: absolute;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    z-index: 2;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    padding: 2rem;

    & .trend-rating {
      display: flex;
    }
  }

  h1 {
    font-size: 4em;
    width: 50%;
    margin: 0;
    padding: 0;
  }
</style>

<svelte:window on:keydown={handleKeydown} />

<div class="trending-wrapper">
  <div bind:this={trendingDiv} class="trending">
    {#if movies}
      {#each movies as mov, i}
        <div class="trend-item">
          <div class="trend-img">
            <img src={imgOrginalUrl + mov.backdrop_path} alt={mov.title} />
          </div>
          <div class="tend-info">
            <span>
              {`${(i + 1).toString().length > 1 ? i + 1 : '0' + (i + 1)}/${movies.length}`}
            </span>
            <h1>{mov.title}</h1>
            <div class="trend-rating">
              <span>{mov.vote_average}</span>
              <Rating />
            </div>
          </div>
        </div>
      {/each}
    {:else}
      <p style="color: #fff">loading.....</p>
    {/if}
  </div>
  <div
    style={counter === movies.length - 1 ? 'display: none' : null}
    on:click={handleRightArrow}
    class="arrow arrow-right">
    <SvgArrow />
  </div>
  <div
    style={!counter ? 'display: none' : null}
    on:click={handleLeftArrow}
    class="arrow arrow-left">
    <SvgArrow direction="left" />
  </div>
</div>
