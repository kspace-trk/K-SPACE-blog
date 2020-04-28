<template>
  <div class="contents">
    <kspaceBlogHeader />
    <div class="contents-wrapper">
      <contents :contents="item" />
    </div>
    <kspaceBlogFooter />
  </div>
</template>

<script>
import axios from "axios";
import kspaceBlogHeader from "@/components/kspaceBlogHeader.vue";
import kspaceBlogFooter from "@/components/kspaceBlogFooter.vue";
import contents from "@/components/contents.vue";
export default {
  data() {
    return {
      item: []
    };
  },
  async asyncData({ params }) {
    const { data } = await axios.get(
      `https://kspace-blog.microcms.io/api/v1/article/${params.id}`,
      {
        headers: { "X-API-KEY": process.env.API_KEY }
      }
    );
    return {
      item: data
    };
  },
  components: {
    kspaceBlogHeader,
    contents,
    kspaceBlogFooter
  }
};
</script>

<style>
.contents {
  background-image: url("~@/assets/img/article-background.jpg");
  background-size: cover;
  background-attachment: fixed;
}
.contents-wrapper {
  max-width: 1000px;
  border-radius: 20px;
  margin: 50px auto;
  width: 90%;
  background-color: #ffffff;
  padding: 5px 0 20px 0;
}
/*----------767px以下------------*/
@media screen and (max-width: 767px) {
  .contents-wrapper {
    border-radius: 20px;
    margin: 10px auto;
    width: 95%;
    background-color: #ffffff;
    padding: 10px 10px 5px;
  }
}
</style>

