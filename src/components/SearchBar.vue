<script>
  export default {
    name: 'SearchBarComponent',
    data() {
      return {
        inputText: '',
      }
    },
    props: {
      data: Array,
    },
    watch: {
      inputText(name) {
      //   입력한 영화제목이 데이터에 있는지 확인
      //   이전 값을 확인할 수도 있음
        const findName = this.data.filter(movie => {
          return movie.title.includes(name);
        });
        if(findName.length == 0) {
          alert('해당하는 자료가 없습니다.');
        }
      }
    }
  }
</script>

<!--   @input="inputText = $event.target.value"를
        v-model="inputText"로 대체할 수 있음-->
<template>
  <div class="search-box">
    <input
        type="search"
        @change="
          $emit('searchMovie', $event.target.value)
          inputText = $event.target.value;
          $event.target.value = '';
        "
        placeholder="검색어 입력"
    >
    <button> 검색 </button>
  </div>
  <p>{{ inputText }}</p>
</template>

<style scoped>
  .search-box {
    padding: 10px;
    display: flex;
    justify-content: center;
  }

  .search-box input {
    padding: 5px 10px;
  }

  .search-box button {
    margin: 0;
  }

</style>