<template>
  <div>
    <Navbar />
    <h1>영화 정보</h1>
    <div v-for="(movie, i) in movies" :key="i" class="item">
      <figure>
        <img :src="movie.imgUrl" :alt="movie.title">
      </figure>
      <div class="info">
        <h3 class="bg-yellow">{{ movie.title }}</h3>
        <p>개봉: {{ movie.year }}</p>
        <p>장르: {{ movie.category }}</p>
        <p>상영시간: {{ movie.time }}</p>
        <p>등급: {{ movie.rating }}</p>
        <button v-on:click="incrementLike(i)">좋아요</button>
        <span>{{ movie.like }}</span>
        <p>
          <button @click="selectMovie(i)">상세보기</button>
        </p>
      </div>
    </div>

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

export default {
  name: 'App',
  data() {
    return {
      isModal: false,
      selectedMovie: null,  // 초기화 시 null로 설정
      movies: movies
    }
  },
  methods: {
    incrementLike(i) {
      this.movies[i].like++;
    },
    selectMovie(i) {  // 새로운 메서드 추가
      this.selectedMovie = i;
      this.isModal = true;
    },
  },
  components: {
    Navbar: Navbar,
    Modal: Modal
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