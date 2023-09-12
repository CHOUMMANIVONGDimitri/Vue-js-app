<script setup>
    import { computed } from 'vue';
    const props = defineProps(["user"]);

    const sentence = computed(() => {
        return `Ton nom est ${props.user.name} et tu as ${props.user.age} ans.`
    });
</script>

<template>
    <h1>Forms :</h1>

    {{ sentence }}

    <p>name : {{ props.user.name }}</p>
    <p>age : {{ props.user.age }}</p>
</template>
