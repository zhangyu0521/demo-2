<template>
  <div class="app-container">
    <h1>App 根组件 --- {{ countFromSon }}</h1>
    <hr />
    <div class="box">
      <!-- 渲染 Left 组件和 Right 组件 -->
      <Left :msg="message" :user="userinfo"></Left>
    <Right @numchange="getNewCount"></Right>
    </div>
  </div>
</template>

<script>
import Left from '@/components/Left.vue';
import Right from '@/components/Right.vue';
export default {
  data() {
    return {
      message: '父组件',
      userinfo: { name: 'zzz',age: 18 },
      //定义
      countFromSon: 0
    }
  },
  components: {
    Left,
    Right
  },
  methods: {
    //获取子组件传递过来的数据
    getNewCount(val) {
      this.countFromSon = val;
    }
  }
}
</script>

<style lang="less">
.app-container {
  padding: 1px 20px 20px;
  background-color: #efefef;
}
.box {
  display: flex;
}
</style>
