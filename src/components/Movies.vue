<template>
    <div class="Container">
      <h1 class="info-title">영화 정보</h1>
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
        <button v-on:click="$emit('incrementLike', i)">좋아요</button>
        <span>{{ movie.like }}</span>
        <p>
          <button @click="$emit('openModal', i)">상세보기</button>
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
.container {
  padding: 20px;
}

.info-title {
  padding-top: 20px;
}
</style>