<!--자바 스크립트 코드가 들어감-->
<script>
import data from './assets/movies.js';
import Navbar from "@/components/Navbar.vue";
import Modal from "@/components/Modal.vue";
import Event from "@/components/Event.vue";
import Movies from "@/components/Movies.vue";
import SearchBar from "@/components/SearchBar.vue";

export default {
  name: 'App',
  data() {
    return {
      isModal: false,
      data: data,
      // 원래 있던 데이터를 복사해오는 것/ data_temp = data의 사본
      data_temp: [...data],
      selectedMovie: 0,
      text: [
          'NETFLIX 강렬한 운명의 드라마, 재홍크리처',
          '디즈니 100주년 기념작, 재홍몬',
          '그날, 대한민국의 운명은 바뀌었다, 재홍의 봄'
      ],
      eventTextNum: 0,
      interval: null,
    }
  },
  methods: {
    increaseLike(id) {
      this.data.find(movie => {
        if(movie.id == id){
          movie.like += 1;
        }
      })
    },
    searchMovie(title) {
    //   영화제목이 포함된 데이터를 가져옴
      this.data_temp = this.data.filter(movie => {
        return movie.title.includes(title);
      })
    },
    showAllMovies() {
      this.data_temp = [...this.data];
    }
  },
  components: {
    Navbar: Navbar,
    Modal: Modal,
    Event: Event,
    Movies: Movies,
    SearchBar: SearchBar,
  },
  mounted() {
    //일정 시간 뒤 메서드를 수행하는 비동기 메서드 setTimeOut()
    // setTimeout(() =>{
    //   this.eventTextNum += 1;
    // }, 3000);
    this.interval = setInterval(()=> {
      if(this.eventTextNum == this.text.length -1) {
        this.eventTextNum = 0;
      }
      else {
        this.eventTextNum += 1;
      }
    }, 3000);
  },

  unmounted() {
    clearInterval(this.interval);
  }
}
</script>

<!--HTML 코드가 들어감-->
<template>
  <Navbar />
  <Event :text="text[eventTextNum]" />
  <SearchBar :data="data_temp" @searchMovie="searchMovie($event)"/>
  <p>
    <button @click="showAllMovies"> 전체보기 </button>
  </p>
  <Movies
      :data="data_temp"
      @openModal = "isModal = true; selectedMovie=$event"
      @increaseLike="increaseLike($event)"
  />
  <Modal :data="data"
         :isModal="isModal"
         :selectedMovie="selectedMovie"
         @closeModal="isModal = false"
  />
</template>

<!--CSS 코드가 들어감-->
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
