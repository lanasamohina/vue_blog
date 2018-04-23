<template>
  <nav class="nav">
    <ul class="nav__list">
      
      <li class="nav__item" v-for="(item, key) in nav"
        :key="key"
      >
        <a :href="item.path" class="nav__link">{{ item.title }}</a>
      </li>

    </ul>
  </nav>
</template>

<script>
export default {
  data () {
    return {
      nav: [
        { title: 'Home', path: '/' },
        { title: 'Contacts', path: '/contacts' },
      ]
    }
  }
}
</script>

<style scoped>
  .nav__list {
    display: flex;
    margin: 0;
    padding: 0;
    list-style: none;
  }

  .nav__item:not(:last-child) {
    margin-right: 25px;
  }

  .nav__link {
    text-decoration: none;
    color: rgba(0, 0, 0, .87);
  }
</style>
