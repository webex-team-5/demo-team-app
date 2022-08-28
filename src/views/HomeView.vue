<template>
  <h1>Home</h1>
  <div id="link">
    <div class="vue_quiz">
      <router-link to="quiz"
        ><img src="../image/quiz_img.png" v-on:mouseover="mouse"
      /></router-link>
      <h4>Vueクイズ</h4>
      <h4 v-bind:class="change">作成者：しゅん</h4>
    </div>

    <div class="vue_palette">
      <router-link to="palette"
        ><img src="../image/enogu_img.png" v-on:mouseover="mouse"
      /></router-link>
      <h4>Vueパレット</h4>
      <h4 v-bind:class="change">作成者：しょうちゃん</h4>
    </div>

    <div class="vue_memo">
      <router-link to="memo"
        ><img src="../image/memo_img.png" v-on:mouseover="mouse"
      /></router-link>
      <h4>Vueメモ</h4>
      <h4 v-bind:class="change">作成者：ゆい</h4>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      change: "before",
    }
  },
  methods: {
    mouse: function () {
      this.change = "after"
    },
  },
}
</script>
<style>
#link {
  display: flex;
  justify-content: space-around;
  margin-right: 40px;
  height: 400px;
}
.vue_quiz {
  width: 200px;
  height: 200px;
  display: flex;
  flex-direction: column;
  justify-items: center;
}
.vue_palette {
  width: 200px;
  height: 200px;
}
.vue_memo {
  width: 200px;
  height: 200px;
}
#link img {
  width: 100%;
  aspect-ratio: 1/1;
  background-color: rgb(215, 215, 215);
  border-radius: 250px;
}
h4 {
  text-align: center;
  margin-top: 20px;
  margin-bottom: 0px;
}
.before {
  opacity: 0;
}
.after {
  opacity: 1;
  transition: 1s;
}
</style>
