<template>
  <div class="chapter-header">
    <h1>{{chapterName}}</h1>
    <div class="chapter-header__button">
      <img src="@/assets/params.svg" />
    </div>
  </div>
</template>

<script>
export default {
  name: 'ChapterHeader',
  props: {
    chapterName: String,
  }
}
</script>

<style scoped>
h1 {
  margin: 0px 1rem;
  width: 100%;
  padding: 0px;
  user-select: none;
}

.chapter-header {
  height: 4rem;
  width: 100%;
  border-bottom: 2px solid #42A08F;
  display: inline-flex;
  margin-top: 1rem;
}

.chapter-header__button {
  margin-left: auto;
  margin-right: 1rem;
  user-select: none;
}
</style>
