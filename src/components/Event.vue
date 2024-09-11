<template>
    <div class="event" :class="{show : isOpen}"> <!--기본 값-->
        <p>{{ text }}</p>
        <button @click="isOpen=false">X</button>
        
    </div>
</template>
<script>
export default {
    name: "EventComponent",
    props: {
        text: String,
        isEventOpen: Boolean
    },
    data() {
        return{
            isOpen: true
        }
    }
}
</script>
<style>
.event {
    background: #444;
    color: #fff;
    padding: 10px 20px;
    text-align: center;
    font-size: small;
    display: flex;
    justify-content: space-between; 
    align-items: center; 
    display: none;/* 보이지 않게 기본 값을 설정 */
}

.show {
    display: flex;
}

.event p {
    margin: 0;
}

.event button {
    margin: 0;
}
</style>