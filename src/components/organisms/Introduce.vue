<script setup lang="ts">
    import IntroduceBox from '../molecules/IntroduceBox.vue'
</script>

<template>
    <div class="introduce">
        <div class="introduce-page">
            <h1 class="introduce-page-title">
                技術記事に　　　　<br>
                　　　あいまいな検索を。
            </h1>
            <h2 class="introduce-page-detail">
                完全無料でQiita記事に対して「あいまい」な検索ができるサービスです。
            </h2>    
            <h3 class="introduce-page-detail-list">
                　・検索文言を考えるのがめんどくさい。<br>
                　・記事を探す時、いちいち開くのがめんどくさい。<br>
                　・単語ベースではなく、より具体的な検索がしたい。<br>
            </h3>
            <h2 class="introduce-page-detail">
                そんなときにご利用いただけます！
            </h2>
        </div>
        <div class="introduce-box-area">
            <IntroduceBox :title="'Qiita記事を基にAIが回答を生成'" :imgPath="'/src/assets/techsearch-demo.png'"></IntroduceBox>
            <IntroduceBox :title="'記事本文のプレビューを画面上で閲覧'" :imgPath="'/src/assets/techsearch-demo2.png'"></IntroduceBox>
        </div>
    </div>
</template>

<style scoped>
.introduce {
    margin:40px;
}

.introduce-page {
    margin-bottom:32px;
}

.introduce-page-title {
    color: #f0f4f8;
    font-size:60px;
    transform: skew(-16deg);
    text-shadow: 2px 2px 4px #f0f4f8;
}

.introduce-page-detail {
    color: #f0f4f8;
    font-size:24px;
    margin:2px;
    font-weight:500;
}

.introduce-page-detail-list {
    color: #f0f4f8b5;
    font-size:24px;
    margin:2px;
    font-weight:500;
}

.introduce-box-area {
    display:flex;
    flex-wrap: wrap;
    justify-content: center;
}
</style>