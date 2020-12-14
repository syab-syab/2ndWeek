<template>
  <div id="app">
    <Title msg="Easy Blog"/>
    <div class="row px-5">
      <div class="col-4 p-5 border-right editzone">
        <div class="form-group">
          <input v-model="BaseTitle" class="form-control" type="text" placeholder="タイトル">
          <textarea v-model="BaseContent" class="form-control" rows="4" placeholder="本文"></textarea>
          <button v-on:click="post" class="btn btn-dark">投稿</button>
        </div>      
        <div class="mt-5 previewbox">
          <p>プレビュー</p>
          <div class="preview p-3 border border-secondary">
            <p>{{ BaseTitle }}</p>
            <p>{{ BaseContent }}</p>
          </div>
        </div>
      </div>
      <div class="col-6 pt-5">
        <transition-group name="fade">
          <div v-for="item in articles" v-bind:key="item.id" class="border border-secondary mx-3 my-3 p-5">
            <p>{{ item.title }}</p>
            <p>{{ item.content }}</p>
          </div>
        </transition-group>
      </div>
    </div>
  </div>
</template>

<script>
import Title from './components/Title.vue'

export default {
  name: 'App',
  components: {
    Title
  },
  data() {
    return {
      BaseTitle: "",
      BaseContent: "",
      articles: [
      ],
      nextArticleId: 0
    }
  },
  methods: {
    post: function() {
      this.articles.push({
        id: this.nextArticleId++,
        title: this.BaseTitle,
        content: this.BaseContent
      })
      this.BaseTitle = ""
      this.BaseContent = ""
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.fade-enter {
  opacity: 0;
}

.fade-enter-to {
  opacity: 1;
}

.fade-enter-active {
  transition: all 1000ms;
}
</style>
