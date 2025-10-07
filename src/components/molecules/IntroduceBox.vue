<script setup lang="ts">
const props = defineProps({
    title: {
        type: String,
        required: true
    },
    imgPath: {
        type:String,
        required: true
    }
});
</script>

<template>
    <div class="introduce-box">
        <p>
            {{ title }}
        </p>
        <img :src="imgPath" alt="サイト説明">
    </div>
</template>

<style scoped>
.introduce-box {
    max-width:800px;
    width:50%;
    min-width:400px;
    justify-content: center;
    text-align: center;
    color: #f0f4f8;
}

.introduce-box img {
    max-width:800px;
    width:94%;
    min-width:400px;
}

</style>