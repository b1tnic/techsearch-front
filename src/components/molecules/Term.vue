<script setup lang="ts">
const props = defineProps({
    termTitle: {
        type: String,
        required: true
    },
    termDetail: {
        type: String,
        required: true
    }
});
</script>

<template>
<li class="term-title"> {{ termTitle }} </li>
<p class="term-detail"> {{ termDetail }} </p>
</template>

<style scoped>
.term-title {
    margin-top:16px;
    color: #f0f4f8;
}

.term-detail {
    margin: 2px 0;
    color: #f0f4f8;
}
</style>