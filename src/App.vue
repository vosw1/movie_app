<template>
  <div>
    <Navbar />

    <Event :text="text" />

    <Movies 
    :movies="movies" 
    @openModal="isModal=true;
    selectedMovie=$even"
    @incrementLike="incrementLike($event)" />

    <!-- 자식에게 변수 값 전달하기 -->
    <Modal 
    :movies="movies" 
    :isModal="isModal" 
    :selectedMovie="selectedMovie"
    @closeModal="isModal=false" />
   
  </div>
</template>

<script>
import movies from './assets/movies';
import Navbar from './components/Navbar.vue';
import Modal from './components/Modal.vue';
import Movies from './components/Movies.vue';
import Event from './components/Event.vue';

export default {
  name: 'App',
  data() {
    return {
      isModal: false,
      selectedMovie: null, 
      movies: movies,
      text: "Neplix 강렬한 운명의 드라마, 경기크리처"
    }
  },
  methods: {
    incrementLike(i) {
      this.movies[i].like++;
    },
    selectMovie(i) {
      this.selectedMovie = i;
      this.isModal = true;
    },
  },
  components: {
    Navbar: Navbar,
    Modal: Modal,
    Movies: Movies,
    Event: Event
  }  
}
</script>

<style>
* {
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

p {
  margin-bottom: 0.5rem;
}

button {
  margin-right: 10px;
  margin-top: 10px;
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
  height: 260px; /* 고정된 높이 */
  object-fit: cover; /* 이미지가 박스에 맞게 조정됨 */
}

.item .info {
  width: 70%;
}

.bg-yellow {
  padding: 10px 0;
  font-size: 1.5rem; /* 글자 크기를 키움 */
}

.modal {
  background: rgba(0, 0, 0, 0.3);
  position: fixed;
  left: 0;
  top: 0;
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal .inner {
  background: #fff;
  max-width: 500px; /* 모달 창의 최대 너비 */
  width: 90%; /* 기본 너비 */
  padding: 20px;
  border-radius: 10px;
  position: relative; /* 버튼을 상대적으로 위치시키기 위한 설정 */
}

.modal .inner .close-btn {
  position: absolute;
  top: 10px;
  right: 10px;
  background: white;
  border: none;
  font-size: 20px;
  cursor: pointer;
}
</style>