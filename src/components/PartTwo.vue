<script>
  export default {
  data() {
    return {
      title: 'Part Two',
      myHtml: '<h1>My Html</h1>'
    }
  },
  methods: {
    
  }
}
</script>

<template>
  <div class="container pt-5">
    <div class="card center">
      <div v-html="myHtml"></div> <!-- v-html - can rander your html -->
      <h2 v-text="title"></h2>
      <h2 v-once>{{ title }}</h2> <!-- v-once - work only once, you can't change that title -->
      <h2 v-pre>{{ title }}</h2> <!-- v-pre - for debagging -->
      <button class="btn" @click="this.title = 'Changed title'">Change titile</button>
    </div>
  </div>
</template>