<template>
  <li>
    <span v-bind:class="{ done: todo.completed }">
      <input
        type="checkbox"
        v-on:change="markComplete(todo.completed)"
        v-bind:checked="todo.completed"
      />
      <strong>{{ todo.id }}</strong>
      {{ todo.title }}
    </span>
    <button class="button" v-on:click="$emit('remove-todo', todo.id)">
      &times;
    </button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true,
    },
  },
  methods: {
    markComplete(isComplete) {
      this.todos.completed = !isComplete;
    },
  },
};
</script>

<style scoped>
li {
  display: flex;
  border: 1px solid pink;
  justify-content: space-between;
  padding: 0.5rem 2rem;
  margin-bottom: 1rem;
}

.button {
  border: none;
  color: #ffffff;
  font-size: 24px;
  font-weight: 600;
  background: pink;
  padding: 10px 20px;
}

.done {
  text-decoration: line-through;
}

.input {
  margin-right: 1rem;
}
</style>
