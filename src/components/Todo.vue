<template>
  <li :class="{ completed: task.completed }" class="list-group-item todo">
    <div class="row">
      <div class="col-auto">
        <h5>
          <i class="fa fa-check" v-if="task.completed"></i>
          {{ task.name }}
        </h5>
      </div>
      <div class="col-auto ml-auto">
          <button
            class="btn btn-outline-success btn-sm mr-1"
            @click="completeTodo"
            v-if="!task.completed"
          >
            <i class="fa fa-check"></i>
          </button>
          <button
            class="btn btn-outline-warning btn-sm mr-1"
            v-if="!task.completed"
          >
            <i class="fa fa-edit"></i>
          </button>
        <button class="btn btn-outline-danger btn-sm" @click="removeTodo">
          <i class="fa fa-trash"></i>
        </button>
      </div>
    </div>
  </li>
</template>

<script>
import bootbox from 'bootbox'

export default {
  props: ['task'],
  methods: {
    removeTodo() {
      bootbox.dialog({
        message: 'Do you realy want to delete this task?',
        size: 'small',
        closeButton: false,
        centerVertical: true,
        buttons: {
          no: {
            label: 'no',
            className: 'btn-light'
          },
          yes: {
            label: 'yes',
            className: 'btn-danger',
            callback: () => {
              this.$emit('removed', this.task.i)
            }
          }
        }
      })
    },
    completeTodo() {
      this.$emit('completed', this.task.i)
    }
  }
}
</script>

<style scoped>
.todo button {
  opacity: 0;
  transition: 0.25s;
}
.todo:hover button {
  opacity: 1;
}
.todo.completed {
  background: #343a40;
}
</style>
