<template >
    <div v-if="isModal" class="modal">
      <div class="inner">
        <button class="close-btn" @click="$emit(`closeModal`)">X</button>
        <h3>영화 '{{ movies[selectedMovie].title }}'</h3>
        <p>{{ movies[selectedMovie].detail }}</p>
      </div>
    </div>
</template>
<script>
export default {
    name: 'ModalComponent',
    // APP에 있는 변수를 컴포넌트에 전달
    props: { // 변수명 : 데이터 타입
        movies: Array,
        isModal: Boolean,
        selectedMovie: Number // 데이터 변경은 부모만 가능
    }
}
</script>

<style>

</style>