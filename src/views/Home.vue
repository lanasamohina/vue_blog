<template>
  <div class="container">

    <!-- lessons -->
    <section class="lessons">
      <transition name="list">
        <span class="lessons__not-found" v-if="renderLessons.length === 0">Результат по запросу "{{myQuery}}" не найден</span>
      </transition>
      <transition-group name="list" tag="div">
        <article class="lessons__item" v-for="(lesson, key) in renderLessons" :key="key">
          <app-card :lessonData="lesson" />
        </article>
      </transition-group>


    </section> <!-- ./lessons -->

  </div>
</template>

<script>
import Card from '../components/Card.vue'
export default {
  props: {
    myQuery: {
      type: String,
      default: '',
    }
  },
  data () {
    return {
      lessons: [
        { title: 'First lesson', author: 'John Doe', descr: 'Some descr', start: '2018-04-21', end: '2018-05-21', id: 1 },
        { title: 'Second lesson', author: 'Alan Doe', descr: 'Some descr 2', start: '2018-04-21', end: '2018-05-21', id: 2 },
        { title: 'Third lesson', author: 'Chris Doe', descr: 'Some descr 3', start: '2018-04-21', end: '2018-05-21', id: 3 },
        { title: 'Fourth lesson', author: 'Andy Doe', descr: 'Some descr 4', start: '2018-04-21', end: '2018-05-21', id: 4 },
      ]
    }
  },
  computed: {
    renderLessons () {
      return this.lessons.filter(lesson => {
        return lesson.title.toLowerCase().indexOf(this.myQuery.toLowerCase()) > -1
      })
    }
  },
  components: {
    appCard: Card,
  }
}
</script>

<style scoped>
  .lessons {
    padding: 30px 0;
  }
  .lessons__item:not(:last-child) {
    margin-bottom: 15px;
  }
  .lessons__not-found{
    display: block;
    font-weight: 700;
    text-align: center;
  }

  .list-enter-active, .list-leave-active {
    transition: opacity .5s;
  }
  .list-enter, .list-leave-to{
    opacity: 0;
  }

</style>
