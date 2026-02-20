A<template>
  <div class="card">
    <div class="avatar-header">
      <slot name="icon">👤</slot> 
      <h3>{{ userName }}</h3>
    </div>

    <div class="content">
      <slot>這人很懶，什麼都沒留下。</slot>
    </div>

    <div class="footer">
      <p>您已閱讀此名片：<strong>{{ seconds }}</strong> 秒</p>
      <button @click="resetTime">重置計時</button>
    </div>
  </div>
</template>

<script>
export default {
  props: ['userName'],
  data() {
    return {
      seconds: 0,
      timer: null
    };
  },
  methods: {
    resetTime() {
      this.seconds = 0;
      this.$emit('reset'); // 3.4 回報重置事件
    }
  },
  // 3.5 生命週期：組件出生時開始計時
  mounted() {
    console.log(`${this.userName} 的名片已掛載`);
    this.timer = setInterval(() => {
      this.seconds++;
    }, 1000);
  },
  // 3.5 生命週期：組件消失時務必清除計時器
  unmounted() {
    console.log(`${this.userName} 的名片已銷毀，清除計時器`);
    clearInterval(this.timer);
  }
}
</script>

<style scoped>
.card { border: 2px solid #3eaf7c; border-radius: 12px; padding: 20px; width: 250px; background: white; }
.avatar-header { display: flex; align-items: center; gap: 10px; border-bottom: 1px solid #eee; }
.footer { margin-top: 15px; font-size: 0.8em; color: #666; }
</style>