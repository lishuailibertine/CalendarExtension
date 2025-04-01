<template>
  <div class="hello">
    <iframe 
      v-if="isIframeLoaded"
      :src="`https://html5.moji.com/nb/wnlh5/index.html?luicode=10000011&lfid=1076036592942312&u=https%3A%2F%2Fhtml5.moji.com%2Fnb%2Fwnlh5%2Findex.html`"
      width="100%" 
      height="100%"
      frameborder="0"
      @load="onIframeLoad"
    ></iframe>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      iframeSrc: 'https://html5.moji.com/nb/wnlh5/index.html?luicode=10000011&lfid=1076036592942312&u=https%3A%2F%2Fhtml5.moji.com%2Fnb%2Fwnlh5%2Findex.html',
      isIframeLoaded: false // 用于控制 iframe 是否加载完成
    };
  },
  mounted() {
    // 预加载 iframe 内容
    this.preloadIframe();
  },
  methods: {
    preloadIframe() {
      const iframe = document.createElement('iframe');
      iframe.src = this.iframeSrc;
      iframe.style.display = 'none'; // 隐藏 iframe
      iframe.onload = () => {
        this.isIframeLoaded = true; // 设置为已加载
      };
      document.body.appendChild(iframe); // 将 iframe 添加到 DOM
    },
    onIframeLoad() {
      // 处理 iframe 加载完成后的逻辑
      console.log('Iframe loaded');
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello {
  width: 400px; /* 设置固定宽度 */
  height: 400px; /* 设置固定高度，您可以根据需要调整 */
  margin: 0 auto; /* 居中对齐 */
  padding: 0; /* 去掉内边距 */
  overflow: hidden; /* 隐藏溢出内容 */
}
</style>
