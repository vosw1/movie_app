<template>
  <div>
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
          <button @click="showModal(i)">상세보기</button>
        </p>
      </div>
      
      <div v-if="currentMovieIndex === i" class="modal">
        <div class="inner">
          <h3>영화 "{{ movie.title }}"</h3>
          <p>{{ movie.detail }}</p>
          <button class="close-btn" @click="showModal(null)">X</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import img1 from '@/assets/1.webp';
import img2 from '@/assets/2.jpg';
import img3 from '@/assets/3.jpg';
import img4 from '@/assets/4.jpg';

export default {
  name: 'App',
  data() {
    return {
      movies: [
        {
          title: "에이리언: 로물루스",
          year: "2024년 8월 16일",
          category: "SF, 호러, 액션, 스릴러, 크리처",
          time: "119분 (1시간 58분 51초)",
          rating: "15세 이상 관람가",
          detail: "에이리언: 로물루스는 인류가 외계 생명체와의 전투를 벌이는 이야기를 담고 있습니다. 먼 미래의 우주에서, 지구와는 전혀 다른 환경을 가진 로물루스 행성에서 외계 생명체의 침공이 시작됩니다. 주인공은 생존을 위해 고군분투하며, 외계 생명체의 정체와 그들의 목적을 파헤쳐야 합니다. 이 영화는 숨 막히는 액션과 함께 호러와 스릴러 요소가 가미된 복합 장르의 작품입니다.",
          imgUrl: img1,
          like: 0
        },
        {
          title: "트위스터스",
          year: "2024년 8월 14일",
          category: "재난, 액션, 모험, 드라마",
          time: "122분 (2시간 2분 13초)",
          rating: "12세 이상 관람가",
          detail: "트위스터스는 미국 중서부를 휩쓸고 지나가는 초강력 회오리바람을 중심으로 한 이야기입니다. 강력한 자연 재해와 싸우는 주인공들은 가족과 지역 사회를 구하기 위해 헌신합니다. 이 과정에서 그들은 각자의 개인적인 문제와 갈등을 해결하며, 인간의 힘과 의지가 자연의 위협에 맞서 싸우는 모습을 그립니다. 감동적인 드라마와 긴장감 넘치는 액션이 혼합된 작품입니다.",
          imgUrl: img2,
          like: 0
        },
        {
          title: "스픽 노 이블",
          year: "2024년 9월 11일",
          category: "공포/드라마",
          time: "98분(1시간 38분 26초)",
          rating: "15세 이상 관람가",
          detail: "스픽 노 이블은 주인공이 상실감과 내면의 공포를 극복해 나가는 심리 스릴러입니다. 주인공은 어릴 적 가족을 잃은 후, 혼자서 폐허가 된 집에서 살아가고 있습니다. 하지만 그 집에서 이상한 현상들이 일어나기 시작하며, 주인공은 자신이 과거에 마주했던 두려움과 싸워야 합니다. 이 영화는 공포와 드라마를 결합하여 관객에게 강렬한 심리적 인상을 남깁니다.",
          imgUrl: img3,
          like: 0 
        },
        {
          title: "안녕, 할부지",
          year: "2024년 9월 4일",
          category: "다큐멘터리, 애니메이션",
          time: "94분 (1시간 34분 32초)",
          rating: "전체 관람가",
          detail: "안녕, 할부지는 할아버지와의 특별한 시간을 다룬 애니메이션 다큐멘터리입니다. 이 영화는 가족과의 소중한 순간을 담아내며, 특히 할아버지와 손자의 관계를 중심으로 이야기를 전개합니다. 할아버지의 삶의 지혜와 따뜻한 마음을 통해 가족의 중요성과 사랑을 일깨우는 내용입니다. 애니메이션을 통해 감동적이고 아름다운 시각적 경험을 제공합니다.",
          imgUrl: img4,
          like: 0 
        },
      ],
      currentMovieIndex: null
    }
  },
  methods: {
    incrementLike(i) {
      this.movies[i].like++;
    },
    showModal(index) {
      this.currentMovieIndex = index;
    }
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
  height: 250px; /* 고정된 높이 */
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
}

</style>