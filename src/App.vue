<template>
    <main>
        <div class="overlay">
            <div class="modal">
                <h4>Add your note</h4>
                <textarea name="note" id="note" cols="30" rows="10"></textarea>
                <div class="modal-footer">
                    <button class="add-note">Add Note</button>
                    <button class="close">Close</button>
                </div>
            </div>
        </div>
        <div class="container">
            <header>
                <h1>Notes</h1>
                <button class="add-card">+</button>
            </header>

            <div class="cards-container">
                <div class="card">
                    <p class="main-text">
                        Lorem ipsum dolor sit amet consectetur adipisicing elit.
                        Velit tenetur saepe, facilis optio aut officia nemo,
                        quo, eligendi a inventore perferendis odit dolor
                        accusantium dolore.
                    </p>
                    <p class="date">03/07/2023</p>
                </div>
                <div class="card">
                    <p class="main-text">
                        Lorem ipsum dolor sit amet consectetur adipisicing elit.
                        Velit tenetur saepe, facilis optio aut officia nemo,
                        quo, eligendi a inventore perferendis odit dolor
                        accusantium dolore.
                    </p>
                    <p class="date">03/07/2023</p>
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
</style>
