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
    padding: 60px 60px 120px;
}
</style>