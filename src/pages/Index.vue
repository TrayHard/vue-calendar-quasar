<template lang="pug">
  q-page.flex.items-center.justify-center
    t-datepicker
</template>

<script lang="ts">
import { Todo, Meta } from 'components/models'
import ExampleComponent from 'components/CompositionComponent.vue'
import TDatepicker from 'components/DatePicker/TDatepicker.vue'
import { defineComponent } from '@vue/composition-api'

export default defineComponent({
  name: 'PageIndex',
  components: { ExampleComponent, TDatepicker },
  data () {
    const todos: Todo[] = [
      {
        id: 1,
        content: 'ct1'
      },
      {
        id: 2,
        content: 'ct2'
      },
      {
        id: 3,
        content: 'ct3'
      },
      {
        id: 4,
        content: 'ct4'
      },
      {
        id: 5,
        content: 'ct5'
      }
    ]
    const meta: Meta = {
      totalCount: 1200
    }
    return { todos, meta }
  }
})
</script>
