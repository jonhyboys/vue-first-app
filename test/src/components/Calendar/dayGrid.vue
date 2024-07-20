<script setup>
    import day from './day.vue'
    import dayWeek from './dayWeek.vue'
    import date from './date.vue'

    const _today = new Date()
    const _todayDate = _today.getDate()
    let dates = []
    setDates()

    function setDates(){
        const firstMonthDay = _todayDate % 7
        const monthFirstDate = (_todayDate + 7 - firstMonthDay) * 86400000
        let firstCalendarDay = new Date(_today)
        const dateMS = _today.valueOf()
        firstCalendarDay.setTime(dateMS - monthFirstDate)
        for(let x=0; x<42; x++){
            dates.push(new Date(firstCalendarDay))            
            firstCalendarDay.setTime(firstCalendarDay.valueOf() + 86400000)
        }
    }

    function handlerClick(e){
        e.stopPropagation()
        const node = e.composedPath().find(n=>n.dataset && 'id' in n.dataset)
        if(node){
            const {id} = node.dataset
            const actualToday = document.querySelector('.today')
            actualToday.classList.remove('today')
            const newToday = document.querySelector('[data-id="' + id + '"]')
            newToday.classList.add('today')
        }
    }
</script>

<template>
    <date :date="_today"></date>
    <div class="calendar-grid" @click="handlerClick($event)">
        <dayWeek></dayWeek>
        <day v-for="(item, index) in dates" :date="item" :index="index"></day>
    </div>
</template>

<style scoped>
    .calendar-grid{
        display: grid;
        grid-template-columns: repeat(7, 40px);
        grid-template-rows: repeat(6, 40px);
    }
</style>