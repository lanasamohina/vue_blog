<template>
  <div id="app">
    <app-header @searchQuery="onReadQuery"/>

    <main class="maincontent">
      <app-home :myQuery="query" />

    </main>

    <app-footer />
  </div>
</template>

<script>

import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
import Home from './views/Home.vue'

export default {
  name: 'app',
  data: () => ({
    query: '',
  }),
  methods: {
    onReadQuery (query) { this.query = query; }
  },
  components: {
    appHeader: Header,
    appFooter: Footer,
    appHome: Home,
  }
}
</script>

<style>
  * {
    box-sizing: border-box;
  }
  html, body, #app {
    width: 100%;
    min-height: 100vh;
    font-family: 'Open Sans', sans-serif;
    background: #f0f0f0;
  }

  body {
    margin: 0;
  }

  #app {
    display: flex;
    flex-flow: column nowrap;
  }

  .maincontent {
    fleX: 1 0;
  }

  .container {
    width: 1200px;
    margin: 0px auto;
  }
</style>
