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
    addNewNote() {
      if(this.inputValue !== '') {
        this.notes.push(this.inputValue)
        this.inputValue = ''
      }
    },
    toUpperCase(item) {
      return item.toUpperCase()
    },
   
    removeNote(idx) {
      this.notes.splice(idx,1);
    }
  },
  computed: {
    doubleCount() {
      return this.notes.length * 2;
    }
  },
  watch: {
    inputValue(value) {
      if(value.length >= 10) {
        this.inputValue = ''
      }
      console.log(`input value watch: ${value}`)
    }
  }
}
</script>

<template>
  <div class="container pt-5">
    <div class="card">
      <!-- <h1 style="color: green">{{ title }}</h1> -->
      <!-- <h1 :style="{color: 'green'}">{{ title }}</h1> -->
      <h1 :style="{
        color: inputValue.length < 5 ? 'green': 'red',
        fontSize: inputValue.length < 6 ? '1.5rem' : '2rem'
      }">{{ title }}</h1>
      <div class="form-control">
        <input 
          type="text" 
          :placeholder="placeholderString"
          v-model="inputValue"
          @keypress.enter="addNewNote"
          >
      </div>
      <button class="btn pimary" v-on:click="addNewNote">Add note</button>
      <hr/>
      <ul class="list" v-if="notes.length !== 0">
        <li class="list-item" v-for="(myNote, idx) in notes">
          <!-- <span :class="myNote.length < 3 ? 'primary' : 'bold'">{{ idx + 1 }}. {{ toUpperCase(myNote) }}</span> -->
          <!-- <span :class="{
            'primary': true,
            'bold': myNote.length > 3
          }">{{ idx + 1 }}. {{ toUpperCase(myNote) }}</span> -->
          <span :class="['primary', {'bold': myNote.length > 3}]">{{ idx + 1 }}. {{ toUpperCase(myNote) }}</span>
          <button class="btn danger" v-on:click="removeNote(idx)">delete</button>
        </li>
        <hr/>
        <li>
          notes count {{ notes.length }} 
          <strong>| double: {{ doubleCount }}</strong>
        </li>
      </ul>
      <div v-else>There are no notes, create first one</div>
    </div>
  </div>
</template>