<template>
  <div class="index">
    <kspaceBlogHeader />
    <div class="mainVisual">
      <img src="~assets/img/kspace-logo.png" alt="circle icon" />
    </div>
    <div class="index-recommend">
      <div class="index-recommend-title">
        <p>おすすめ記事</p>
      </div>
      <div v-for="elem in item" :key="elem.id">
        <recommend-article :recommend="elem" />
      </div>
    </div>
    <b-container>
      <div class="index-article-list-title">
        <p>記事一覧</p>
      </div>
      <b-row class="article-list">
        <b-col
          lg="4"
          md="6"
          sm="12"
          xs="12"
          v-for="elem in item"
          :key="elem.id"
          class="article-list"
        >
          <articleList :article="elem" />
        </b-col>
      </b-row>
    </b-container>
    <kspaceBlogFooter />
  </div>
</template>

<script>
import axios from "axios";
import kspaceBlogHeader from "@/components/kspaceBlogHeader.vue";
import kspaceBlogFooter from "@/components/kspaceBlogFooter.vue";
import RecommendArticle from "@/components/recommend-article.vue";
import articleList from "@/components/articleList.vue";

export default {
  async asyncData() {
    const { data } = await axios.get(
      "https://kspace-blog.microcms.io/api/v1/article?limit=99",
      {
        headers: { "X-API-KEY": process.env.API_KEY }
      }
    );
    return {
      item: data.contents
    };
  },
  components: {
    kspaceBlogHeader,
    RecommendArticle,
    articleList,
    kspaceBlogFooter
  }
};
</script>

<style>
.index {
  background-color: #f7f7f7;
}
.mainVisual {
  background-image: url("~assets/img/main-visual.jpg");
  height: 400px;
  background-size: cover;
  background-position: center;
  width: 100%;
  justify-content: center;
  display: flex;
  align-items: center;
}
.mainVisual img {
  width: 600px;
}
/*----------600px以下------------*/
@media screen and (max-width: 600px) {
  .mainVisual img {
    width: 400px;
  }
}
/*----------500px以下------------*/
@media screen and (max-width: 500px) {
  .mainVisual img {
    width: 320px;
  }
}
.index-recommend {
  margin-top: 50px;
}
.index-recommend-title {
  width: 150px;
  margin: 0 auto;
  border-bottom: solid 2px #707070;
  margin-bottom: 40px;
}
.index-recommend-title p {
  font-size: 1.5rem;
  color: #404040;
  font-weight: 700;
}
.index-article-list-title {
  width: 96px;
  margin: 0 auto 40px;
  border-bottom: solid 2px #707070;
}
.index-article-list-title p {
  font-size: 1.5rem;
  color: #404040;
  font-weight: 700;
}
</style>