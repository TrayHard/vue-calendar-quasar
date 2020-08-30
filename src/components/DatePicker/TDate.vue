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
.datepicker__date
    display: flex
    flex-basis: 50px
    justify-content: center
    font-size: 15px
    color: #888
    line-height: 30px
</style>