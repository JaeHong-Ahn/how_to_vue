<script>
  export default {
    name: "ModalComponent",
    props: {
      data: Array,
      isModal: Boolean,
      selectedMovie: Number,
    }
  }

</script>

<template>
  <div class="modal" v-if="isModal">
    <div class="inner">
      <h3>{{data[selectedMovie].title}}</h3>
      <p>영화 상세정보</p>
      <button @click="$emit('closeModal')"> 닫기 </button>
    </div>
  </div>
</template>

<style scoped>
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