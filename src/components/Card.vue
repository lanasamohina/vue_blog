
  <template>
    <a href="#" class="card">
      <h3 class="card__title">{{ lessonData.title }}</h3>
      <span class="card__author">{{ lessonData.author }}</span>
      <p class="card__descr">{{ lessonData.descr }}</p>

      <div class="card__date">
        <time class="card__date-item" datetime="2018-04-21">Start: {{ lessonData.start }}</time>
        <time class="card__date-item" datetime="2018-05-21">End: {{ lessonData.end }}</time>
      </div>
    </a>
  </template>

<script>
export default {
  props: ['lessonData'],
}
</script>

<style scoped>
  .card {
    display: block;
    background: #fff;
    padding: 25px 15px;
    color: rgba(0, 0, 0, .87);
    text-decoration: none;
    box-shadow: 0 5px 5px rgba(0, 0, 0, .08);
    transition: box-shadow .2s ease-out;
  }

  .card:hover {
    box-shadow: 0 10px 15px rgba(0, 0, 0, .1);
  }

  .card__title {
    margin: 0 0 5px 0;
    font-size: 30px;
  }

  .card__descr {
    margin: 30px 0 0 0;
    font-size: 14px;
  }

  .card__date {
    margin-top: 40px;
    font-size: 14px;
    color: blue;
    display: flex;
    flex-flow: column nowrap;
    line-height: 1.8;
  }

</style>
