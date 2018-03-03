<template>
 <div id="app">
        <Notebook @change-page="changePage" @new-page="newPage" :pages="pages" :activePage="index" />
        <MarkdownPage @save-page="savePage" @delete-page="deletePage" :page="pages[index]" />
    </div>
</template>

<script>
import Notebook from './components/Notebook'
import MarkdownPage from './components/MarkdownPage'

export default {
  name: 'app',
  components: {
    Notebook,
    MarkdownPage
  },
  data: () => ({
    pages: [],
    index: 0
  }),
  methods: {
    newPage () {
      this.pages.push({
        title: '',
        content: ''
      })
      this.index = this.pages.length - 1
    },
    changePage (index) {
      this.index = index
    },
    savePage () {
      // nothing as of yet
    },
    deletePage () {
      this.pages.splice(this.index, 1)
      this.index = Math.max(this.index - 1, 0)
    }
  }
}
</script>

<style>
    html, body, #app {
        height: 100%;
        overflow: hidden;
    }

    body {
        margin: 0;
    }

    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        display: flex;
        flex-direction: row;
    }
    </style>
  
