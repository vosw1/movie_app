<template>
  <div class="Container">
    <h1 class="info-title">영화 정보</h1>
    <div v-for="(movie) in movies" :key="movie.id" class="item">
      <figure>
        <img :src="movie.imgUrl" :alt="movie.title">
      </figure>
      <div class="info">
        <h3 class="bg-yellow">{{ movie.title }}</h3>
        <p>개봉: {{ movie.year }}</p>
        <p>장르: {{ movie.category }}</p>
        <p>상영시간: {{ movie.time }}</p>
        <p>등급: {{ movie.rating }}</p>
        <button v-on:click="$emit('incrementLike', movie.id)">좋아요</button>
        <span>{{ movie.like }}</span>
        <p>
          <button @click="$emit('openModal', movie.id)">상세보기</button>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MoviesComponent",
  props: {
    movies: Array
  }
}
</script>

<style>
.Container {
  padding: 20px;
  border-radius: 10px;
}

.info-title {
  padding: 10px 0;
}

.item {
  width: 100%;
  border: 1px solid #ccc;
  display: flex;
  margin-bottom: 20px;
  padding: 1rem;
  border-radius: 10px; /* 박스의 모서리를 둥글게 설정 */
}

.item figure {
  width: 30%;
  margin-right: 1rem;
}

.item img {
  width: 100%;
  height: 260px; /* 고정된 높이 */
  object-fit: cover; /* 이미지가 박스에 맞게 조정됨 */
  border-radius: 10px; /* 박스의 모서리를 둥글게 설정 */
}

.item .info {
  width: 70%;
}

.bg-yellow {
  padding: 10px 0;
  font-size: 1.5rem; /* 글자 크기를 키움 */
}
</style>