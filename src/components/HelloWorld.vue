<script setup>
    const props = defineProps(["subTitle", "title"]);
</script>

<template>
    <h1>{{ props.title }}</h1>
    <p>{{ props.subTitle }}</p>
</template>
