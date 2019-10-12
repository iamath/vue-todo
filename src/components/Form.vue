<template>
  <div class="form">
    <div class="form-row justify-content-center">
      <div class="col-10">
        <input
          type="text"
          placeholder="Type your task here"
          class="form-control form-control-lg"
          v-model="todo"
        >
      </div>
      <div class="col-auto">
        <button type="submit" class="btn btn-light btn-lg" @click="addTodo">
          <i class="fa fa-plus"></i>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      todo: ''
    }
  },
  methods: {
    addTodo() {
      this.$emit('submited', this.todo)
      this.todo = ''
    }
  }
}
</script>
