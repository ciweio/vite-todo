<template>
  <div class="btn-group mt-3 task_filter" role="group" aria-label="Basic example">
    <button type="button" class="btn" :class="active === 0 ? 'btn-primary' : 'btn-secondary'" @click="filter_switch(0)">
      全部
    </button>
    <button type="button" class="btn" :class="active === 1 ? 'btn-primary' : 'btn-secondary'" @click="filter_switch(1)">
      已完成
    </button>
    <button type="button" class="btn" :class="active === 2 ? 'btn-primary' : 'btn-secondary'" @click="filter_switch(2)">
      未完成
    </button>
  </div>
</template>

<script>
export default {
  name: "FilterButton",
  emits: ['update:active'],
  props: {
    active: {
      type: Number,
      required: true,
      default: 0  //status: 0-all,1-completed,2-incomplete
    }
  },
  methods: {
    filter_switch(filter_active) {
      this.$emit('update:active', filter_active);
    }
  }
}
</script>

<style lang="less" scoped>
.task_filter {
  width: 240px;
  text-align: center;
  margin-left: 60px;
}
</style>