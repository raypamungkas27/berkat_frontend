<template>

  <div id="app">
    <!-- <nav class="navbar navbar-dark shadow-sm">
  <div class="container">
    <a href="/" class="navbar-brand text-dark fs-1 fw-bold">Movie</a>

    <v-form class="d-flex" role="search" >
      <v-autocomplete clearable hide-no-data hide-selected label="Search" flat :items="movies" item-text="title" item-value="id" id="Search">
        <template v-slot:item="{item}">
              <v-btn text :to="`/movie/${item.id}`">{{item.title}}</v-btn>
        </template>
      </v-autocomplete>
    </v-form>
  </div>
</nav> -->
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
      <div class="container">


        <a class="navbar-brand" href="/">Movie</a>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNavDropdown"
          aria-controls="navbarNavDropdown" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNavDropdown">
          <ul class="navbar-nav">

            <li class="nav-item dropdown">
              <a class="nav-link " href="/kategori/now_playing" >
                Now Playing
              </a>
            </li>
            <li class="nav-item dropdown">
              <a class="nav-link " href="/kategori/popular" >
                Popular
              </a>
            </li>
            <li class="nav-item dropdown">
              <a class="nav-link " href="/kategori/top_rated" >
                Top Rated
              </a>
            </li>
            <li class="nav-item dropdown">
              <a class="nav-link " href="/kategori/upcoming" >
                Up Coming
              </a>
            </li>

          </ul>
        </div>
      </div>
    </nav>
  </div>
</template>

<script>
  export default {
    data: () => ({
      drawer: null,
      model: '',
      search: null,
      movies: []
    }),
    mounted() {
      this.loadMovies();
      this.loadKategori();
    },
    methods: {
      loadMovies: async function () {
        try {
          const response = await this.$http.get("/movie/popular");
          this.movies = response.data.results;

        } catch (error) {
          console.log(error);
        }
      },
      loadKategori: async function () {

      }
    }
  }
</script>
<style></style>