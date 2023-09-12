<script setup>
    const props = defineProps(["slotTitle"]);
</script>

<template>
    <h1>{{props.slotTitle}}</h1>
   <article>
    <slot name="pargraphe1">
        
    </slot>
    <hr />
    <slot name="pargraphe2">

    </slot>
   </article>
</template>
