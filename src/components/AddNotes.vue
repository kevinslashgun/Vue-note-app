<template>
    <form>
        <label for="note">Note:</label>
        <button type="button" class="close" @click="close">X</button>
        <textarea name="note" id="note" cols="30" rows="10"></textarea>
        <button type="button" @click="submit">Add Note</button>
    </form>
</template>

<script setup>
import { ref } from 'vue'
const emit = defineEmits(['closeModal', 'addNote'])
const close = () => {
    emit('closeModal')
}
const submit = () => {
    const currentDate = new Date();

    const day = currentDate.getDate().toString().padStart(2, '0');
    const month = (currentDate.getMonth() + 1).toString().padStart(2, '0'); // Aggiungi 1 perché i mesi sono zero-based
    const year = currentDate.getFullYear();

    const dateString = `${day}/${month}/${year}`;

    console.log(dateString);

    emit('addNote', note.value, dateString)
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
    width: 10%;
    height: 10%;
    position: absolute;
    right: 0;
    top: 0;
    transition: color 0.3s ease;
}

.close:hover {
    background-color: red;
    color: black;
}


textarea {
    border-radius: 5px;
    padding: 0.5em;
    margin-bottom: 1em;
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
    cursor: pointer;
}
</style>