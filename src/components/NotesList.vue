<template>
    <article>
        <section v-for="note in notes" :key="note.id">
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
}

p {
    color: black;
}

.date {
    font-size: 0.8em;
}
</style>