<template lang="pug">
    .datepicker__date
        .datepicker__datewrapper(@click="$emit('date-selected', value)")
            | {{ value }}
</template>

<script lang="ts">
import { defineComponent } from '@vue/composition-api'

export default defineComponent({
    name: 'TDate',
    props: {
        value: {
            type: Number,
            default: 0
        }
    }
})
</script>

<style lang="sass" scoped>
@import 'datepicker.sass'

.datepicker__date
    display: flex
    flex-basis: $dp-column-width
    justify-content: center
    font-size: $dp-dates-font-size
    color: $dp-dates-color
    height: $dp-dates-height
    &.chosen
        .datepicker__datewrapper
            background: $dp-date-chosen-bgcolor
            color: $dp-date-chosen-color
.datepicker__datewrapper
    display: flex
    justify-content: center
    align-items: center
    width: $dp-dates-height
    border-radius: 50%
    &:hover
        cursor: pointer
        background: #eee
        box-shadow: 0 0 1px 1px #ddd
        transition: all 0.1s ease-in-out
</style>
