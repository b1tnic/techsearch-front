<script setup lang="ts">
    import Term from '../molecules/Term.vue'
</script>

<template>
    <div class="terms">
        <h1 class="terms-title">
            本サービスについて
        </h1>
        <ul>
            <Term :termTitle="'サービス内容'" :termDetail="'本サービスは技術記事に対して、AIを使用してベクトル検索ができるサービスです。'"></Term>
            <Term :termTitle="'商用利用について'" :termDetail="'本サービスで得た情報の商用利用は、有償・無償を問わずに禁止しています。'"></Term>
            <Term :termTitle="'データソースについて'" :termDetail="'本サービスの技術記事はQiita APIを通して作成されております。 データの更新日時によってリアルタイムなデータと誤差がある可能性があるのでご了承ください。'"></Term>
            <Term :termTitle="'損害について'" :termDetail="'本サービスのデータ提供により生じた損害はデータの整合性の有無にかかわらず保障できません。'"></Term>
            <Term :termTitle="'データ範囲について'" :termDetail="'技術記事については、随時追加していますがQiitaの全記事の情報がある訳ではないのでご了承ください。'"></Term>
            <Term :termTitle="'データ更新のタイミング'" :termDetail="'毎日、午前3時～4時頃に、最終更新日時が前日の記事の情報を取得しております。'"></Term>
            <Term :termTitle="'全体のアクセス制限'" :termDetail="'無償のサービスを継続して提供するため、本サービスの1日のデータ通信量の限度をユーザ全体の合計で定めています。 ユーザ全体からのアクセス量が限度を超えると、アクセスに規制がかかることがあります。 アクセス規制は0時にリセットされますので、時間をおいてから再度ご利用ください。'"></Term>
            <Term :termTitle="'個人のアクセス制限'" :termDetail="'悪意のあるアクセスであると判断した場合、個人ユーザを対象にIPアドレス規制等の措置を講じることがあります。'"></Term>
        </ul>
    </div>
</template>

<style scoped>
.terms {
    max-width: 900px;
    margin:40px 30px;
    padding-bottom: 80px;
}

.terms-title {
    color: #f0f4f8;
}
</style>