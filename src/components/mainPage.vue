<template>
  <div>
    <input v-model="searchInput" type="text" placeholder="Введите название фильма" />
    <ul v-if="filteredMovies != false" class="list">
      <li v-for="movie in filteredMovies" :key="movie.Title" class="list__item">
        <h3 list__item__title>{{ movie.Title }} - {{ movie.Year }}</h3>
        <div class="list__item__list--img">
          <li v-for="img in movie.Images" :key="img" class="list__item__img">
            <img :src="img" alt="Арты">
          </li>
        </div>
      </li>
    </ul>
    <div v-else>
      <div>Фильмов с таким названием нет</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'mainPage',
  data() {
    return {
      movies: [], // данные из файла JSON
      searchInput: '', // введенное пользователем значение поиска
    };
  },
  mounted() {
    this.movies = require('../Film.JSON');
    console.log(this.movies)
  },
 computed: {
    filteredMovies() {
      const searchTerm = this.searchInput.toLowerCase();
      return this.movies.filter(movie =>
        movie.Title.toLowerCase().includes(searchTerm)
      );
    },
  },
}
</script>

<style scoped lang="scss">
.list__item__img {
  width: 200px;
  display: flex;
  margin-right: 10px;
}
.list__item__img:last-child {
  margin-right: 0;
}
.list__item__list--img {
  display: flex;
}
</style>
