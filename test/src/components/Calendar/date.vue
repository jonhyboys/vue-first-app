<script setup>
    defineProps({
        date: Date
    })
</script>

<template>
    <div>{{ date.toDateString() }}</div>
</template>