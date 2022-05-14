<template>
  <div class="container">
    <section class="section">
      <h1 class="title">エラー発生</h1>
      <div>HTTPステータスコード：{{ error.statusCode }}</div>
      <div>エラーメッセージ：{{ error.message }}</div>
    </section>
  </div>

</template>

<script>
export default {
  name: "error",
  props: {
    error: {
      type: Object,
      default: null
    }
  }
}
</script>

<style scoped>

</style>
