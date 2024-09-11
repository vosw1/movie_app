<template>
  <div v-if="isModal" class="modal">
    <div class="inner">
      <button class="close-btn" @click="$emit('closeModal')">X</button>
      <h3 v-if="selectedMovie !== null && movies[selectedMovie]">
        영화 '{{ movies[selectedMovie].title }}'
      </h3>
      <p v-if="selectedMovie !== null && movies[selectedMovie]">
        {{ movies[selectedMovie].detail }}
      </p>
      <p v-else>
        선택된 영화 정보가 없습니다.
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ModalComponent',
  props: { 
    movies: {
      type: Array,
      required: true
    },
    isModal: {
      type: Boolean,
      required: true
    },
    selectedMovie: {
      type: Number,
      default: null
    }
  }
}
</script>

<style>

</style>