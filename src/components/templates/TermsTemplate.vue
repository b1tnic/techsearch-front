<script setup lang="ts">
import Header from '../organisms/Header.vue'
import Sidebar from '../organisms/Sidebar.vue'
import Terms from '../organisms/Terms.vue'
</script>

<template>
    <div class="background">
        <Header />
        <Sidebar />
        <Terms />
    </div>
</template>

<style scoped>
    .background{
        margin: 0;
        min-height:100vh;
        background: linear-gradient(to left, rgba(20, 25, 40, 1), rgba(30, 30, 50, 0.9), rgba(50, 40, 70, 0.85), rgba(70, 50, 90, 0.8));
    }
</style>