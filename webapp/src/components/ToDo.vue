<template>
  <div class="todo columns">
    <b-checkbox v-model="todo.done" v-on:input="handleCheck" />
    <span class="todo-title column">
      {{ todo.title }}
    </span>
    <div class="dropdown">
              <b-button v-on:click="drop" class="submit">Category</b-button>
              <div id="myDropdown" class="dropdown-content">
                <a href="#home">school</a>
                <a href="#about">home</a>
                <a href="#contact">work</a>
              </div>
            </div>
    <b-button v-on:click="handleDelete">Delete</b-button>
  </div>
</template>
debugger;
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
    handleCheck: function(value) {
      this.$store.dispatch("updateTodo", { ...this.todo, done: value });
    },
    handleDelete: function() {
      this.$store.dispatch("deleteTodo", this.todo);
    },
    drop: function() {
      document.getElementById("myDropdown").classList.toggle("show");
    }
  }
};
</script>
<style scoped>
.dropbtn {
  background-color: #3498DB;
  color: white;
  padding: 16px;
  font-size: 16px;
  border: none;
  cursor: pointer;
}

.dropbtn:hover, .dropbtn:focus {
  background-color: #2980B9;
}

.dropdown {
  position: relative;
  display: inline-block;
}

.dropdown-content {
  display: none;
  position: absolute;
  background-color: #f1f1f1;
  min-width: 160px;
  overflow: auto;
  box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
  z-index: 1;
}

.dropdown-content a {
  color: black;
  padding: 12px 16px;
  text-decoration: none;
  display: block;
}

.dropdown a:hover {
  background-color: #ddd;
}

.show {
  display: block;
}
</style>
