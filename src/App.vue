<script setup>
import { ref } from "vue";

// generate unique id
function generateUniqueId() {
    const digits = "0123456789";
    let uniqueId = "";

    for (let i = 0; i < 8; i++) {
        const randomIndex = Math.floor(Math.random() * digits.length);
        uniqueId += digits[randomIndex];
    }

    return uniqueId;
}

// generate random light color
function getRandomColor() {
    let color = "hsl(" + Math.random() * 360 + ", 100%, 75%)";
    return color;
}

const showModal = ref(false);
const newNote = ref("");
const notes = ref([]);
const errorMessage = ref("");

const addNote = () => {
    if (newNote.value.length < 9) {
        return (errorMessage.value = "Please add at least 10 characters");
    }
    notes.value.push({
        id: generateUniqueId(),
        text: newNote.value,
        date: new Date(),
        backgroundColor: getRandomColor(),
    });
    newNote.value = "";
    showModal.value = false;
    errorMessage.value = "";
};

const removeCard = (card) => {
    notes.value = notes.value.filter((i) => i.id !== card.id);
};
</script>

<template>
    <main>
        <div v-if="showModal" class="overlay">
            <div class="modal">
                <h4>Add your note</h4>
                <textarea
                    v-model.trim="newNote"
                    name="note"
                    id="note"
                    cols="30"
                    rows="10"
                ></textarea>
                <p v-if="errorMessage" class="error-message">
                    {{ errorMessage }}
                </p>
                <div class="modal-footer">
                    <button @click="addNote" class="add-note">Add Note</button>
                    <button @click="showModal = false" class="close">
                        Close
                    </button>
                </div>
            </div>
        </div>
        <div class="container">
            <header>
                <h1>Notes App</h1>
                <button @click="showModal = true" class="add-card">+</button>
            </header>

            <div class="cards-container">
                <div
                    v-for="note in notes"
                    :key="note.id"
                    class="card"
                    :style="{ backgroundColor: note.backgroundColor }"
                    @click="removeCard(note)"
                >
                    <p class="main-text">{{ note.text }}</p>
                    <p class="date">
                        {{ note.date.toLocaleDateString("en-US") }}
                    </p>
                </div>
            </div>
        </div>
    </main>
</template>

<style scoped>
main {
    height: 100vh;
}
.container {
    max-width: 1000px;
    margin: 0 auto;
    padding: 10px;
}

header {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

h1 {
    font-weight: bold;
    font-size: 5rem;
    margin-bottom: 2rem;
}

h4 {
    font-size: 1rem;
}

.add-card {
    border: none;
    height: 50px;
    width: 50px;
    line-height: 50px;
    text-align: center;
    border-radius: 50%;
    color: #fff;
    background-color: #222;
    font-size: 2rem;
    cursor: pointer;
    font-weight: light;
}

.cards-container {
    display: flex;
    gap: 20px;
}

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

.date {
    font-size: 0.75rem;
    font-weight: bold;
}

.overlay {
    position: fixed;
    z-index: 9;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.8);
    display: flex;
    justify-content: center;
    align-items: center;
}

.modal {
    max-width: 600px;
    width: 100%;
    border-radius: 1rem;
    padding: 2rem;
    background-color: #fff;
}

.modal textarea {
    width: 100%;
    border: 1px solid grey;
    padding: 10px;
    resize: none;
}
.modal-footer {
    display: flex;
    justify-content: space-between;
}

.modal-footer button {
    border: 0;
    height: 30px;
    width: 100px;
    color: #fff;
    cursor: pointer;
}

.modal-footer .add-note {
    background-color: rgb(89, 67, 192);
}

.modal-footer .close {
    background-color: rgb(202, 28, 28);
}

.error-message {
    color: #ff0000;
    margin-bottom: 0.5rem;
}
</style>
