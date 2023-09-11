<script setup>
  import { ref, onMounted, computed, watch } from 'vue'

  const todos = ref([])
  const name = ref('')

  const input_content = ref('')
  const input_category = ref(null)

  const todo_asc = computed(() => todos.value.sort((a,b) => {
    return a.createAt - b.createAt
  }))

</script>

<template>
  <main class="app">
    <section class="greeting">
      <h2 class="title">
        Hello, <input type="text" id="name" placeholder="Name Here" v-model="name" /> !
      </h2>
    </section>
    <section class="create-todo">
      <h3>CREATE A TODO</h3>
      <form id="new-todo-form" @submit.prevent="addTodo">
        <h4>What do you want to do today</h4>
        <input type="text" name="content" id="content" placeholder="Create Todo..." v-model="input_content"/>
        <h4>Pick a Category</h4>
        <div class="options">
          <label>
            <input type="radio" name="category" id="category" value="business" v-model="input_category"/>
            <span class="bubble business"></span>
            <div>Business</div>
          </label>
          <label>
            <input type="radio" name="category" id="category" value="personal" v-model="input_category"/>
            <span class="bubble personal"></span>
            <div>Personal</div>
          </label>
        </div>
        <input type="submit" value="Add todo" />
      </form>
    </section>
  </main>
</template>
