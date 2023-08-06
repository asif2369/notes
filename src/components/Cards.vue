<script setup>
// const props = defineProps(["note"]);
defineProps({
    note: {
        type: Object,
    },
});
</script>

<template>
    <div class="card" :style="{ backgroundColor: note.backgroundColor }">
        <p class="main-text">
            {{ note.text }}
        </p>
        <p class="date">
            {{ note.date.toLocaleDateString("en-US") }}
        </p>
    </div>
</template>

<style scoped>
.card {
    height: 250px;
    width: 250px;
    background-color: lime;
    padding: 1rem;
    border-radius: 1rem;
    margin-bottom: 20px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
}
.card:hover {
    opacity: 0.9;
}

.date {
    font-size: 0.75rem;
    font-weight: bold;
}
</style>
