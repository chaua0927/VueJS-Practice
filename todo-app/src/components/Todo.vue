<template>
    <div class='ui centered card'>
      <!-- show Todo when not in edit mode -->
      <div class='content' v-show="!isEditing">
        <div class='header'>
          {{todo.title}}
        </div>
        <div class='meta'>
          {{todo.project}}
        </div>
        <div class='extra content'>
          <span class='right floated edit icon' v-on:click="showForm">
            <i class='edit icon'></i>
          </span>
          <span class='right floated trash icon' v-on:click="deleteTodo(todo)">
            <i class='trash icon'></i>
          </span>
        </div>
      </div>
      <!-- show form when in edit mode -->
      <div class='content' v-show="isEditing">
        <div class='ui form'>
          <div class='field'>
            <label>Title</label>
            <input type='text' v-model="todo.title">
          </div>
          <div class='field'>
            <label>Project</label>
            <input type='text' v-model="todo.project">
          </div>
          <div class='ui two button attached buttons'>
            <button class='ui basic blue button' v-on:click="hideForm">
              Close X
            </button>
          </div>
        </div>
      </div>
      <div class='ui bottom attached green basic button'
              v-show="!isEditing && todo.isDone">
        Completed
      </div>
      <div class='ui bottom attached red basic button'
              v-show="!isEditing && !todo.isDone"
              v-on:click="completeTodo(todo)">
        Pending
      </div>
    </div>
</template>

<script>
export default {
  props: ['todo'],
  methods: {
    showForm() {
      this.isEditing = true;
    },
    hideForm() {
      this.isEditing = false;
    },
    deleteTodo(todo) {
      this.$emit('delete-todo', todo);
    },
    completeTodo(todo) {
      this.$emit('complete-todo', todo);
    },
  },
  data() {
    return {
      isEditing: false,
    };
  },
};
</script>
