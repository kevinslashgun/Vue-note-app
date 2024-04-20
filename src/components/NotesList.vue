<template>
    <article>
        <section v-for="note in notes" :key="note.id" :style="{backgroundColor: note.backgroundColor}">
            <p>{{ note.text }}</p>
            <p class="date">{{ note.date }}</p>
        </section>
    </article>
</template>

<script setup>
const props = defineProps(['notes'])
</script>

<style scoped>
article {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
    margin-top: 1em;
}

section {
    background-color:burlywood;
    border-radius: 5px;
    padding: 1em;
    margin: 1em;
    height: 200px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
}

p {
    color: black;
}

.date {
    font-size: 0.8em;
}
</style>