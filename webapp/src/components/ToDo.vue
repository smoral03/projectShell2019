<template>
  <div class="todo">
    <b-checkbox v-model="todo.done" v-on:input="onDone($event)" />
    <span class="todo-title">
      {{ todo.title }}
      <b-button v-on:click="onDelete" type="is-danger" size="is-small" rounded = "true" outlined>Delete</b-button>
    </span>
  </div>
</template>

<script>
export default {
  name: "ToDo",
  props: {
    todo: {
      type: Object,
      default: () => {
        return {};
      }
    }
  },
  methods: {
    onDelete () {
      debugger;
      this.$store.dispatch('dToDo', this.todo.id)
    },
    onDone (event){
      debugger;
      this.todo.done = event;
      this.$store.dispatch('dDone', this.todo)
    }
  }
};
</script>
