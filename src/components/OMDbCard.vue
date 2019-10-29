<template>
  <div>
    <template v-if="isLoader">
      <div class="lds-dual-ring"></div>
    </template>
    <template v-else>
      <a :href="`https://imdb.com/title/${film.imdbID}`" target="_blank">
        <img :src="film.Poster" class="omdb__card-img" />
      </a>
      <h3 class="omdb__title">{{ film.Title }}</h3>
      <h4 class="omdb__title">{{ film.Director }}, {{ film.Year }}</h4>
    </template>
  </div>
</template>

<script>
export default {
  props: {
    id: String,
  },
  data() {
    return {
      apiKey: 'ea35794c',
      film: {},
      isLoader: true,
    };
  },
  methods: {
    getFilm() {
      fetch(`http://www.omdbapi.com/?i=${this.id}&apikey=${this.apiKey}`).then(
        async response => {
          this.film = await response.json();
          this.isLoader = false;
        }
      );
    },
  },
  created() {
    this.getFilm();
  },
};
</script>

<style>
.omdb__card-img {
  width: 100%;
  max-width: 300px;
  height: 420px;
  border: 8px solid #ffffff;
  border-radius: 5px;
  box-shadow: 0px 0px 42px 5px rgba(0, 0, 0, 0.75);
  margin-bottom: 10px;
  object-fit: cover;
  transition: all 0.5s;
}
.omdb__card-img:hover {
  transform: translateY(-5px);
}

/* loader */

.lds-dual-ring {
  display: inline-block;
  width: 2rem;
  height: 2rem;
}
.lds-dual-ring:after {
  top: 50%;
  content: ' ';
  display: block;
  width: 2rem;
  height: 2rem;
  margin: 1px;
  border-radius: 50%;
  border: 5px solid #fff;
  border-color: #fff transparent #fff transparent;
  animation: lds-dual-ring 1s linear infinite;
}
@keyframes lds-dual-ring {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
</style>
