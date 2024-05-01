<template>
  <div class="content">
    <Box>
      <AppInfo
        v-bind:allMoviesCount="movies.length"
        v-bind:likedMoviesCount="movies.filter((c) => c.liked).length"
      />
    </Box>
    <Box>
      <SearchPanel :updateTermHandler="updateTermHandler" />
      <MovieFilter :updateFilterHandler="updateFilterHandler" />
    </Box>
    
    <Box v-if="!movies.length && !isLoading">
      <p class="text-center fs-3 text-danger">Kinolar yoq</p>
    </Box>
    <Box v-if="isLoading" class="text-center">
      <Loader />
    </Box>
    <Box v-else>
      <MovieList
        :movies="onFilterHandler(onSearchHandler(movies, term), filter)"
        @onToggle="onToggleHandler"
        @onDelete="onDeleteHandler"
      />
    </Box>
    
    <Box>
      <AddMovie @createMovie="createMovie" />
    </Box>
  </div>
</template>

<script>
  import AppInfo from "@/components/app-info/AppInfo.vue";
  import SearchPanel from "@/components/search-filter/SearchPanel.vue";
  import MovieFilter from "@/components/movie-filter/MovieFilter.vue";
  import MovieList from "@/components/movie-list/MovieList.vue";
  import AddMovie from "@/components/add-movie/AddMovie.vue";
  import axios from "axios";
import Box from "@/ui-components/Box.vue";
import Loader from "@/ui-components/Loader.vue";
  export default {
    components: {
      AppInfo,
      SearchPanel,
      MovieList,
      AddMovie,
      MovieFilter,
    },
    data() {
      return {
        movies: [],
        term: '',
        filter: 'all',
        isLoading: false,
      };
    },
    methods: {
      createMovie(item) {
        this.movies.push(item);
      },
      onToggleHandler({ id, prop }) {
        this.movies = this.movies.map((movie) => {
          if (movie.id == id) {
            return { ...movie, [prop]: !movie[prop] };
          }
          return movie;
        });
      },
      onDeleteHandler(id) {
        this.movies = this.movies.filter(c => c.id !== id)
      },
      onSearchHandler(arr, term) {
        if(term.length == 0) {
          return arr;
        }

        return arr.filter(c => c.name.toLowerCase().indexOf(term) > -1)
      },
      onFilterHandler(arr, filter) {
        switch(filter) {
          case 'popular':
            return arr.filter(c => c.favourited);
          case 'most_viewed':
            return arr.filter(c => c.seen_count > 700)
          default:
            return arr;
        }
      },
      updateFilterHandler(filter) {
        this.filter = filter
      },
      updateTermHandler(term) {
        this.term = term
      },

      async fetchMovie() {
        try {
          this.isLoading = true
          const {data} = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10')
          const newArr = data.map(item => ({
            id: item.id,
            name: item.title,
            liked: false,
            favourited: false,
            seen_count: item.id * 10,
          }))
          this.movies = newArr
          // this.isLoading = false
        } catch (error) {
          alert(error.message) 
        } finally {
          this.isLoading = false
        }
      }
    },
    mounted() {
      this.fetchMovie()
    }
  }
</script>

<style>
.content {
  width: 1000px;
  min-height: 700px;
  background-color: #fff;
  margin: 0 auto;
  padding: 5rem 0;
  font-family: calibri;
}

.item {
  margin-top: 2rem;
  padding: 1.5rem;
  background-color: #fcfaf5;
  border-radius: 4px;
  box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
}
</style>
