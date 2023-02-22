<template>
  <div class="right-container">
    <h3>Right 组件 --- {{ count }}</h3>
    <button @click="add">+1</button>
    <p>{{ msgFromLeft }}</p>
  </div>
</template>

<script>
import bus from '@/components/eventBus.js';
export default {
  data() {
    return {
      //子组件自己的数据，将来希望把count值传给父组件
      count: 0,
      msgFromLeft: ''
    }
  },
  methods: {
    add() {
      //让子组件的count值自增+1
      this.count += 1;
      //把自增的结果传给父组件
      this.$emit('numchange',this.count);
    }
  },
  created() {
    bus.$on('share', val => {
      this.msgFromLeft = val;
    })
  }
}
</script>

<style lang="less">
.right-container {
  padding: 0 20px 20px;
  background-color: lightskyblue;
  min-height: 250px;
  flex: 1;
}
</style>
