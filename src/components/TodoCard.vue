<template>
    <div class="ui centered card">
      <!-- Show when not in editing mode -->
      <div class="content" v-show="!isEditing">
        <div class="header">
          {{ todo.title }}
        </div>
        <div class="meta">
          {{ todo.project }}
        </div>
        <div class="extra content">
          <span class="right floated edit icon" @click="showForm"><i class="edit icon"></i></span>
          <span class="right floated trash icon" @click="deleteTodo(todo)"><i class="trash icon"></i></span>
        </div>
      </div>
      <!-- Show form when in editing mode -->
      <div class="content" v-show="isEditing">
        <div class="ui form">
          <div class="field">
            <label for="title">Title</label>
            <input type="text" id="title" v-model="todo.title">
          </div>
          <div class="field">
            <label for="project">Project</label>
            <input type="text" id="project" v-model="todo.project">
          </div>
          <div class="ui two button attached buttons">
            <button class="ui basic blue button" @click="hideForm">閉じる</button>
          </div>
        </div>
      </div>
      <div class="ui bottom attached green basic button" v-show="todo.done" @click="completeTodo(todo)">完了済</div>
      <div class="ui bottom attached red basic button" v-show="!todo.done" @click="completeTodo(todo)">未完了</div>
    </div>
</template>
<script type = "text/javascript" >

export default {
  props: ['todo'],
  data() {
    return {
      isEditing: false,
    };
  },
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
};
</script>
