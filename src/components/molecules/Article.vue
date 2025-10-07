<script setup lang="ts">
import { Icon } from "@iconify/vue";
import { computed, ref } from "vue";
import { marked } from "marked"

const props = defineProps({
    article: {
        type: Object,
        required: true
    }
});

const modalShowFlag = ref(false);

const toggleModalFlag = () => {
    modalShowFlag.value = !modalShowFlag.value
}

// 記事本文の文字数制限
const formatArticleBody = (body: string):string => {
    return body.slice(0,36)
}

// 日時変換関数
const formatDateTime = (dateString: string): string => {
    if (!dateString) return '';
    
    const date = new Date(dateString);
    
    // yyyy/MM/dd hh:mm:ss形式に整形
    const year = date.getFullYear();
    const month = String(date.getMonth() + 1).padStart(2, '0');
    const day = String(date.getDate()).padStart(2, '0');
    const hours = String(date.getHours()).padStart(2, '0');
    const minutes = String(date.getMinutes()).padStart(2, '0');
    const seconds = String(date.getSeconds()).padStart(2, '0');
    
    return `${year}/${month}/${day} ${hours}:${minutes}:${seconds}`;
};

const formattedArticleBody = computed(() => formatArticleBody(props.article.Body))
const formattedCreatedAt = computed(() => formatDateTime(props.article.CreatedAt));
const formattedUpdatedAt = computed(() => formatDateTime(props.article.UpdatedAt));

const parsedBody = computed(() => {
  return marked(props.article.Body);
});
</script>

<template>
    <div class="article-box">
        <a :href="article.Url" target="_blank">
            <div class="article-part-box">
                <p class="article-part article-title">{{ article.Title }}</p>
                <p class="article-part article-body">{{ formattedArticleBody }}</p>
                <div class="article-part article-informations">
                    <Icon icon="tabler:heart" />
                    <p class="article-part article-likesCount">{{ article.LikesCount }}</p>
                    <Icon icon="material-symbols:book-outline-rounded" />
                    <p class="article-part article-stocksCount">{{ article.StocksCount }}</p>
                                <p class="article-part article-createdAt">作成: {{ formattedCreatedAt }}</p>
                    <p class="article-part article-updatedAt">更新: {{ formattedUpdatedAt }}</p>
                </div>
            </div>
        </a>
        <div class="article-icon" @click="toggleModalFlag">
            <Icon icon="stash:article" class="article-icon" />
        </div>
    </div>
    <Transition name="article-modal">
        <div v-if="modalShowFlag" @click="toggleModalFlag">
            <div class="overlay">
            </div>
            <div class="modal">
                <div class="title">
                </div>
                <div v-html="parsedBody"></div>
            </div>
        </div>
    </Transition>
</template>

<style scoped>
    .article-box {
        background: rgba(20, 25, 40, 0.8);
        border: 1px solid #2d3548;
        margin: 0 36px 24px;
        padding: 0 0 0 24px;
        min-height: 60px;
        min-width: 90%;
        display:flex;
        align-items: center;
        text-decoration: none;
    }

    .article-part {
        color:#FFFFFF;
        margin:0;
    }

    .article-part-box {
        opacity:0.5;
    }

    .article-part-box:hover {
        opacity:0.7;
    }

    .article-informations {
        display: flex;
        align-items: center;
        gap: 8px;
    }

    .article-title {
        font-size:14px;
    }

    .article-body {
        font-size:12px;
        color:#ffffff80;
    }

    .article-likesCount {
        font-size:12px;
    }

    .article-stocksCount {
        font-size:12px;
    }

    .article-updatedAt,
    .article-createdAt {
        font-size:12px;
        color:#ffffff80;
    }

    .article-icon {
        font-size:48px;
        color:#ffffff80;
        margin-left:auto;
        padding-left:24px;
        margin-right:24px;
    }

    .article-icon:hover {
        opacity:0.7;
    }


    .article-modal-enter-from .overlay,
    .article-modal-leave-to .overlay{
      opacity:0;
    }

    .article-modal-enter-from .modal,
    .article-modal-leave-to .modal{
      right: -1200px;
    }

    .article-modal-enter-active,
    .article-modal-leave-active {
      transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
    }

    .overlay {
      position: fixed;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background: rgba(255, 255, 255, 0.3);
      backdrop-filter: blur(5px);
      z-index: 998;
      opacity: 0.8;
      transition: opacity 0.4s;
    }

    .modal {
      position: fixed;
      top: 0;
      right: 0px;
      height: 100vh;
      width: 1200px;
      background: white;
      box-shadow: -10px 0 30px rgba(0,0,0,0.15);
      z-index: 999;
      overflow-y: auto;
      transition: right 0.4s cubic-bezier(0.4, 0, 0.2, 1);
    }
</style>