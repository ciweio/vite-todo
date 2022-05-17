<template>
  <ul class="list-group">
    <li class="list-group-item d-flex justify-content-between align-items-center" v-for="(item) in list" :key="item.id">
      <div class="form-check">
        <input class="form-check-input" type="checkbox" value="" :id="item.id" v-model="item.completed">
        <label class="form-check-label" :for="item.id" :class="item.completed ? 'task_completed' : ''">
          {{ item.task }}
        </label>
      </div>
      <span class="badge bg-success rounded-pill" v-if="item.completed">已完成</span>
      <span class="badge bg-danger rounded-pill" v-else>未完成</span>
    </li>
  </ul>
</template>

<script>
export default {
  name: "TodoList",
  props: {
    list: {
      type: Array,
      required: true,
      default: []
    }
  }
}
</script>

<style lang="less" scoped>
.list-group {
  width: 360px;

  .task_completed {
    color: darkgray;
    text-decoration: line-through;
    font-style: italic;
  }
}
</style>