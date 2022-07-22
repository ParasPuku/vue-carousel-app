<template>
  <header>
    <div class="title">
      <p>Carousel in VUE</p>
    </div>
    <div class="next-prev-btn">
      <div class="next">
        <span class="nextBtn" v-on:click="scrollLeftCards()"></span>
      </div>
      <div class="prev">
        <span class="prevBtn" v-on:click="scrollRightCards()"></span>
      </div>
    </div>
  </header>
  <div class="carousel-wrapper">
    <div class="carousel-container" v-for="datas in carouselData" :key="datas._id">
      <div class="carousels" v-for="data in datas" :key="data._id">
        <div class="carousel">
          <div class="top-section">
            <img :src="`${data.image}`" class="image" :alt="`${data.name}`" />
          </div>
          <div class="midlle-section">
            <p>{{data.name}}</p>
          </div>
          <div class="last-section">
            <p>
              {{data.description}}
            </p>
            <button class="more-info" v-on:click="openPopUp">
              {{data.more}}
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import data from './assets/data.json'
  export default {
    name: 'Carousel',
    data() {
      return {
        carouselData: data,
      }
    },
    methods: {
      scrollLeftCards(e) {
        const carouselContainer = document.querySelector('.carousel-container');
        const nextBtn = document.querySelector('.nextBtn');
        const prevBtn = document.querySelector('.prevBtn');

        carouselContainer.scrollLeft += 320;
        prevBtn.parentElement.classList.add('leftBtnActive')
        if(carouselContainer.scrollLeft > 1050) {
          nextBtn.parentElement.classList.add('rightBtnActive')
        }
      },
      scrollRightCards(e) {
        const carouselContainer = document.querySelector('.carousel-container');
        const nextBtn = document.querySelector('.nextBtn');
        const prevBtn = document.querySelector('.prevBtn');

        carouselContainer.scrollLeft -= 320;
        nextBtn.parentElement.classList.remove('rightBtnActive')
        if(carouselContainer.scrollLeft <= 0) {
          prevBtn.parentElement.classList.remove('leftBtnActive')
        }
      }
    }
  }
</script>

<style>
@import "./assets/base.css";
html {
  scroll-behavior: smooth;
}
.carousels {
  min-width: 350px;
  width: 100%;
  border: 5px solid #333333;
  border-radius: 10px 10px 10px 10px;
  margin: 0 5px;
  transition: all 0.5s ease; 
}
header {
  line-height: 1.5;
  display: flex;
  justify-content: space-between;
  margin: 0 40px;
}
.carousel-container {
  display: flex;
  overflow: auto;
  padding: 0 30px;
  scroll-behavior: smooth;
}
.carousel {
  padding: 10px;
}
.midlle-section p {
  font-weight: bold;
  font-size: 18px;
  margin: 10px 0;
}
.more-info {
  margin: 20px 0 10px;
  border: 3px solid #00ac23;
  font-size: 16px;
  background-color: #646464;
  padding: 7px 10px;
  cursor: pointer;
  color: #ffffff;
  border-radius: 3px;
}
.image {
  max-width: 350px;
  width: 100%;
  height: 250px;
  border-radius: 10px 10px 0 0;
}
.title p {
  font-size: 30px;
  letter-spacing: 3px;
  margin: 0 auto 10px;
  text-align: center;
}
.next.rightBtnActive {
  background-color: #cd0000;
}
.next {
  background-color: #186504;
  padding: 5px 10px;
  margin-right: 5px;
  cursor: pointer;
  border-radius: 10px;
  margin-bottom: 10px;
}
.next span {
  background-image: url(/src/assets/images/right.png);
  min-width: 40px;
  height: 40px;
  display: block;
  background-repeat: no-repeat;
  position: relative;
  background-size: cover;
}
.prev span {
  background-image: url("./assets/images/left.png");
  width: 40px;
  height: 40px;
  display: block;
  background-repeat: no-repeat;
  background-size: cover;
}
.prev.leftBtnActive {
  background-color: #186504;
}
.prev {
  background-color: #cd0000;
  padding: 5px 10px;
  cursor: pointer;
  border-radius: 10px;
  margin-bottom: 10px;
}
.next-prev-btn {
  display: flex;
  justify-content: center;
  align-items: center;
}
::-webkit-scrollbar {
  display: none;
}
.last-section p {
  font-size: 14px;
  color: #727272;
}
#app {
  max-width: 1280px;
  padding: 12px 0;
  font-weight: normal;
}

header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

a,
.green {
  text-decoration: none;
  color: hsla(160, 100%, 37%, 1);
  transition: 0.4s;
}

@media (hover: hover) {
  a:hover {
    background-color: hsla(160, 100%, 37%, 0.2);
  }
}

@media (min-width: 1024px) {
  body {
    display: flex;
    place-items: center;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
