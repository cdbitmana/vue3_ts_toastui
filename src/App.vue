<template>
  <ToastUIEditor :height="200" />

  <hr>
  <hr>
  <hr>

  <ToastUIEditor :height="200" />
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import ToastUIEditor from './components/TUIEditor.vue'

export default defineComponent({
  name: 'App',
  components: {
    ToastUIEditor
  }
})
</script>

<style>
</style>