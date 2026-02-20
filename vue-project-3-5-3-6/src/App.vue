<template>
  <div class="app">
    <h1>組件綜合練習</h1>
    
    <button @click="showCard = !showCard">
      {{ showCard ? '隱藏名片 (銷毀)' : '顯示名片 (掛載)' }}
    </button>

    <hr>

    <ActivityCard 
      v-if="showCard" 
      userName="張小明" 
      @reset="handleReset"
    >
      <template v-slot:icon>
        <span>🔥</span>
      </template>

      <p>資深前端開發者，熱愛 Vue.js 與 🍵 綠茶。</p>
    </ActivityCard>
    
    <p v-if="message" class="toast">{{ message }}</p>
  </div>
</template>

<script>
import ActivityCard from './components/ActivityCard.vue';

export default {
  components: { ActivityCard },
  data() {
    return {
      showCard: true,
      message: ''
    };
  },
  methods: {
    handleReset() {
      this.message = '計時器已重置！';
      setTimeout(() => this.message = '', 2000);
    }
  }
}
</script>