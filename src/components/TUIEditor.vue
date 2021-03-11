<template>
  <div ref="groundElRef"></div>
</template>

<script lang="ts">
import { ref, defineComponent, onMounted } from 'vue'
// toastUi 불러오기
import Editor from '@toast-ui/editor';
import 'codemirror/lib/codemirror.css'; // Editor's Dependency Style
import '@toast-ui/editor/dist/toastui-editor.css'; // Editor's Style
import Viewer from '@toast-ui/editor/dist/toastui-editor-viewer';
import '@toast-ui/editor/dist/toastui-editor-viewer.css';

// 제이쿼리 불러오기
import $ from 'jquery';

export default defineComponent({
  name: 'ToastUIEditor',
  props: {
    height: {
      type: Number,
      default:500
    }
  },
  setup: (props) => {
    const groundElRef = ref<HTMLInputElement>();

    onMounted(() => {
      if ( !!!groundElRef.value ) {
        return;
      }

      const editor = new Editor({
        el: groundElRef.value,
        previewStyle: undefined,
        initialValue: "# 안녕",
        height: props.height + "px"
      });
    });

    return {
      groundElRef
    }
  }
})
</script>

<style scoped>
</style>
