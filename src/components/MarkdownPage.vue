<template>
    <div class="page">
        <div v-if="page">
            <!-- <label for="title">Title</label>-->
            <input type="text" v-model="page.title" class="title" name="title" placeholder="Enter a title" />
            <div class="actions">
                <!-- <label for="content">Content</label> -->
                <button v-if="active" @click="toggleMarkdown()">Render Markdown</button>
                <button v-if="!active" @click="toggleMarkdown()">&nbsp;Write Markdown&nbsp;</button>
                <button @click="deletePage()">Delete Page</button>
                <button @click="savePage()">Save Page</button>
            </div>
            <div class="content-container">
                <textarea v-if="active" class="content" name="content" v-model="page.content" placeholder="Enter some content">

                </textarea>
                <vue-markdown v-if="!active" class="rendered-content" :source="page.content"></vue-markdown>
            </div>
        </div>
        <div v-else>
            <h1>&larr; To start, create a new page!</h1>
        </div>
    </div>
    </div>
</template>
<script>
import VueMarkdown from 'vue-markdown'
export default {
  name: 'MarkdownPage',
  components: {
    VueMarkdown
  },
  data: () => ({
    active: true
  }),
  props: ['page'],
  methods: {
    deletePage () {
      this.$emit('delete-page')
    },
    savePage () {
      this.$emit('save-page')
    },
    toggleMarkdown () {
      this.active = !this.active;
    }
  }
}
</script>

<style scoped>
    .page {
        display: flex;
        flex-flow: column;
        -webkit-flex-direction: column; /* Safari */
        flex-direction: column;
        height: 100%;
        width: 100%;
        padding: 2rem;
        overflow: auto;
    }
    .content, .title {
        border-style: none;
        border: none;
    }
    .content:focus, .title:focus {
        outline: 0;
    } 
    .title {
        font-size: 2rem;
        padding: 0.5rem 1rem;
        width: 100%;
        flex: 0 1 auto;
    }
    .actions{
        flex: 1 1 auto;
        width: 100%;
        padding:10px 0 10px 0;
    }
    .content-container{
        display: relative;
        flex: 2 1 auto;
        padding: 10px
    }
    .content {
      display: inline-table;
      resize: vertical; 
      outline: none;
      width: 100%;
      padding: 10px;
      border: none;
      height: 100%;
      margin: -10px;
    }

    label {
        margin-bottom: 0.5rem;
        display: inline-block;
    }

    button {
        border: #4C5456 2px solid;
        padding: 0.5rem 0.75rem;
        background-color: transparent;
        margin-right: 1rem;
        border-radius: 0.25rem;
        color: #4C5456;
        font-size: 1rem;
        cursor: pointer;
    }

    button:hover {
    }
</style>
