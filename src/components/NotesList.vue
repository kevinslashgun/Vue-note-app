<template>
    <article>
        <section v-for="note in notes" :key="note.id" :style="{ backgroundColor: note.backgroundColor }">
            <button type="button" class="close" @click="close">X</button>
            <p v-html="formatText(note.text)"></p>
            <p class="date">{{ note.date }}</p>
        </section>
    </article>
</template>

<script setup>
const props = defineProps(['notes'])

const formatText = (text) => {
    // Aggiungi un newline ogni tot caratteri senza tagliare le parole a metà
    const maxCharactersPerLine = 30; // Modifica a seconda delle tue esigenze
    // Espressione regolare per dividere il testo in linee di lunghezza massima senza tagliare le parole
    const regex = new RegExp(`.{1,${maxCharactersPerLine}}(?:\\b|\\W|$)`, 'g');
    return text.match(regex).join('<br>');
}

const close = () => {
    // Implementa la logica per chiudere la nota
}
</script>

<style scoped>
article {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    /* Colonne di larghezza fissa */
    padding: 1em;
    gap: 1em;
}

section {
    display: grid;
    grid-template-rows: auto 1fr auto;
    /* Una riga per il pulsante, una per il testo principale, una per la data */
    height: 300px;
    background-color: lightgray;
    border-radius: 10px;
    padding: 1.5em;
}

p {
    color: black;
    font-size: 1.2em;
    margin: 0;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
    /* Nasconde il testo che supera il contenitore */
    word-wrap: break-word;
    /* Permette il wrapping delle parole lunghe */
    text-align: justify;
    /* Giustifica il testo */
}

.date {
    font-size: 0.8em;
    justify-self: start;
    /* Allineamento della data a sinistra */
}

.close {
    justify-self: end;
    /* Allineamento del pulsante X a destra */
    background-color: transparent;
    border-radius: 10px;
    border: none;
}

.close:hover {
    background-color: red;
    color: black;
}
</style>
