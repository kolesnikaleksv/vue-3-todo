<script>
  export default {
  data() {
    return {
      title: 'List of notes',
      placeholderString: "Write title of note",
      inputValue: "",
      notes: ['note 1', 'note 2']
    }
  },
  methods: {
    inputChangeHanler(e) {
      this.inputValue = e.target.value
      console.log(this.inputValue)
    },
    addNewNote() {
      this.notes.push(this.inputValue)
      this.inputValue = ''
    }
  }
}
</script>

<template>
  <div class="container pt-5">
    <div class="card">
      <h1>{{ title }}</h1>
      <div class="form-control">
        <input 
          type="text" 
          :placeholder="placeholderString"
          :value="inputValue"
          v-on:input="inputChangeHanler">
      </div>
      <button class="btn pimary" @click="addNewNote">Add</button>
      <hr/>
      <ul class="list">
        <li class="list-item" v-for="myNote in notes">
          {{ myNote }}
        </li>
      </ul>
    </div>
  </div>
</template>