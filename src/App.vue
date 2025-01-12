<template>
  <Navbar />
  <Event :text="text"/>
  <Searchbar :data="data_temp" @searchMovie="searchMovie($event)"/>
  <p>
    <button @click="showAllMovie">전체보기</button>
  </p>
  <Movie
    :data="data_temp"
    @opemModal="isModal=true;selectedMovie=$event"
    @increaseLike="increaseLike($event)"/>

  <Modal
    :data="data"
    :isModal="isModal"
    :selectedMovie="selectedMovie"
    />
</template>

<script>
import data from './assets/movies.js';
import Navbar from './components/Navbar.vue';
import Modal from './components/Modal.vue';
import Event from './components/Event.vue';
import Movie from './components/Movie.vue';
import Searchbar from './components/Searchbar.vue';
export default {
  name: "App",
  data() {
    return {
      isModal: false,
      data: data, //원본
      data_temp: [...data], //사본
      selectedMovie: 0,
      text: "NEPLIX 강렬한 운명의 드라마, 경기크리쳐",
    };
  },
  methods: {
    increaseLike(i) {
      this.data.find(movie => {
        if(movie.id === i) {
          movie.like++;
        }
      });
    },
    searchMovie(title){
      this.data_temp = this.data.filter((movie) => {
        return movie.title.includes(title);
      });
    },
    showAllMovie(){
      this.data_temp = [...this.data];
    }
  },
  components:{
    Navbar: Navbar,
    Event: Event,
    Modal: Modal,
    Movie: Movie,
    Searchbar: Searchbar,
  }
};
</script>

<style>
*{
  box-sizing: border-box;
  margin: 0;
}

body {
  max-width: 768px;
  margin: 0 auto;
  padding: 20px;
}

h1, h2, h3 {
  margin-bottom: 1rem;
}

p{
  margin-bottom: 0.5rem;
}

button {
  margin-right: 10px;
  margin-bottom: 1rem;
}

.item {
  width: 100%;
  border: 1px solid #ccc;
  display: flex;
  margin-bottom: 20px;
  padding: 1rem;
}

.item figure {
  width: 30%;
  margin-right: 1rem;
}

.item img {
  width: 100%;
}

.item .info {
  width: 100%;
}

.modal {
  display: flex;
  justify-content: center;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  background: rgba(0, 0, 0, 0.7);
  align-items: center;
}

.modal .inner{
  background: #fff;
  width: 80%;
  padding: 20px;
  border-radius: 10px;
}
</style>
