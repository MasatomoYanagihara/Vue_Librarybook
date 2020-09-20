<template>
  <div class="root">
    <div class="serch_wrapper">
      <h3>タイトルを検索</h3>
      <input type="text" v-model="serchTitle" /><button @click="serchBooks">
        検索
      </button>
    </div>

    <ul v-for="item in items" :key="item.Item.title">
      <div class="wrapper_1">
        <div class="img_wrapper">
          <img :src="item.Item.mediumImageUrl" />
        </div>
        <div>
          <li>
            タイトル：<br />
            {{ item.Item.title }}<br />
          </li>
          <li>著者：<br />{{ item.Item.author }}</li>
        </div>
      </div>
    </ul>
  </div>
</template>

<script>
import axios from "axios";
// @ is an alias to /src

export default {
  name: "Home",
  data() {
    return {
      items: [],
      serchTitle: "",
    };
  },
  methods: {
    serchBooks() {
      axios
        .get(
          "https://app.rakuten.co.jp/services/api/BooksBook/Search/20170404?format=json&アプリID&title=" +
            this.serchTitle
        )
        .then((response) => {
          console.log(response.data.Items);
          this.items = response.data.Items;
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>

<style scoped lang="scss">
.root {
  background-color: rgb(244, 244, 244);
}
.serch_wrapper {
  text-align: center;
}
ul {
  list-style: none;
}
.wrapper_1 {
  width: 96%;
  display: flex;
  margin-top: 6%;
  padding-top: 6%;
  border-top: 1px solid gray;
  /* background-color: gray; */
  
  img {
    width: 120px;
  }

  li {
    padding-left: 4%;
    padding-top: 4%;
  }
}
</style>
