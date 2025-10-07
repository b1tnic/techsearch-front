<script setup lang="ts">
import TerminalHead from '../molecules/TerminalHead.vue'
import TerminalBody from '../molecules/TerminalBody.vue'
</script>

<template>
    <div class="terminal">
        <TerminalHead />
        <TerminalBody />
    </div>
</template>

<style scoped>
.terminal {
    max-width: 1280px;
    margin:40px 30px;
}
</style>