0<template lang="pug">
    .datepicker
        .datepicker__title
            | {{ monthName }}
        .datepicker__body
            .datepicker__weekheader
                .datepicker__weekdayname(v-for="weekDay in weekDayNames") {{ weekDay }}
            .datepicker__dates.flex.row.justify-between.flex-wrap
                .datepicker__fill-prefix(v-for="prefixFill in numOfPrefixFills")
                t-date(
                    v-for="dateVal in daysInMonth"
                    :key="dateVal"
                    :value="dateVal"
                    @date-selected="chooseDate"
                    :class="{ 'chosen': dateVal === dateChosen }"
                )
</template>

<script lang="ts">
import { defineComponent } from '@vue/composition-api'
import TDate from './TDate.vue'

export default defineComponent({
    name: 'TDatePicker',
    components: { TDate },
    props: {
        // TODO: При изменении месяца сбрасывать dateChosen
        month: {
            type: Number,
            default: 0
        }
    },
    computed: {
        daysInMonth (): number {
            return new Date(2020, this.month + 1, 0).getDate()
        },
        monthName (): string {
            return new Date(2020, this.month).toLocaleString('ru', { month: 'long' })
        },
        weekDayNames () {
            return ['Пн', 'Вт', 'Ср', 'Чт', 'Пт', 'Сб', 'Вс']
        },
        numOfPrefixFills (): number {
            const firstDayWeekName = new Date(2020, this.month, 1).getDay()
            if (!firstDayWeekName) return 6
            else return firstDayWeekName - 1
        }
    },
    data (): { dateChosen: number } {
        return {
            dateChosen: 0
        }
    },
    methods: {
        chooseDate (dateNum: number): void {
            this.dateChosen = dateNum
            this.$emit('date-chosen', new Date(2020, this.month, dateNum).toLocaleDateString('ru'))
        }
    }
})
</script>

<style lang="sass" scoped>
@import 'datepicker.sass'

.datepicker
    cursor: default
    width: $dp-width
    height: $dp-height
    border-radius: $dp-bradius
    box-shadow: 0 0 30px -10px #ccc
    padding: 25px
    .datepicker__title
        color: $dp-weekheader-color
        font-weight: bold
        font-size: $dp-weekheader-font-size
        text-transform: capitalize
        padding-left: 10px
        line-height: $dp-title-height
    .datepicker__body
        .datepicker__weekheader
            line-height: $dp-weekheader-height
            display: flex
            justify-content: center
            color: #aaa
            .datepicker__weekdayname
                display: flex
                flex-basis: $dp-column-width
                justify-content: center
        .datepicker__dates
            height: $dp-dates-body-height
            justify-content: left
            .datepicker__fill-prefix
                display: flex
                flex-basis: $dp-column-width
                line-height: $dp-dates-height
</style>
