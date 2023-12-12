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
    },
    addNewNote() {
      this.notes.push(this.inputValue)
      this.inputValue = ''
    },
    removeNote(idx) {
      this.notes.splice(idx,1);
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
          v-on:input="inputChangeHanler"
          v-on:keypress.enter="addNewNote"
          >
      </div>
      <button class="btn pimary" @click="addNewNote">Add note</button>
      <hr/>
      <ul class="list" v-if="notes.length !== 0">
        <li class="list-item" v-for="(myNote, idx) in notes">
          {{ myNote }}
          <button class="btn danger" v-on:click="removeNote(idx)">delete</button>
        </li>
      </ul>
      <div v-if="notes.length === 0">There are no notes, create first one</div>
    </div>
  </div>
</template>