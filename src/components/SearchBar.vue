<template>
<div>
    <div class="search-box">
        <input 
          type="search" 
          @change="$emit('searchMovie', $event.target.value) // 데이터 전달
          inputText = $event.target.value; 
          $event.target.value = ''" 
          placeholder="검색어를 입력해주세요">
        <button>🔍</button>
    </div>
</div>
</template>

<script>
export default {
    name: "SearchBarComponent",
    data() {
        return {
            inputText: '',
        }
    },
    props: {
        movies: Array,
    },
    watch: {
        inputText(name) {
            // 입력한 영화 제목이 데이터에 있는지 확인하기
            const findName = this.movies.filter(movie => {
                return movie.title.includes(name); 
            })
            if(findName.length == 0) {
                alert('해당하는 영화가 없습니다');
            }
        }
    }
}
</script>

<style>
.search-box {
    padding: 20px;
    display: flex;
    justify-content: center;
}

.search-box input {
    padding: 5px 10px;
}

.search-box button {
    margin: 0;
}
</style>