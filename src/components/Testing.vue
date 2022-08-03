<template>
  <div class="app">
    <div id="app">
      <input
        v-model="newTodo"
        @keyup.enter="addTodo"
        type="text"
        placeholder="New tasks go here..."
        autofocus
      />
      <button class="add" v-on:click="addTodo">Add</button>
      <!-- <button class="clear" v-on:click="clearTodos">Clear</button> -->
    </div>
    <ul>
      <li v-for="todo in todos" :key="todo"></li>
    </ul>
  </div>

  <h4 class="headline text-center">Country Price</h4>
  <div class="form-group row" v-for="country in countries" :key="country">
    <label class="col-xl-3 col-lg-3 col-form-label text-right"
      >{{ country.name }} {{ country.id }}</label
    >
    <div class="col-lg-9 col-xl-6">
      <v-text-field outlined dense></v-text-field>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodo: "",
      todos: [{ title: "Just a todo" }],
      newItemText: "",
      nextTodoId: 4,
      countries: [],

      // contents: [
      // {
      //   name: "Dog",
      //   image: [require("../SVG/Dog.png")],
      // },
      // ],
    };
  },

  methods: {
    addTodo() {},
    getCountry() {
      this.axios
        .get("http://localhost:8000/api/countries/")
        .then((response) => {
          this.countries = response.data;
        })
        // .catch((error) => {});
    },
  },
};
</script>

<style>
/*  */
</style>
