<template lang="pug">
    .datepicker__date
        slot
</template>

<script lang="ts">
import { defineComponent } from '@vue/composition-api'

export default defineComponent({
    name: 'TDate'
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
    line-height: $dp-dates-height
</style>
