<script>
  import axios from "axios";
  import { onMount } from "svelte";
  import Trending from "./UI/Trending.svelte";

  let movies = [];
  let tvShow = [];

  onMount(async () => {
    const req = await axios(
      "https://api.themoviedb.org/3/trending/all/week?api_key=f8470eb01393c02fbae6d72d9e1bf2ff"
    );
    const res = req.data;
    for (let item of res.results) {
      item.media_type === "movie"
        ? (movies = [...movies, item])
        : (tvShow = [...tvShow, item]);
    }
  });

  $: console.log(movies);
</script>

<style type="text/scss">
  main {
    display: flex;
    flex: 1;
    background-color: #0f1324;
  }

  .side-bar {
    display: flex;
    flex-direction: column;
    padding: 0.5rem;
    background-color: rgba(255, 255, 255, 0.06);
    min-width: 15rem;

    & header {
      display: flex;
      justify-content: center;
    }

    .menu-list {
      padding-left: 1rem;
    }
  }

  #content {
    display: flex;
    flex: 1 auto;
    height: 100vh;
    overflow: hidden;
  }
</style>

<main>
  <section class="side-bar">
    <header>
      <h1>Movee.</h1>
    </header>
    <ul class="menu-list">
      <li>Movies</li>
      <li>Tv Shows</li>
    </ul>
  </section>
  <section id="content">
    <Trending {movies} />
  </section>
</main>
