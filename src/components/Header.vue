<template>
  <header class="header">
    <div class="container">
      <!-- search -->
      <form class="header__search" @submit.prevent="onSearchSubmit">
        <input type="text" class="header__search-textfield"
          v-model="query"
          placeholder="Turn lesson name"
          :class="{ 'header__search-textfield--invalid': invalid }"
          :maxlength="max"
        >
        <transition name="fade">
          <span class="invalid" v-if="invalid === true">{{invalidMessage}}</span>
        </transition>

        <button class="header__search-submit">
          <i class="material-icons">search</i>
        </button>
        <button class="header__search-clear"
                v-on:click.prevent="onSearchClear">
          <i class="material-icons">close</i>
        </button>

        <span class="header__search-max">{{count}} / {{max}}</span>
      </form> <!-- ./search -->

      <app-nav />
    </div>

  </header>
</template>

<script>
import Nav from './Nav.vue'
export default {
  data () {
    return {
      query: '',
      invalidMessage: '',
      invalid: false,
      max: 25,
    }
  },
  methods: {
    onSearchSubmit () {
      if (this.query.length === 0) {
        this.invalid = true;
        this.invalidMessage = 'Пустое поле ввода'
      } else {
        this.$emit('searchQuery', this.query);
      }
    },
    onSearchClear(){
      this.query = '';
      this.$emit('searchQuery', this.query);
    }
  },
  watch: {
    query () {
      if (this.query.length > 0 && this.invalid === true) {
        this.invalid = false;
        this.invalidMessage = '';
      }
    }
  },
  components: {
    appNav: Nav,
  },
  computed:{
    count: function () {
      return this.query.length;
    }
  }
}
</script>

<style scoped>
  .header {
    background: #fff;
    border-bottom: 1px solid rgba(0, 0, 0, .1);
    box-shadow: 0 5px 5px rgba(0, 0, 0, .07);
    padding: 25px 0;
  }

  .container {
    display: flex;
    justify-content: space-between;
  }

  .header__search {
    display: flex;
    align-items: center;
    position: relative;
    flex-flow: row wrap;
  }

  .header__search-textfield {
    border: none;
    outline: none;
    border-bottom: 1px solid rgba(0, 0, 0, .5);
    font-size: 16px;
  }

  .header__search-textfield--invalid {
    border-bottom-color: red;
  }

  .header__search-submit, .header__search-clear {
    background: none;
    border: none;
    outline: none;
    display: flex;
    align-items: center;
    justify-content: center;
    line-height: 1;
    padding: 0;
    cursor: pointer;
  }
  .header__search-submit > i {
    font-size: 18px;
  }

  .invalid {
    position: absolute;
    color: red;
    left: 0;
    bottom: -15px;
    font-size: 13px;
  }

  .header__search-clear{
    font-size: 18px;

  }

  .fade-enter-active, .fade-leave-active {
    transition: opacity .5s;
  }
  .fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
    opacity: 0;
  }

  .header__search-max{
    display: flex;
    width: 100%;
    font-size: 13px;
    margin-bottom: 5px;
    color: rgba(0, 0, 0, .5);
  }

</style>
