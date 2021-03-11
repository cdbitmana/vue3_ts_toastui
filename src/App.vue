<template>
  <TUIEditor :height="200" ref="aa"/>

  <hr>
  <hr>
  <hr>

  <TUIEditor :height="200" ref="aa" />
</template>

<script lang="ts">
import { defineComponent, onMounted, ref } from 'vue'
import TUIEditor from './components/TUIEditor.vue'

export default defineComponent({
  name: 'App',
  components: {
    TUIEditor
  },
  setup:() => {
    const aa = ref();
    onMounted(() => {
       
      aa.value.alert();
      
    })
   return {
     aa
   }
  }
})
</script>

<style>
</style>