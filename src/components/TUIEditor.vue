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
// code syntax highlight 불러오기
import 'highlight.js/styles/github.css';
import codeSyntaxHighlight from '@toast-ui/editor-plugin-code-syntax-highlight';

// 제이쿼리 불러오기
import $ from 'jquery';

export default defineComponent({
  name: 'TUIEditor',
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
// 유튜브 플러그인 시작
function youtubePlugin() {
  toastui.Editor.codeBlockManager.setReplacer('youtube', youtubeId => {
    // Indentify multiple code blocks
    const wrapperId = `yt${Math.random().toString(36).substr(2, 10)}`;

    // Avoid sanitizing iframe tag
    setTimeout(renderYoutube.bind(null, wrapperId, youtubeId), 0);

    return `<div id="${wrapperId}"></div>`;
  });
}

function renderYoutube(wrapperId:any, youtubeId:any) {
  const el = document.querySelector(`#${wrapperId}`);
  if( !!!el ){
    return;
  }
  el.innerHTML = `<div class="toast-ui-youtube-plugin-wrap"><iframe src="https://www.youtube.com/embed/${youtubeId}" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></div>`;
}
// 유튜브 플러그인 끝

// codepen 플러그인 시작
function codepenPlugin() {
  toastui.Editor.codeBlockManager.setReplacer('codepen', url => {
    const wrapperId = `yt${Math.random().toString(36).substr(2, 10)}`;

    // Avoid sanitizing iframe tag
    setTimeout(renderCodepen.bind(null, wrapperId, url), 0);

    return `<div id="${wrapperId}"></div>`;
  });
}

function renderCodepen(wrapperId:any, url:any) {
  const el = document.querySelector(`#${wrapperId}`);
  
  var urlParams = new URLSearchParams(url.split('?')[1]);
  var height = urlParams.get('height');
  if ( !!!el ){
    return;
  }
  el.innerHTML = `<div class="toast-ui-codepen-plugin-wrap"><iframe height="${height}" scrolling="no" src="${url}" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true"></iframe></div>`;
}
// codepen 플러그인 끝

      const editor = new Editor({
        el: groundElRef.value,
        previewStyle: 'vertical',
        initialValue: "# 안녕",
        height: props.height + "px",
        plugins: [codeSyntaxHighlight]
      });
    });
    
    return {
      groundElRef
    }
  },
  methods:{
    alert(){
      alert(this.groundElRef);
    }
  }
})
</script>

<style scoped>
</style>
