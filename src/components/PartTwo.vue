<script>
  export default {
  data() {
    return {
      title: 'Part Two',
      myHtml: '<h1>My Html</h1>',
      person: {
        name: 'Olex',
        age: '25',
        wife: 'Lyubov'
      },
      items: [1, 2, 3, 4, 5, 6]
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
      <ul class="list">
        <!-- <li class="list-item" v-for="item in 7">{{ item }}</li> we can work with loop without array at all -->
        <!-- <li class="list-item" v-for="item in person">{{ item }}</li>  we can work with obj -->
      <li class="list-item" v-for="item in items">
        <strong>{{ item }}</strong>
      </li> 
      </ul>
    </div>
  </div>
</template>