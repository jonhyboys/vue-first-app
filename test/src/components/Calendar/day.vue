<script setup>
    import { ref } from 'vue'
    //const _day = ref(0)
    defineProps({
        date: Date,
        index: Number
    })

    const _today = new Date().getDate()

</script>

<template>
    <div class="day" :class="{today: _today === date.getDate()}" v-bind:data-id="index">{{date.getDate()}}</div>
</template>

<style scoped>
    .day{
        cursor: pointer;
    }
    .today{
        background-color: black;
        color: white;
    }
</style>