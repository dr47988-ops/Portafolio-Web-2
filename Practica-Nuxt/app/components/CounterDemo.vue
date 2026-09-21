<script setup>
// composition API
import { ref } from "vue";
const count = ref(0);
const increment = () => {
    count.value++;
};

//hooks https://vuejs.org/api/composition-api-lifecycle.html
onMounted(() => {
    console.log("CounterDemo component mounted");
});

console.log("CounterDemo component setup executed");
</script>
<template>
    <article class="card">
        <h2>Contador</h2>
        <p>Valor actual: {{ count }}</p>
        <p v-if="count > 5">contador mayor de 5!</p>
        <p v-else>contador menor o igual a 5!</p>
        <button @click="increment">Incrementar</button>
    </article>
</template>
<style scoped>
.card {
    background: #fff;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    padding: 1rem;
}

button {
    background: #38c1d9;
    color: #fff;
    border: none;
    padding: 0.5rem 1rem;
    border-radius: 4px;
    cursor: pointer;
}
</style>
