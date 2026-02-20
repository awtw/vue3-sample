<template>
  <div class="app">
    <h1>我的任務清單</h1>
    <TodoItem 
      v-for="(item, index) in todoList" 
      :key="index"
      :taskTitle="item.title"
      :isDone="item.done"
      @toggle-status="handleToggle(index)"
      @delete-task="handleDelete(index)"
    />
  </div>
</template>

<script>
import TodoItem from './components/TodoItem.vue';

export default {
  components: { TodoItem },
  data() {
    return {
      todoList: [
        { title: '學習 Vue 組件通信', done: false },
        { title: '練習 Props 驗證', done: true },
        { title: '撰寫 $emit 講稿', done: false }
      ]
    };
  },
  methods: {
    handleToggle(index) {
      this.todoList[index].done = !this.todoList[index].done;
      console.log(`任務 ${index} 狀態已更新`);
    },
    handleDelete(index) {
      this.todoList.splice(index, 1);
      alert('任務已刪除！');
    }
  }
}
</script>