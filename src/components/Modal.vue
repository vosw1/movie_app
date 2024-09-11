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
    props: { 
        movies: Array,
        isModal: Boolean,
        selectedMovie: Number
    }
}
</script>

<style>

</style>