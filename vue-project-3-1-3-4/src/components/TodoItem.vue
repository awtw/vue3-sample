<template>
  <div class="todo-item" :class="{ completed: isDone }">
    <span>{{ taskTitle }}</span>
    <div class="actions">
      <button @click="onToggle">{{ isDone ? '取消' : '完成' }}</button>
      <button @click="onDelete" class="delete-btn">刪除</button>
    </div>
  </div>
</template>

<script>
export default {
  // 3.3 重點：定義 Props
  props: {
    taskTitle: {
      type: String,
      required: true
    },
    isDone: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    // 3.4 重點：使用 $emit 向上發送事件
    onToggle() {
      this.$emit('toggle-status');
    },
    onDelete() {
      this.$emit('delete-task');
    }
  }
}
</script>

<style scoped>
.todo-item { display: flex; justify-content: space-between; padding: 10px; border-bottom: 1px solid #eee; }
.completed span { text-decoration: line-through; color: gray; }
.delete-btn { color: red; }
</style>