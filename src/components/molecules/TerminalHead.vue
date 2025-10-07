<template>
    <div class="terminal-header">
        <div class="dots">
            <div class="dot red"></div>
            <div class="dot yellow"></div>
            <div class="dot green"></div>
        </div>
        <div class="terminal-title">
            <p class="title">techsearch:@bedrock</p>
        </div>
    </div>
</template>

<style scope>
    .terminal-header{
        min-width:600px;
        max-width: 80%;
        margin: 0 auto;
        background: rgba(20, 25, 40, 0.8);
        border-radius: 12px 12px 0 0;
        padding: 4px 20px;
        border: 1px solid #2d3548;
        backdrop-filter: blur(10px);
        display: flex;
        align-items: center;
    }

    .dots{
        margin: auto 15px auto;
        display: flex;
    }

    .dot {
        width: 12px;
        height: 12px;
        border-radius: 50%;
        margin-left: 6px;
    }
    .dot.red { background: #ff5f56; }
    .dot.yellow { background: #ffbd2e; }
    .dot.green { background: #27c93f; }

    .title{
        color: #8892b0;
        font-size: 14px;
        margin-left: 10px;
    }
</style>