<template>
  <h1>영화 정보</h1>
  <div v-for="(movie, i) in movies" :key="i">
    <h3 class="bg-yellow" :style="{ color: movie.titleColor }">{{ movie.title }}</h3>
    <p>개봉: {{ movie.year }}</p>
    <p>장르: {{ movie.category }}</p>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      movies: [
        {
          title: "에이리언: 로물루스",
          year: "2024년 8월 16일",
          category: "SF, 호러, 액션, 스릴러, 크리처",
          titleColor: "red"
        },
        {
          title: "트위스터스",
          year: "2024년 8월 14일",
          category: "재난, 액션, 모험, 드라마",
          titleColor: "brown"
        },
        {
          title: "스픽 노 이블",
          year: "2024년 9월 11일",
          category: "공포/드라마",
          titleColor: "grey"
        },
        {
          title: "안녕, 할부지",
          year: "2024년 9월 4일",
          category: "다큐멘터리, 애니메이션",
          titleColor: "green"
        },
      ]
    }
  }
}
</script>

<style>
.bg-yellow {
  background: yellow;
  padding: 10px;
}
</style>