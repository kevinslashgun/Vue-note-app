<template>
  <div class="overlay" v-if="showAddNote">
    <AddNotes @closeModal="closeModal" @addNote="sendNote"/>
  </div>
  <header>
    <h1>Notes</h1>
    <button @click="addNote">+</button>
  </header>
  <main>
    <NotesList :notes="notes" />
  </main>
</template>

<script setup>
import NotesList from './components/NotesList.vue'
import AddNotes from './components/AddNotes.vue'

import { ref } from 'vue'

const showAddNote = ref(false)
const id = ref(0)
const notes = ref([])

const addNote = () => {
  showAddNote.value = true
}

const closeModal = () => {
  showAddNote.value = false
}

const sendNote = (note, date) => {
  notes.value.push({ id: id.value++, text: note, date: date})
  showAddNote.value = false
}

</script>

<style scoped>
.overlay {
  background-color: rgba(0, 0, 0, 0.5);
  height: 100%;
  position: fixed;
  width: 100%;
  z-index: 1;
  display: flex;
  justify-content: center;
  align-items: center;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: black;
  color: aliceblue;
  padding: 1em;
}

h1 {
  font-size: 3em;
}

button {
  background-color: aliceblue;
  border: none;
  border-radius: 50%;
  color: black;
  font-size: 2em;
  height: 2em;
  width: 2em;
  margin-top: 10px;
  transition: background-color 0.3s ease, box-shadow 0.3s ease;
}

button:hover {
  background-color: lightblue;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
  cursor: pointer;
}
</style>