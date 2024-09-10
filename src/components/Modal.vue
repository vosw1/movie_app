<template >
    <div v-if="isModal" class="modal">
      <div class="inner">
        <button class="close-btn" @click="isModal=false">X</button>
        <h3>영화 '{{ selectedMovie.title }}'</h3>
        <p>{{ selectedMovie.detail }}</p>
      </div>
    </div>
</template>
<script>
export default {
    name: 'ModalComponent',
}
</script>

<style>
    
</style>