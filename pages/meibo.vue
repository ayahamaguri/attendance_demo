<template>
  <div>
    <v-data-table :headers="headers" :items="students"></v-data-table>
  </div>
</template>
<script lang="ts">
import { defineComponent, ref } from '@nuxtjs/composition-api'

export default defineComponent({
  setup() {
    const headers = ref(['メールアドレス', '名前', '時間'])
    return {
      headers,
    }
  },
})
</script>
