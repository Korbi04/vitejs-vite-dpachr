<script setup lang="ts">
import { ref } from 'vue'
import { useResizeObserver } from '@vueuse/core'

const el = ref(null)
const text = ref('')

useResizeObserver(el, (entries) => {
  const [entry] = entries
  const { width, height } = entry.contentRect
  text.value = `width: ${width}\nheight: ${height}`
})
</script>

<template>
  <note class="mb-2">
    Resize the box to see changes
  </note>
  <BR /><BR />
  <textarea ref="el" class="resizer" disabled v-text="text" />
</template>