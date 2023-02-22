<template>
  <div class="left-container">
    <h3>Left 组件</h3>
    <p>父组件传递过来的msg值是:{{ msg }}</p>
    <p>父组件传递过来的user值是:{{ user }}</p>
    <button @click="send">把诗发给right</button>
  </div>
</template>

<script>
import bus from '@/components/eventBus.js';
export default {
  props: ['msg', 'user'],
  data() {
    return {
      str: `黑云压城城欲摧，甲光向日金鳞开。`
    }
  },
  methods: {
    send() {
      bus.$emit('share',this.str);
    }
  }
}
</script>

<style lang="less">
.left-container {
  padding: 0 20px 20px;
  background-color: orange;
  min-height: 250px;
  flex: 1;
}
</style>
