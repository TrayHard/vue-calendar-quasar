<template lang="pug">
    .datepicker
        .datepicker__title
            | {{ monthName }}
        .datepicker__body
            .datepicker__weekheader
                .datepicker__weekdayname(v-for="weekDay in weekDayNames") {{ weekDay }}
            .datepicker__dates.flex.row.justify-between.flex-wrap
                .datepicker__fill-prefix(v-for="prefixFill in numOfPrefixFills")
                t-date(v-for="dateVal in daysInMonth" :key="dateVal") {{dateVal}}
</template>

<script lang="ts">
import { defineComponent } from '@vue/composition-api'
import TDate from './TDate.vue';

export default defineComponent({
    name: 'TDatePicker',
    components: { TDate },
    computed: {
        daysInMonth() {
            //@ts-ignore
            return new Date(2020, this.month, 0).getDate();
        },
        monthName() {
            return new Date().toLocaleString('ru', { month: 'long' });
        },
        weekDayNames() {
            return ['Пн', 'Вт', 'Ср', 'Чт', 'Пт', 'Сб', 'Вс']
        },
        numOfPrefixFills() {
            let firstDayWeekName = new Date(2020, this.month, 1).getDay();
            if (!firstDayWeekName) return 6
            else return firstDayWeekName - 1;
        }
    },
    data(): {
        month: number
    } {
        return {
            month: 7
        }
    },
})
</script>

<style lang="sass" scoped>
.datepicker
    width: 400px
    height: 280px
    border-radius: 3px
    box-shadow: 0 0 30px -10px #ccc
    padding: 25px
    .datepicker__title
        color: #777
        font-weight: bold
        font-size: 16px
        text-transform: capitalize
        padding-left: 10px
        margin-bottom: 10px
    .datepicker__body
        .datepicker__weekheader
            display: flex
            justify-content: center
            margin-bottom: 10px
            color: #aaa
            .datepicker__weekdayname
                display: flex
                flex-basis: 50px
                justify-content: center
        .datepicker__dates
            justify-content: left
            .datepicker__fill-prefix
                display: flex
                flex-basis: 50px
</style>