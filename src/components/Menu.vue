<template>
  <div class="ui secondary pointing green inverted massive menu" v-if="isMenuNeeded">
    <!-- 基本的なコンテンツはここに記載する -->
    <div class="ui" id="logo">
      GoldSteps
    </div>
    <router-link active-class="active" class="item" exact to="/">ホーム</router-link>
    <router-link active-class="active" class="item" to="/article">投稿</router-link>
    <router-link active-class="active" class="item" to="/profile">プロフィール</router-link>
    <div class="right menu">
      <a @click="logout" class="item">ログアウト</a>
    </div>
  </div>
</template>

<script>
  // 必要なものはここでインポートする
  // @は/srcと同じ意味です
  // import something from '@/components/something.vue';

  export default {
    name: 'Menu',

    components: {
      // 読み込んだコンポーネント名をここに記述する
    },

    data() {
      // Vue.jsで使う変数はここに記述する
      return {};
    },

    computed: {
      // 計算した結果を変数として利用したいときはここに記述する
      isMenuNeeded() {
        const excludedRoutes = ['Login', 'Welcome']; // メニューを表示しないページのルート名
        return !excludedRoutes.includes(this.$route.name);
      }

    },

    methods: {
      // Vue.jsで使う関数はここで記述する
      logout() {
        window.localStorage.clear();
        this.$router.push({ name: 'Login' });
      }
    },
  }
</script>

<style scoped>
  /* このコンポーネントだけに適用するCSSはここに記述する */
  #logo {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 20px;
    color: white;
    font-weight: bold;
    font-size: 40px;
    margin: 0 40px 0 20px;
  }
</style>
