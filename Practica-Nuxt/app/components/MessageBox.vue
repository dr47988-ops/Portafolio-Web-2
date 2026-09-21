<script lang="ts" setup>
const props = defineProps<{
    title?: string;
}>();
const { title = "Mensaje" } = props;
</script>
<template>
    <article class="card">
        <h2>{{ title }}</h2>
        <p>Este es un mensaje de ejemplo.</p>
    </article>
</template>
<style scoped>
.card {
    background: #fff;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    padding: 1rem;
}
</style>
