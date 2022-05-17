<template>
  <div class="input-group mb-3 msg_append">
    <span class="input-group-text" id="basic-addon1">任务</span>
    <input type="text" class="form-control" placeholder="请输入任务信息" aria-label="Username"
           aria-describedby="basic-addon1" v-model="taskname">
    <div class="d-grid gap-2 d-md-block">
      <button class="btn btn-primary" type="button" @click="task_transmit">添加新任务</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "AppendInput",
  emits: ['append'],
  data() {
    return {
      taskname: ''
    }
  },
  methods: {
    task_transmit() {
      if (this.taskname === '') return alert('任务名称不能为空!');
      this.$emit('append', this.taskname);
      this.taskname = '';
      console.log(this.taskname)
    }
  }
}
</script>

<style lang="less" scoped>
.msg_append {
  width: 450px;

  button {
    margin-left: 10px;
  }
}
</style>