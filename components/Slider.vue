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
  </div>
</template>

<script>
import Slick from "vue-slick";

export default {
  components: { Slick },
  methods: {
    handleBeforeChange() {
      document.querySelector(".slick-next.slick-arrow").innerHTML = `
      <svg class="svg-next" width="50" height="50">
          <circle
            cx="25"
            cy="25"
            r="24"
            fill="none"
            stroke-width="2"
            stroke="rgb(100,100,100)"
          />
          <circle
            class="circle-go"
            cx="25"
            cy="25"
            r="24"
            fill="none"
            stroke-width="2"
            stroke="rgb(255,255,255)"
          />
          <polyline
            points="10,20 25,35 40,20"
            style="fill: none; stroke: #fff; stroke-width: 2"
          />
        </svg>`;

      document.querySelector(".slick-prev.slick-arrow").innerHTML = `
        <svg class="svg-prev" width="26" height="26">
          <circle
            cx="13"
            cy="13"
            r="12"
            fill="none"
            stroke-width="2"
            stroke="rgb(100,100,100)"
          />
          <polyline
            points="15,6 8,13 15  ,21"
            style="fill: none; stroke: #fff; stroke-width: 2"
          />
        </svg>      
      `;
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

<style lang="scss">
@import "@/assets/scss/main";

.slick-slider {
  position: relative;

  .slick-list {
    overflow: hidden;

    .slick-track {
      display: flex;
    }
  }

  .slick-next.slick-arrow {
    position: absolute;
    bottom: 42px;
    right: 6.5%;
    padding: 0;
    height: 52px;
    width: 52px;
    background: none;
    border-color: transparent;
    border-radius: 50%;
    z-index: 1001;

    .svg-next {
      transform: rotate(-90deg);
      border-radius: 100%;
      cursor: pointer;

      &:hover {
        transition: background-color linear 0.2s;
        background-color: #5c585a;
      }

      @keyframes progress {
        from {
          stroke-dashoffset: 150;
        }
        to {
          stroke-dashoffset: 0;
        }
      }

      .circle-go {
        animation: progress 12s;
        stroke-dasharray: 150;
        stroke-dashoffset: 150;
      }
    }
  }

  .slick-prev.slick-arrow {
    position: absolute;
    bottom: 55px;
    right: 11%;
    width: 28px;
    height: 28px;
    padding: 0;
    background: none;
    border-color: transparent;
    border-radius: 50%;
    z-index: 1001;

    .svg-prev {
      border-radius: 100%;
      cursor: pointer;

      &:hover {
        transition: background-color linear 0.2s;
        background-color: #5c585a;
      }
    }
  }

  .slick-dots {
    position: absolute;
    bottom: 40px;
    left: 0;
    right: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 1000;

    li {
      list-style: none;
      margin: 0px 10px;

      button {
        font-size: 0px;
        width: 10px;
        height: 10px;
        padding: 3px;
        background: #8f8888;
        border: none;
        border-radius: 50%;
      }
    }

    li.slick-active button {
      font-size: 0px;
      padding: 6px;
      background: #f0e8e8;
      border: none;
      border-radius: 50%;
    }
  }

  @media (max-width: 1439px) {
    .slick-prev.slick-arrow {
      right: 13%;
    }
  }

  @media (max-width: 1023px) {
    .slick-next.slick-arrow {
      .svg-next {
        display: none;
      }
    }
    .slick-prev.slick-arrow {
      .svg-prev {
        display: none;
      }
    }
  }
}

.slider-container {
  position: relative;
  margin: 90px auto;

  .slider {
    position: relative;
    display: block;

    .slider-inner {
      max-width: 1375px;
      height: 475px;
      margin: 0 auto;
      background-color: #000;
      border-radius: 32px;
    }
  }

  @media (max-width: 767px) {
    .slider {
      .slider-inner {
        height: calc(100vh - 90px);
        border-radius: 0;
      }
    }
  }
}

.slide {
  position: relative;
  max-width: 1345px;
  font-family: Nekst-Black;
  color: #fff;

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
    max-width: 585px;
    padding: 50px 0 0 70px;
    z-index: 1100;

    .slide-title {
      font-size: 54px;
      line-height: 48px;
      padding: 12px 0;
    }
    .slide-description {
      padding: 24px 0;
      font-size: 30px;
      line-height: 26px;
    }
    .btn {
      @include btn;
      height: 48px;
      width: 178px;
      z-index: 1100;
    }
  }

  @media (max-width: 1439px) {
    .slide-image {
      max-width: 675px;
      top: 75px;
      bottom: 19px;
      left: 250px;
    }
  }

  @media (max-width: 1023px) {
    .slide-info {
      padding: 185px 0 0 70px;

      .slide-description {
        display: none;
      }
      .slide-title {
        padding: 32px 0;
      }
      .btn {
        width: 178px;
        height: 48px;
      }
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
    .slide-info {
      padding: 35vh 0 0 0;
      max-width: 280px;
      margin: 0 auto;

      .slide-title {
        height: 85px;
        font-size: 32px;
        line-height: 28px;
        padding: 0 0 25px 0;
      }
    }
    .slide-image {
      max-width: 460px;
      top: 0px;
      bottom: 285px;
      left: -125px;
      right: 17px;
    }
  }
}
</style>