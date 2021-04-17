<template>
  <div class="slider-container">
    <Slick
      ref="slick"
      :options="slickOptions"
      @beforeChange="handleBeforeChange"
      @init="handleInit"
    >
      <div class="slider">
        <div class="slider-inner">
          <div class="slide">
            <img
              class="slide-image"
              src="@/assets/images/car1.jpg"
              alt="car1"
              title="car1"
            />
            <div class="slide-info">
              <h1 class="slide-title">Авто в лизинг для физических лиц</h1>
              <p class="slide-description">Получите машину за 5 дней</p>
              <button class="btn" @click="$emit('toggleForm')">
                Оставить заявку
              </button>
            </div>
          </div>
        </div>
      </div>
      <div class="slider">
        <div class="slider-inner">
          <div class="slide">
            <img
              class="slide-image"
              src="@/assets/images/car2.jpg"
              alt="car2"
              title="car2"
            />
            <div class="slide-info">
              <div class="slide-title">
                Авто в лизинг для личного пользования
              </div>
              <p class="slide-description">Получите машину за 5 дней</p>
              <button class="btn-disabled">
                Оставить заявку
              </button>
            </div>
          </div>
        </div>
      </div>
      <div class="slider">
        <div class="slider-inner">
          <div class="slide">
            <img
              class="slide-image"
              src="@/assets/images/car3.jpg"
              alt="car3"
              title="car3"
            />
            <div class="slide-info">
              <div class="slide-title">Авто в лизинг для физических лиц</div>
              <p class="slide-description">Получите машину за 5 дней</p>
              <button class="btn" @click="$emit('toggleForm')">
                Оставить заявку
              </button>
            </div>
          </div>
        </div>
      </div>
      <div class="slider">
        <div class="slider-inner">
          <div class="slide">
            <img
              class="slide-image"
              src="@/assets/images/car4.jpg"
              alt="car4"
              title="car4"
            />
            <div class="slide-info">
              <div class="slide-title">Авто в лизинг для физических лиц</div>
              <p class="slide-description">Получите машину за 5 дней</p>
              <button class="btn" @click="$emit('toggleForm')">
                Оставить заявку
              </button>
            </div>
          </div>
        </div>
      </div>
      <div class="slider">
        <div class="slider-inner">
          <div class="slide">
            <img
              class="slide-image"
              src="@/assets/images/car5.jpg"
              alt="car5"
              title="car5"
            />
            <div class="slide-info">
              <div class="slide-title">Авто в лизинг для физических лиц</div>
              <p class="slide-description">Получите машину за 5 дней</p>
              <button class="btn" @click="$emit('toggleForm')">
                Оставить заявку
              </button>
            </div>
          </div>
        </div>
      </div>
      <div class="slider">
        <div class="slider-inner">
          <div class="slide">
            <img
              class="slide-image"
              src="@/assets/images/car6.jpg"
              alt="car6"
              title="car6"
            />
            <div class="slide-info">
              <div class="slide-title">Авто в лизинг для физических лиц</div>
              <p class="slide-description">Получите машину за 5 дней</p>
              <button class="btn" @click="$emit('toggleForm')">
                Оставить заявку
              </button>
            </div>
          </div>
        </div>
      </div>
    </Slick>

    <div class="arrow-left"></div>
  </div>
</template>

// <Slick
//       ref="slick"
//       :options="slickOptions"
//       @beforeChange="handleBeforeChange"
//       @init="handleInit"
//     >
//       <div
//         class="slider"
//         v-for="currentSlide in slides"
//         :key="currentSlide.image"
//       >
//         <div
//           :style="{
//             backgroundColor: '#000',
//             borderRadius: '32px',
//             maxWidth: '1375px',
//             height: '475px',
//             margin: '0 auto',
//           }"
//         >
//           <div class="slide">
//             <img
//               class="slide-image"
//               :src="require(`@/assets/images/${currentSlide.image}`)"
//             />
//             <div class="slide-info">
//               <h2 class="slide-title">{{ currentSlide.title }}</h2>
//               <p class="slide-description">{{ currentSlide.description }}</p>
//               <button class="btn" @click="$emit('toggleForm')">
//                 Оставить заявку
//               </button>
//             </div>
//           </div>
//         </div>
//       </div>

<script>
import Slick from "vue-slick";

export default {
  components: { Slick },
  methods: {
    handleBeforeChange() {
      document.querySelector(
        ".slick-next.slick-arrow"
      ).innerHTML = `<div class="arrow-right"></div>
      <svg class="progress-svg" width="60" height="60">
		<g transform="translate(24, 25)">
      <circle class="circle-go" r="24" cx="0" cy="0"></circle>
		</g>
    </svg>`;
    },
    handleInit() {
      this.handleBeforeChange();
    },
  },

  data() {
    return {
      slickOptions: {
        lazyLoad: "ondemand",
        dots: true,
        fade: true,
        infinite: true,
        speed: 500,
        slidesToShow: 1,
        slidesToScroll: 1,
        autoplay: true,
        autoplaySpeed: 10000,
        pauseOnFocus: false,
      },

      slides: [
        {
          image: "car1.jpg",
          title: "Авто в лизинг для физических лиц",
          description: "Получите машину за 5 дней",
        },
        {
          image: "car2.jpg",
          title: "Авто в лизинг для физических лиц",
          description: "Получите машину за 5 дней",
        },
        {
          image: "car3.jpg",
          title: "Авто в лизинг для физических лиц",
          description: "Получите машину за 5 дней",
        },
        {
          image: "car4.jpg",
          title: "Авто в лизинг для физических лиц",
          description: "Получите машину за 5 дней",
        },
        {
          image: "car5.jpg",
          title: "Авто в лизинг для физических лиц",
          description: "Получите машину за 5 дней",
        },
        {
          image: "car6.jpg",
          title: "Авто в лизинг для физических лиц",
          description: "Получите машину за 5 дней",
        },
      ],
      timer: null,
      currentIndex: 0,
    };
  },
};
</script>

<style >
@keyframes progress {
  from {
    stroke-dashoffset: 360;
  }

  to {
    stroke-dashoffset: 0;
  }
}
.slider-inner {
  background-color: #000;
  border-radius: 32px;
  max-width: 1375px;
  height: 475px;
  margin: 0 auto;
}
.circle-go {
  fill: rgba(255, 255, 255, 0);
  stroke: rgb(255, 255, 255);
  stroke-width: 2;
  stroke-linecap: round;
  animation: progress 40s;
  stroke-dasharray: 360px;
  stroke-dashoffset: 360;
  z-index: 1001;
}
.slick-next.slick-arrow {
  position: absolute;
  bottom: 42px;
  right: 6.5%;
  z-index: 1001;
  background: none;
  padding: 0;
  height: 52px;
  width: 52px;
  border-color: transparent;
  border-radius: 50%;
}
.slick-next.slick-arrow::before {
  content: "";
  display: block;
  position: absolute;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  z-index: 1001;
  border: 2px solid rgba(168, 163, 163, 0.2);
  border-radius: 50%;
}
.slick-next.slick-arrow:hover {
  background-color: rgb(95, 95, 95);
  z-index: 999;
}

.slick-prev.slick-arrow {
  position: absolute;
  bottom: 55px;
  right: 11%;
  z-index: 1001;
  width: 24px;
  height: 24px;
  background: none;
  border: 2px solid rgba(168, 163, 163, 0.2);
  border-radius: 50%;
  font-size: 0;
}

.slick-track {
  display: flex;
}
.slick-list {
  overflow: hidden;
}
.slick-slider {
  position: relative;
}
.slick-dots {
  position: absolute;
  bottom: 40px;
  left: 43%;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1000;
}
.slick-dots li {
  list-style: none;
  margin: 0px 10px;
}
.slick-dots button {
  font-size: 0px;
  width: 10px;
  height: 10px;
  padding: 3px;
  background: #8f8888;
  border: none;
  border-radius: 50%;
}
.slick-dots li.slick-active button {
  font-size: 0px;
  padding: 6px;
  background: #f0e8e8;
  border: none;
  border-radius: 50%;
}
.arrow-left {
  position: absolute;
  right: 11.3%;
  bottom: 62px;
  height: 10px;
  width: 10px;
  border-top: 2px solid #fff;
  border-left: 2px solid #fff;
  transform: rotate(315deg);
  cursor: pointer;
  z-index: 1000;
}
.arrow-right {
  position: absolute;
  bottom: 115px;
  right: 35%;
  top: 15px;
  height: 20px;
  width: 20px;
  border-top: 2px solid #fff;
  border-right: 2px solid #fff;
  transform: rotate(45deg);
  cursor: pointer;
  z-index: 1000;
}
.slider-container {
  position: relative;
  margin: 90px auto;
}
.slider {
  position: relative;
  display: block;
}
.slide {
  position: relative;
  max-width: 1345px;
  color: #fff;
  font-family: Nekst-Black;
}
.slide-image {
  position: absolute;
  right: 0px;
  top: 0;
  bottom: 0px;
  left: 500px;
  max-width: 840px;
}
.slide-info {
  position: relative;
  height: 240px;
  width: 585px;
  padding: 50px 0 0 70px;
  font-weight: 900;
  z-index: 1100;
}
.slide-title {
  font-size: 54px;
  font-weight: 900;
  line-height: 48px;
  padding: 12px 0;
}
.slide-description {
  padding: 24px 0;
  font-size: 30px;
  font-weight: 900;
  line-height: 26px;
}
.btn {
  position: relative;
  height: 48px;
  padding: 12px 24px;
  background: #ff9514;
  border: solid 1px #ff9514;
  border-radius: 40px;
  font-family: Gilroy-regular;
  font-size: 16px;
  font-weight: 700;
  line-height: 100%;
  color: #fff;
  cursor: pointer;
  z-index: 1100
}
.btn:active {
  background-color: #575757;
}
.btn-disabled {
  height: 48px;
  padding: 12px 24px;
  border: solid 1px #ff9514;
  border-radius: 40px;
  font-family: Gilroy-regular;
  font-size: 16px;
  font-weight: 700;
  line-height: 100%;
  color: #fff;
  cursor: pointer;
  background: rgba(255, 149, 20, 0.4);
}

@media (max-width: 1439px) {
  .arrow-left {
    right: 14%;
    bottom: 62px;
  }
  .arrow-right {
    right: 35%;
  }
  .slick-prev.slick-arrow {
    right: 13.5%;
  }
  .slick-dots {
    left: 40%;
  }
  .slide-image {
    max-width: 675px;
    top: 75px;
    bottom: 19px;
    left: 250px;
  }
}
@media (max-width: 1023px) {
  .circle-go {
    display: none;
  }
  .slick-next.slick-arrow {
    display: none;
  }
  .slick-next.slick-arrow::before {
    display: none;
  }
  .slick-prev.slick-arrow {
    border: none;
  }
  .arrow-left {
    display: none;
  }
  .arrow-right {
    display: none;
  }
  .slick-dots {
    left: 37%;
  }
  .slide-description {
    display: none;
  }
  .slide-title {
    padding: 32px 0;
  }
  .slide-info {
    padding: 185px 0 0 70px;
  }
  .btn {
    width: 175px;
    height: 48px;
  }
  .slide-image {
    max-width: 570px;
    top: -70px;
    bottom: 214px;
    left: 76px;
    right: 46px;
  }
}
@media (max-width: 767px) {
  .slick-dots {
    left: 20%;
  }
  .slide-info {
    padding: 200px 0 0 20px;
  }
  .slide-title {
    max-width: 260px;
    height: 85px;
    font-size: 32px;
    font-weight: 900;
    line-height: 28px;
    padding: 12px 0;
  }
  .btn {
    margin-top: 40px;
  }
  .slide-image {
    max-width: 460px;
    top: 0px;
    bottom: 285px;
    left: -125px;
    right: 17px;
  }
}
</style>