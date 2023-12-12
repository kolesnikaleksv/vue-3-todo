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
      // items: [1, 2, 3, 4, 5, 6]
      items: [1, 2]
    }
  },
  methods: {
    addItem() {
      this.items.unshift(this.$refs.myInput.value)
      this.$refs.myInput.value = ''
      console.log(this.$refs)
    }
  },
  computed: {
    filterItems() {
      return this.items.filter(i => i % 2 === 0)
    }
  }
}
</script>

<template>
  <div class="container pt-5">
    <div class="card center">
      <div class="form-control">
        <input type="text" @keyup.enter="addItem" ref="myInput">
      </div>
      <div v-html="myHtml"></div> <!-- v-html - can rander your html -->
      <h2 v-text="title"></h2>
      <h2 v-once>{{ title }}</h2> <!-- v-once - work only once, you can't change that title -->
      <h2 v-pre>{{ title }}</h2> <!-- v-pre - for debagging -->
      <button class="btn" @click="this.title = 'Changed title'">Change titile</button>
      <!-- <ul class="list" v-if="items.length !== 0"> -->
        <!-- v-if="items.length" - is the same like above -->
      <ul class="list" v-if="items.length">
        <!-- <li class="list-item" v-for="item in 7">{{ item }}</li> we can work with loop without array at all -->
        <!-- <li class="list-item" v-for="item in person">{{ item }}</li>  we can work with obj -->
      <li 
        class="list-item"
        v-for="(item, i) in filterItems"
        @click="items.splice(i,1)"
        :key="item">   
         <!-- we can delete element like this --> <!-- we always have to use key but with item, not with i --> 
         <!-- v-for="(item, i) in items" --> <!-- in that way we can filter elements --> <!-- v-for="(item, i) in filterItems" -->
        <strong>{{ item }}</strong>&nbsp;
        <input type="text" @click.stop> <!-- it's like e.preventDefault or stopPropagation-->
      </li> 
      </ul>
      <!-- <h3 v-else>There are not elements</h3> -->
      <!-- <h3 v-show="items.length === 0">There are not elements</h3> elements will be always but with display: none -->
    </div>
  </div>
</template>