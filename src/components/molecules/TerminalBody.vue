<script setup lang="ts">
import Article from '../molecules/Article.vue'
import { Icon } from "@iconify/vue";
import axios, { AxiosError } from 'axios'
import { ref } from 'vue';
</script>

<template>
    <div class="terminal-body">
        <h1 class="terminal-body-title">
            TechSearch
        </h1>
        <h4 class="terminal-body-title-description">
            // qiitaの記事を自然言語で検索できるアプリ
        </h4>
        <div class="search-box">
            <span @click="searchArticles" class="search-box-symbol">&gt;</span>
            <textarea v-model="query" @keydown.enter="searchArticles" class="search-box-input" placeholder="// Pythonの単体テストで有効なライブラリを調べて"></textarea>
        </div>
        <p v-if="loadingFlag" class="loading">
            検索中・・・        
        </p>
        <div class="generated-box">
            <div class="generate-icon" @click="toggleFlag">
                <Icon icon="majesticons:robot" class="generate-icon" />
            </div>
            <p class="generated-box-text">
                {{ generatedText }}
            </p>
        </div>
        <Article v-for="article in articles" :key="article.ID" :article="article"></Article>
    </div>
</template>

<script lang="ts">

const loadingFlag = ref(false);

const toggleLoadingFlag = () => {
    loadingFlag.value = !loadingFlag.value
}


export default {
    data() {
        return {
            query: '',
            response: {},
            generatedText: '',
            articles: []
        }
    },
    methods: {
        async searchArticles(event: { shiftKey: any; preventDefault: () => void }) {
        if (event.shiftKey) {
            // Shift+Enterの場合は改行させたいので何もしない
            return
        } else {
            // 記事取得APIを叩く
            event.preventDefault()
            toggleLoadingFlag()
            try {
                this.articles = []
                this.generatedText = ""
                this.response = await this.sendQuery(this.query)
                this.generatedText = this.response.Output
                this.articles = this.response.Articles
            } finally {
                toggleLoadingFlag()
            }
        }
    },
    async sendQuery(query) {
        try {   
            const response = await axios.post('/api/search', 
                { q: query }
            );
            return response.data;
            } catch (err) {
            this.error = err.message;
            }
        }
    }
}
</script>


<style scope>
    .terminal-body{
        border: 1px solid #2d3548;
        background: rgba(20, 25, 40, 0.8);
        padding: 4px 20px;
        min-width:600px;
        max-width: 80%;
        margin: 0 auto;
    }

    .terminal-body-title{
        color: #64ffda;
        font-size: 48px;
        text-shadow: 0 0 30px rgba(100, 255, 218, 0.5);
        margin: 12px 0px 12px 36px;
        display: inline-block;
    }

    .terminal-body-title-description{
        margin:0 36px 24px;
        color: #8892b0;
        font-weight:300;
    }

    .loading {
        margin:0 36px 24px;
        color: #8892b0;
        font-weight:300;
    }

    .search-box {
        background: rgba(20, 25, 40, 0.8);
        border: 1px solid #2d3548;
        margin: 0 36px 24px;
        padding: 0 2px 0 24px;
        min-height: 48px;
        max-width: 800px;
        min-width: 90%;
        display:flex;
    }

    .search-box-input{
        margin: 4px auto 4px 8px;
        background: rgba(20, 25, 40, 0.8);
        border: rgba(20, 25, 40, 0.8);
        max-width: 800px;
        min-width: 96%;
        height: 48px;
        font-weight: 24px;
        font-size: 16px;
        white-space: normal;
        max-height: 96%;
        color: white;
    }

    .search-box-input::placeholder{
        font-size: 16px;
        color: #6c738aa0;
        font-weight:300;
    }

    .search-box-symbol{
        color: #64ffda;
        font-weight: 600;
        line-height: 48px;
        display: inline-block;
        margin:auto;
    }

    .generated-box {
        background: rgba(20, 25, 40, 0.8);
        border: 1px solid #2d3548;
        margin: 0 36px 24px;
        padding: 0 0 0 24px;
        min-height: 60px;
        min-width: 90%;
        display:flex;
        align-items: center;
    }

    .generated-box-text {
        color:#FFFFFF;
        margin:0;
    }

    .generate-icon {
        font-size:48px;
        color:#ffffff80;
        margin-left:auto;
        padding-left:24px;
        margin-right:24px;
    }
</style>