<template>
  <div class="container">
    <h1>My to-do list!</h1>
    <input
      v-model="currentValue"
      type="text"
      placeholder="Add task..."
      @keyup.enter="addTask()"
      class="container-input">
    <ul>
      <li v-for="(item, index) in items" :key="index">
        <input type="checkbox" v-model="item.isDone">
        <template v-if="item.isDone">
          <s>{{ item.name }}</s>
        </template>
        <template v-else>
          {{ item.name }}
        </template>
        <button @click="removeTask(index)">delete</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'App',
  data: () => ({
    currentValue: '',
    items: [{
      name: 'First item',
      isDone: false
    }]
  }),
  methods: {
    addTask () {
      this.items.push({
        name: this.currentValue,
        isDone: false
      })
      this.currentValue = '';
    },
    removeTask (index) {
      this.items.splice(index, 1)
    }
  }
}
</script>

<style src="./style.css"></style>
