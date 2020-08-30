<template lang="pug">
  q-layout(view='lHh Lpr lFf')
    q-header(elevated)
      q-toolbar Toolbar
    q-page-container
      router-view

</template>

<script lang="ts">
import EssentialLink from 'components/EssentialLink.vue'

import { defineComponent } from '@vue/composition-api'

export default defineComponent({
  name: 'MainLayout',
  components: { EssentialLink }
})
</script>
