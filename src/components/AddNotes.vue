<template>
    <form>
        <label for="note">Note:</label>
        <button type="button" class="close" @click="close">X</button>
        <textarea v-model="note" name="note" id="note" cols="30" rows="10"></textarea>
        <button type="button" @click="submit">Add Note</button>
    </form>
</template>

<script setup>
import { ref } from 'vue'
const emit = defineEmits(['closeModal', 'addNote'])
const note = ref('')

const close = () => {
    emit('closeModal')
}

const submit = () => {
    emit('addNote', note.value, new Date().toLocaleString("it-IT"))
    note.value = ''
}
</script>

<style scoped>
form {
    background-color: aliceblue;
    border-radius: 10px;
    padding: 1em;
    margin: 1em;
    position: relative;
    display: flex;
    flex-direction: column;
    color: black;
}

label {
    font-size: 1.5em;
    margin-bottom: 0.5em;
}

.close {
    background-color: transparent;
    border: none;
    border-radius: 10px;
    color: black;
    font-size: 1em;
    cursor: pointer;
    width: 2em;
    /* Utilizzo di un valore specifico per width invece di percentuale */
    height: 2em;
    /* Utilizzo di un valore specifico per height invece di percentuale */
    position: absolute;
    right: 0;
    top: 0;
    transition: color 0.3s ease;
}

.close:hover {
    background-color: red;
}

textarea,
.note-text {
    border-radius: 5px;
    padding: 0.5em;
    margin-bottom: 1em;
    overflow: auto;
    /* Abilita lo scrolling se il testo supera il contenitore */
}

button {
    background-color: black;
    border: none;
    border-radius: 5px;
    color: aliceblue;
    font-size: 1.5em;
    padding: 0.5em;
    width: 100%;
    cursor: pointer;
    transition: background-color 0.3s ease, color 0.3s ease;
}

button:hover {
    background-color: darkblue;
    color: white;
}
</style>
