<template>
  <div>
    <h1>刺猬 To Do</h1>
    <div class="spliter"/>
    <append-input class="mt-3" @append="task_append"/>
    <todo-list :list="list_task_filter"/>
    <filter-button v-model:active="filter_active"/>
  </div>
</template>

<script>
import AppendInput from "./components/AppendInput.vue";
import TodoList from "./components/TodoList.vue";
import FilterButton from "./components/FilterButton.vue";

export default {
  name: 'App',
  components: {
    AppendInput,
    TodoList,
    FilterButton
  },
  data() {
    return {
      id_next: 4,
      filter_active: 0,
      list_task: [
        {
          id: 1,
          task: '周一早晨9点开会',
          completed: false
        },
        {
          id: 2,
          task: '周一晚上8点聚餐',
          completed: false
        },
        {
          id: 3,
          task: '准备周三上午的演讲稿',
          completed: true
        },
      ]
    };
  },
  computed: {
    list_task_filter() {
      switch (this.filter_active) {
        case 0:
          return this.list_task;
        case 1:
          return this.list_task.filter(x => x.completed === true);
        case 2:
          return this.list_task.filter(x => x.completed === false);
      }
    }
  },
  methods: {
    task_append(taskname) {
      this.list_task.push(
          {
            id: this.id_next,
            task: taskname,
            completed: false
          },
      );
      this.id_next++;
    }
  }
}
</script>

<style lang="less" scoped>
.spliter {
  height: 1px;
  width: 500px;
  background-color: #f5f5f5;
}
</style>