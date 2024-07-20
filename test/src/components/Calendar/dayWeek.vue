<script setup>
    const weekDays = ['L', 'M', 'X', 'J', 'V', 'S', 'D']
</script>

<template>
    <div v-for="day in weekDays">{{ day }}</div>
</template>