<template>
  <div class="memo-container">
    <!--イラスト左-->
    <div class="right">
      <div class="image1"><img src="../assets/irasutoya1.png" /></div>
      <div class="image2"><img src="../assets/irasutoya2.png" /></div>
    </div>
    <!--メモ-->
    <div class="memo-box">
      <div id="app" class="memo-list">
        <h1>Vueメモ</h1>
        <ul class="memo-list__container">
          <li v-for="(memo, index) in memos" v-bind:key="index" class="memo">
            <div class="memo__checkbox">
              <input type="checkbox" v-model="memo.isDone" />
            </div>
            <div v-if="memo.isDone" class="memo__text memo__text--done">
              {{ index }}:{{ memo.text }}
            </div>
            <div v-else class="memo__text">{{ index }}:{{ memo.text }}</div>
            <button v-on:click="deleteMemo(index)" class="memo__delete">
              削除
            </button>
          </li>
        </ul>
        <div class="add-memo-field">
          <input
            class="add-memo-field__input"
            type="text"
            v-model="inputMemo"
            placeholder="忘れないように書いておきましょう😊"
          />
          <button class="add-memo-field__button" v-on:click="addMemo">
            追加
          </button>
        </div>
      </div>
    </div>
    <!--イラスト右-->
    <div class="irasutoB">
      <div class="image3">
        <img src="../assets/irasutoya3.png" />
      </div>
      <div class="image4">
        <img src="../assets/irasutoya4.png" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      inputMemo: "",
      memos: [
        {
          text: "ひき肉を300g買う",
          isDone: false,
        },
        {
          text: "ホウレンソウを1束買う",
          isDone: false,
        },
        {
          text: "ピーマンを2個買う",
          isDone: false,
        },
      ],
    }
  },
  methods: {
    addMemo() {
      if (this.inputMemo !== "") {
        const memo = { text: this.inputMemo, isDone: false }
        this.memos.push(memo)
      }
    },
    deleteMemo(index) {
      this.memos.splice(index, 1)
    },
  },
}
</script>

<style scoped>
.memo-container {
  display: flex;
  justify-content: center;
}
.memo-container img {
  height: 200px;
}
.memo-list {
  padding-left: 5rem;
  padding-right: 5rem;
  display: flex;
  flex-direction: column;
  align-items: stretch;
  max-width: 512px;
  margin-left: auto;
  margin-right: auto;
}
.memo-list h1 {
  border-bottom: #a6bfa1 2px solid;
}
.memo-list__container {
  padding: 0;
}

.memo {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0.5rem;
  border-radius: 5px;
}

.memo:hover {
  color: white;
  background-color: #a6bfa1;
}

.memo__text {
  margin-left: 2rem;
  text-align: left;
}

.memo__text--done {
  text-decoration-line: line-through;
}

.memo__delete {
  margin-left: 1rem;
  padding: 0.5rem 0.5rem;
  border: solid 1px black;
  border-radius: 5px;
  background-color: white;
}

.memo__delete:hover {
  background-color: #6abe83;
  border-radius: 5px;
}

.add-memo-field {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.add-memo-field__input {
  padding: 10px;
}
.add-memo-field__button {
  padding: 0.5rem 0.5rem;
  border: solid 1px black;
  border-radius: 5px;
  background-color: white;
}

.add-memo-field__button:hover {
  background-color: #f1ac9d;
  border-radius: 5px;
}
</style>
