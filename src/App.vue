<template>
  <div id="app">
    <div class="omdb">
      <h2 class="omdb__title" v-html="title"></h2>
      <OMDbCard
        class="omdb__card"
        v-for="(film, index) in films"
        v-show="index == currentIndex"
        :key="index"
        :id="film"
      />
      <div v-if="films.length > 1" class="omdb__indicators">
        <span
          v-for="(film, index) in films"
          :key="index"
          class="omdb__indicator"
          :class="{ 'omdb__indicator--active': index == currentIndex }"
          @click="changeIndex(index)"
        ></span>
      </div>
    </div>
  </div>
</template>

<script>
import OMDbCard from './components/OMDbCard.vue';

export default {
  components: {
    OMDbCard,
  },
  data() {
    return {
      title: '&#9733; My Favorite Films',
      films: ['tt2905772', 'tt9418878', 'tt5334076', 'tt4373956', 'tt1827487'],
      currentIndex: 0,
    };
  },
  methods: {
    changeIndex(index) {
      this.currentIndex = index;
    },
  },
};
</script>

<style>
body {
  background-image: radial-gradient(
    circle,
    #660e1e,
    #4e0f1c,
    #360f18,
    #200b10,
    #000000
  );
}
* {
  margin: 0px;
  padding: 0px;
  font-family: 'Gill Sans', sans-serif;
}
.omdb {
  display: flex;
  min-height: 100vh;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.omdb__card {
  display: flex;
  flex-direction: column;
  justify-content: center;
  min-height: 510px;
  margin-top: 20px;
}
.omdb__title {
  color: #ffffff;
  margin: 5px 0px;
  text-align: center;
}
.omdb__indicators {
  margin-top: 10px;
}
.omdb__indicator {
  display: inline-block;
  width: 0.75rem;
  height: 0.75rem;
  background-color: #ffffff;
  border: 1px solid #efefef;
  border-radius: 50%;
  margin: 0px 5px;
  cursor: pointer;
  transition: all 0.4s;
}
.omdb__indicator--active {
  background-color: #660e1e;
}
</style>
