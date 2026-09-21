<script setup>
import { ref } from "vue";

const newItem = ref("");
const items = ref([]);

const addItem = () => {
    if (newItem.value.trim() === "") {
        return;
    }

    items.value.push(newItem.value.trim());
    newItem.value = "";
};

const removeItem = (index) => {
    items.value.splice(index, 1);
};


const name = ref("");
const email = ref("");
const message = ref("");
const formError = ref("");
const submittedData = ref(null);

const submitForm = () => {
    if (
        name.value.trim() === "" ||
        email.value.trim() === "" ||
        message.value.trim() === ""
    ) {
        formError.value = "Por favor, complete todos los campos.";
        submittedData.value = null;
        return;
    }

    formError.value = "";
    submittedData.value = {
        name: name.value.trim(),
        email: email.value.trim(),
        message: message.value.trim(),
    };
};
</script>

<template>
    <section class="activity-page">
        <div class="page-heading">
            <h1>Lista y formulario</h1>
            <p>
             manejo de datos y eventos con Vue.
            </p>
        </div>

        <div class="activity-grid">
            <article class="card">
                <h2>Lista interactiva</h2>

                <div class="item-form">
                    <input
                        v-model="newItem"
                        type="text"
                        placeholder="Escriba un elemento"
                    />
                    <button type="button" @click="addItem">Agregar</button>
                </div>

                <p v-if="items.length === 0" class="empty-message">
                    Todavía no hay elementos en la lista.
                </p>

                <ul v-else class="items-list">
                    <li v-for="(item, index) in items" :key="index">
                        <span>{{ item }}</span>
                        <button
                            type="button"
                            class="delete-button"
                            @click="removeItem(index)"
                        >
                            Eliminar
                        </button>
                    </li>
                </ul>
            </article>

            <article class="card">
                <h2>Formulario</h2>

                <form class="simple-form" @submit.prevent="submitForm">
                    <label for="name">Nombre</label>
                    <input
                        id="name"
                        v-model="name"
                        type="text"
                        placeholder="Escriba su nombre"
                    />

                    <label for="email">Correo</label>
                    <input
                        id="email"
                        v-model="email"
                        type="email"
                        placeholder="Escriba su correo"
                    />

                    <label for="message">Mensaje</label>
                    <textarea
                        id="message"
                        v-model="message"
                        rows="4"
                        placeholder="Escriba un mensaje"
                    ></textarea>

                    <p v-if="formError" class="error-message">
                        {{ formError }}
                    </p>

                    <button type="submit">Enviar</button>
                </form>

                <div v-if="submittedData" class="result-box">
                    <h3>Información enviada</h3>
                    <p><strong>Nombre:</strong> {{ submittedData.name }}</p>
                    <p><strong>Correo:</strong> {{ submittedData.email }}</p>
                    <p><strong>Mensaje:</strong> {{ submittedData.message }}</p>
                </div>
            </article>
        </div>
    </section>
</template>

<style scoped>
.activity-page {
    display: grid;
    gap: 1.5rem;
}

.page-heading h1 {
    margin-bottom: 0.5rem;
}

.page-heading p {
    margin-top: 0;
    color: #52607a;
}

.activity-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 1.5rem;
}

.card {
    background: #ffffff;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    padding: 1.25rem;
}

.item-form {
    display: flex;
    gap: 0.75rem;
    margin-bottom: 1rem;
}

.item-form input {
    flex: 1;
}

input,
textarea {
    width: 100%;
    box-sizing: border-box;
    border: 1px solid #cbd5e1;
    border-radius: 4px;
    padding: 0.65rem;
    font: inherit;
}

button {
    background: #38c1d9;
    color: #ffffff;
    border: none;
    border-radius: 4px;
    padding: 0.65rem 1rem;
    cursor: pointer;
}

button:hover {
    opacity: 0.9;
}

.items-list {
    list-style: none;
    padding: 0;
    margin: 0;
    display: grid;
    gap: 0.75rem;
}

.items-list li {
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 1rem;
    background: #f8fafc;
    border: 1px solid #e2e8f0;
    border-radius: 4px;
    padding: 0.75rem;
}

.delete-button {
    background: #dc2626;
}

.empty-message {
    color: #64748b;
}

.simple-form {
    display: grid;
    gap: 0.7rem;
}

.simple-form label {
    font-weight: 600;
}

.error-message {
    margin: 0;
    color: #b91c1c;
}

.result-box {
    margin-top: 1rem;
    padding: 1rem;
    background: #ecfeff;
    border: 1px solid #a5f3fc;
    border-radius: 6px;
}

.result-box h3 {
    margin-top: 0;
}

.result-box p:last-child {
    margin-bottom: 0;
}

@media (max-width: 540px) {
    .item-form {
        flex-direction: column;
    }

    .items-list li {
        align-items: stretch;
        flex-direction: column;
    }
}
</style>
