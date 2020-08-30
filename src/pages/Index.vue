<template lang="pug">
    q-page.column.items-center.justify-center
        q-select.q-mb-lg.month-selector(outlined v-model="monthSelected" :options="monthOptions")
        t-datepicker(:month="monthSelected.value")
</template>

<script lang="ts">
import { Month } from 'components/models'
import ExampleComponent from 'components/CompositionComponent.vue'
import TDatepicker from 'components/DatePicker/TDatepicker.vue'
import { defineComponent } from '@vue/composition-api'

export default defineComponent({
    name: 'PageIndex',
    components: { ExampleComponent, TDatepicker },
    computed: {
        monthOptions (): Array<unknown> {
            return this.$data.months.map((el: Month) => ({ value: el.code, label: el.name }))
        }
    },
    data () {
        const months: Month[] = [
            { name: 'Январь', code: 0 },
            { name: 'Февраль', code: 1 },
            { name: 'Март', code: 2 },
            { name: 'Апрель', code: 3 },
            { name: 'Май', code: 4 },
            { name: 'Июнь', code: 5 },
            { name: 'Июль', code: 6 },
            { name: 'Август', code: 7 },
            { name: 'Сентябрь', code: 8 },
            { name: 'Октябрь', code: 9 },
            { name: 'Ноябрь', code: 10 },
            { name: 'Декабрь', code: 11 }
        ]
        return {
            months,
            monthSelected: { label: 'Январь', value: 0 }
        }
    }
})
</script>

<style lang="sass" scoped>
.month-selector
    min-width: 250px
</style>
