<template>
  <div class="container">
    <img src="https://res.cloudinary.com/kyart2036/image/upload/v1658683970/ns-banner_cnpuhr.png"/>

    <h1 class="title">
      記事リスト
    </h1>
    <ul>
      <li v-for="content in contents" :key="content.id">
        <nuxt-link :to="`/${content.id}`">
          {{ content.title }}
        </nuxt-link>
      </li>
    </ul>
  </div>

</template>

<script>
import axios from 'axios'

export default {
  layout:'articles',
  async asyncData({ params }) {
    const { data } = await axios.get(
      'https://northernscript.microcms.io/api/v1/blogs',
      {
        headers: { 'X-MICROCMS-API-KEY': '4c68f961f7d64e24b25d0f09b342632dbf79' }
      }
    )
    return data
  }
}
</script>

<style lang="scss" scoped>
.main {
  width: 960px;
  margin: 0 auto;
}
.title {
  margin-bottom: 20px;
}

.publishedAt {
  margin-bottom: 40px;
}

.post ::v-deep {
  & > h1 {
    font-size: 30px;
    font-weight: bold;
    margin: 40px 0 20px;
    background-color: #eee;
    padding: 10px 20px;
    border-radius: 5px;
  }

  & > h2 {
    font-size: 24px;
    font-weight: bold;
    margin: 40px 0 16px;
    border-bottom: 1px solid #ddd;
  }

  & > p {
    line-height: 1.8;
    letter-spacing: 0.2px;
  }

  & > ol {
    list-style-type: decimal;
    list-style-position: inside;
  }
}
</style>
