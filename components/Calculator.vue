<template>
  <div class="container">
    <div class="title">Рассчитайте стоимость автомобиля в лизинг</div>

    <div class="calculator">
      <div>
        <div class="calc-title">Стоимость автомобиля</div>
        <div class="calc-input">
          <input
            class="calc-input-number"
            @blur="priceHandler"
            type="number"
            v-model="calculatorValues.price"
            value.number="calculatorValues.price"
          />
          <span class="calc-symbol-price">
            <span>&#8381;</span>
          </span>

          <input
            class="calc-range"
            type="range"
            min="1000000"
            max="6000000"
            v-model="calculatorValues.price"
            value.number="calculatorValues.price"
          />
        </div>
      </div>
      <div>
        <div class="calc-title">Первоначальный взнос</div>
        <div class="calc-input">
          <div class="calc-input-number">
            <span class="calc-input-number-contribution"
              >{{ contribution }}
            </span>
          </div>

          <div class="calc-input-rate-box">
            <input
              class="calc-input-rate"
              @blur="rateHandler"
              type="number"
              v-model="calculatorValues.rate"
            />
            <span class="calc-symbol-rate"></span>
          </div>

          <input
            class="calc-range"
            type="range"
            min="10"
            max="60"
            v-model="calculatorValues.rate"
          />
        </div>
      </div>

      <div>
        <div class="calc-title">Срок лизинга</div>
        <div class="calc-input">
          <input
            class="calc-input-number"
            @blur="termHandler"
            type="number"
            v-model="calculatorValues.term"
            value.number="calculatorValues.term"
          />
          <span class="calc-symbol-month">
            <span>мес.</span>
          </span>

          <input
            class="calc-range"
            type="range"
            min="1"
            max="60"
            v-model="calculatorValues.term"
          />
        </div>
      </div>
    </div>

    <div class="calc-results">
      <div class="calc-result">
        <div class="calc-title">Сумма договора лизинга</div>
        <span class="cacl-value">{{ lisingSum }} </span>
      </div>

      <div class="calc-result">
        <div class="calc-title">Ежемесячный платеж</div>
        <span class="cacl-value">{{ Math.floor(monthlyPayment) }} </span>
      </div>

      <div class="calc-btn">
        <button class="btn" @click="sendCalculatorValues">
          Оставить заявку
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    priceHandler(event) {
      if (event.target.value > 6000000) {
        this.calculatorValues.price = 6000000;
      } else if (event.target.value < 0) {
        this.calculatorValues.price = 0;
      }
    },
    rateHandler(event) {
      if (event.target.value > 60) {
        this.calculatorValues.rate = 60;
      } else if (event.target.value < 10) {
        this.calculatorValues.rate = 10;
      }
    },
    termHandler(event) {
      if (event.target.value > 60) {
        this.calculatorValues.term = 60;
      } else if (event.target.value < 1) {
        this.calculatorValues.term = 1;
      }
    },
    sendCalculatorValues() {
      this.$emit("toggleForm");
      const data = {
        price: this.calculatorValues.price,
        rate: this.calculatorValues.rate,
        term: this.calculatorValues.term,
        contribution: this.contribution,
        lisingSum: this.lisingSum,
        monthlyPayment: this.monthlyPayment,
      };
      console.log(data);
    },
  },
  data() {
    return {
      calculatorValues: {
        price: 1000000,
        rate: 10,
        term: 1,
      },
    };
  },
  computed: {
    contribution() {
      return Math.floor(
        (this.calculatorValues.rate / 100) * this.calculatorValues.price
      );
    },
    lisingSum() {
      return Math.floor(
        this.contribution + this.calculatorValues.term * this.monthlyPayment
      );
    },
    monthlyPayment() {
      return (
        (this.calculatorValues.price - this.contribution) /
        this.calculatorValues.term
      );
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/assets/scss/main";

.container {
  max-width: 1375px;
  margin: 0 auto;

  .title {
    margin: 50px auto;
    font-family: Nekst-Black;
    font-size: 54px;
  }

  .calc-title {
    margin: 20px auto;
    max-width: 430px;
    font-family: Gilroy-Regular;
    font-size: 20px;
    line-height: 16px;
    color: #575757;
  }

  @media (max-width: 1439px) {
    .calc-title {
      margin: 20px 0;
    }
  }
  @media (max-width: 767px) {
    max-width: 280px;
    margin: 0 auto;

    .title {
      margin: 30px auto;
      font-size: 34px;
      line-height: 30px;
    }
    .calc-title {
      margin: 10px 0;
      font-size: 14px;
      line-height: 19px;
    }
  }
}

.calculator {
  display: flex;
  justify-content: space-between;

  .calc-input {
    position: relative;
    width: 430px;
    height: 70px;
    background: #f3f3f4;
    border-radius: 16px;
    font-family: Nekst-Black;
    font-size: 30px;
    line-height: 36px;
    color: rgba(87, 87, 87, 1);

    .calc-input-number {
      padding: 16px 15px 24px;
      background-color: transparent;
      border: none;
      font-family: Nekst-Black;
      font-size: 30px;
      line-height: 36px;
      color: rgba(87, 87, 87, 1);

      .calc-input-number-contribution {
        &:after {
          content: "\20BD";
        }
      }
    }
    .calc-input-rate-box {
      position: absolute;
      right: 10px;
      top: 10px;
      width: 70px;
      height: 50px;
      background-color: #ebebec;
      border-radius: 16px;

      .calc-input-rate {
        padding-left: 10px;
        width: 40px;
        height: 50px;
        border: none;
        background-color: transparent;
        text-align: center;
        font-family: Nekst-Black;
        font-size: 20px;
        line-height: 24px;
        color: rgba(87, 87, 87, 1);
      }
      .calc-symbol-rate {
        position: absolute;
        right: 15px;
        top: 3px;

        &::after {
          content: "%";
          font-size: 20px;
          line-height: 24px;
          color: rgba(87, 87, 87, 1);
        }
      }
    }

    .calc-range {
      position: absolute;
      padding: 0;
      bottom: 0;
      left: 20px;
      height: 3px;
      width: 90%;
      color: $orangeColor;
    }
  }
  .calc-symbol-month {
    position: absolute;
    right: 20px;
    top: 12px;
  }
  .calc-symbol-price {
    position: absolute;
    right: 15px;
    top: 15px;
  }

  @media (max-width: 1439px) {
    display: flex;
    flex-direction: column;

    .calc-input {
      width: 100%;
      margin-bottom: 40px;

      .calc-range {
        width: 95%;
      }
    }
  }
  @media (max-width: 1023px) {
    .calc-input {
      .calc-range {
        width: 94%;
      }
    }
  }
  @media (max-width: 767px) {
    .calc-input {
      margin-bottom: 20px;
      font-size: 22px;
      line-height: 20px;

      .calc-input-number {
        width: 100%;
        padding: 24px 15px;
        font-size: 22px;
        line-height: 20px;
      }
      .calc-input-rate-box {
        .calc-input-rate {
          padding-left: 8px;
          font-size: 22px;
          line-height: 20px;
        }
        .calc-symbol-rate {
          top: 13px;
        }
      }
      .calc-symbol-price {
        top: 25px;
      }
      .calc-symbol-month {
        top: 25px;
      }

      .calc-range {
        width: 86%;
      }
    }
  }
}

.calc-results {
  display: flex;
  justify-content: space-between;
  margin-top: 20px;

  .calc-result {
    width: 430px;
    margin: 30px 0;

    .cacl-value {
      position: relative;
      font-family: Nekst-Black;
      font-style: normal;
      font-size: 54px;
      line-height: 48px;
      color: rgba(87, 87, 87, 1);

      &:after {
        content: "\20BD";
      }
    }
  }

  .calc-btn {
    margin: 50px 0;

    .btn {
      @include btn;
      width: 425px;
      height: 60px;
      font-family: Nekst-Black;
      font-size: 30px;

      line-height: 36px;
    }
  }

  @media (max-width: 1439px) {
    flex-wrap: wrap;

    .calc-result {
      width: 50%;
      margin: 0;
    }
    .calc-btn {
      .btn {
        width: 345px;
        height: 68px;
      }
    }
  }
  @media (max-width: 1023px) {
    .calc-result {
      .cacl-value {
        font-size: 44px;
        line-height: 20px;
      }
    }
  }

  @media (max-width: 767px) {
    margin: 0;

    .calc-result {
      width: 100%;
      margin: 10px 0;

      .cacl-value {
        font-size: 22px;
        line-height: 20px;
      }
    }
    .calc-btn {
      margin: 25px 0;

      .btn {
        width: 280px;
        height: 60px;
        margin: 0;
        font-size: 22px;
        line-height: 20px;
      }
    }
  }
}

input[type="range"] {
  position: absolute;
  width: 95%;
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
}
input[type="range"]::-webkit-slider-runnable-track {
  border-radius: 10px/100%;
  height: 2px;
  border: 1px solid #ff9514;
  background-color: #fff;
}
input[type="range"]::-webkit-slider-thumb {
  background: #ff9514;
  border: 1px solid #ff9514;
  border-radius: 10px/100%;
  cursor: pointer;
  width: 15px;
  height: 15px;
  -webkit-appearance: none;
  margin-top: -7px;
}

input[type="range"]::-moz-range-track {
  border-radius: 10px/100%;
  height: 0px;
  border: 1px solid #ff9514;
  background-color: #ff9514;
}
input[type="range"]::-moz-range-thumb {
  background: #ff9514;
  border: 1px solid #ff9514;
  border-radius: 10px/100%;
  cursor: pointer;
  width: 15px;
  height: 15px;
}
</style>