<script>
export default {
  name: "MoviesComponent",
  props: {
    data: Array,
  }
}
</script>

<template>
  <div class="container">
    <h1>영화정보</h1>
    <div v-for="(movie) in data" :key="movie.id" class ="item">
      <figure>
        <img :src="`${movie.imgUrl}`" :alt="movie.title">
      </figure>
      <div class="info">
        <h3 class="bg-yellow">{{ movie.title }}</h3>
        <p>개봉: {{ movie.year }}</p>
        <p>장르: {{ movie.category }}</p>
        <button @:click="$emit('increaseLike', movie.id)"> 좋아요 </button>
        <span>{{ movie.like }}</span>
        <p>
          <button @click="$emit('openModal', movie.id)"> 상세 보기 </button>
        </p>
      </div>
    </div>
  </div>
</template>

<style scoped>
  .container {
    padding: 20px;
  }

  .bg-yellow {
    background: gold;
    padding: 10px;
  }

  * {
    box-sizing: border-box;
    margin: 0;
  }

  h1, h2, h3 {
    margin-bottom: 1rem;
  }

  p {
    margin-bottom: 0.5rem;
  }

  button {
    margin-right: 10px;
    margin-top: 1rem;
  }

  .item {
    width: 100%;
    border: 1px solid #ccc;
    display: flex;
    margin-bottom: 20px;
    padding: 1rem;
  }

  .item figure {
    width: 30%;
    margin-right: 1rem;
  }

  .item img {
    width: 100%;
  }

  .item .info {
    width: 100%;
  }

  .modal {
    background: rgba(0, 0, 0, 0.7);
    position: fixed;
    left: 0;
    top: 0;
    width: 100%;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .modal .inner {
    background: #ffffff;
    width: 80%;
    padding: 20px;
    border-radius: 10px;
  }
</style>