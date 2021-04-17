<template>
  <div class="container">
    <div class="title">Рассчитайте стоимость автомобиля в лизинг</div>
    <div class="calculator">

      <div>
        <div class="calc-title">Стоимость автомобиля</div>
        <div class="calc-input">
          <input class="calc-input-number"
            @blur="priceHandler"
            type="number"
            v-model="calculatorValues.price"
            value.number="calculatorValues.price"
          />
          <span class="calc-symbol-price">
            <span class="calc-symbol">&#8381;</span>
          </span>
          
          <input class="calc-range"
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
            <span>{{ contribution }}
                <span >&#8381;</span>
            </span>
          </div>
          <div class="calc-input-rate-box">
            <input class="calc-input-rate"
            @blur="rateHandler"
            type="number"
            v-model="calculatorValues.rate"
            />
            <span class="calc-symbol-rate">
              <span class="calc-symbol-rate-text">%</span> 
            </span>
            
          </div>
          
          <input class="calc-range"
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
          <input class="calc-input-number"
          @blur="termHandler"
          type="number"
          v-model="calculatorValues.term"
          value.number="calculatorValues.term"
          />
          <span class="calc-symbol-month">
            <span class="calc-symbol">мес.</span>
          </span>
          
          <input class="calc-range" type="range" min="1" max="60" v-model="calculatorValues.term" />
        </div>
      </div>

    </div>

    <div class="calc-results">
      <div class="calc-result">
        <div class="calc-title">Сумма договора лизинга</div>
        <span class="cacl-value">{{ lisingSum }}
          <span class="calc-symbol-ruble">
            <span class="calc-symbol-ruble-text">&#8381;</span>
          </span>
        </span>
      </div>
      
      <div class="calc-result">
        <div class="calc-title">Ежемесячный платеж</div>
        <span class="cacl-value">{{ monthlyPayment }}
          <span class="calc-symbol-ruble">
            <span class="calc-symbol-ruble-text">&#8381;</span>
          </span>
        </span>
      </div>

      <div class="calc-btn">
        <button class="btn" @click="sendCalculatorValues" >Оставить заявку</button>
      </div>
      <!-- {{`price${calculatorValues.price} rate${calculatorValues.rate} term${calculatorValues.term}`}} -->
      
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
      return Math.round(
        (this.calculatorValues.rate / 100) * this.calculatorValues.price
      );
    },
    lisingSum() {
      return Math.round(
        this.contribution + this.calculatorValues.term * this.monthlyPayment
      );
    },
    monthlyPayment() {
      return Math.round(
        this.calculatorValues.price -
          this.contribution *
            (this.calculatorValues.rate / 1 + this.calculatorValues.rate / 100 -
              this.calculatorValues.term -
              1)
      );
    },
  },
};
</script>

<style scoped>
.container {
  max-width: 1375px;
  margin: 0 auto;
  font-family: Nekst-Black;
}
.title {
  margin: 50px auto;
  font-size: 54px;
  font-weight: 900;
}
.calculator {
  display: flex;
  justify-content: space-between;
}
.calc-title {
  margin: 20px auto;
  max-width: 430px;
  font-family: Gilroy-Regular;
  font-size: 20px;
  line-height: 16px;
  color: #575757;
}
.calc-input {
  position: relative;
  width: 430px;
  height: 70px;
  background: #f3f3f4;
  border-radius: 16px;
}
.calc-input-number {
  padding: 16px 15px 24px;
  background-color: transparent;
  border: none;
  font-family: Nekst-Black;
  font-size: 30px;
  line-height: 36px;
  font-weight: 900;
  color: rgba(87, 87, 87, 1);
}

.calc-input-rate-box {
  position: absolute;
  right: 10px;
  top: 10px;
  width: 70px;
  height: 50px;
  background-color: #ebebec;
  border-radius: 16px;
}
.calc-input-rate {
  padding-left: 10px;
  width: 40px;
  height: 50px;
  border: none;
  background-color: transparent;
  text-align: center;
  font-size: 20px;
  line-height: 24px;
  font-weight: 900;
  color: rgba(87, 87, 87, 1);
}
.calc-symbol-month {
  position: absolute;
  right: 20px;
  top: 12px;
  font-size: 30px;
  line-height: 36px;
  color: rgba(87, 87, 87, 1);
}
.calc-symbol-price {
  position: absolute;
  right: 15px;
  top: 15px;
}
.calc-symbol-rate {
  position: absolute;
  right: 15px;
  top: 12px;
}
.calc-symbol-rate-text {
  font-size: 20px;
  line-height: 24px;
  font-weight: 900;
  color: rgba(87, 87, 87, 1);
}
.calc-symbol {
  font-family: Nekst-Black;
  font-size: 30px;
  line-height: 36px;
  font-weight: 900;
  color: rgba(87, 87, 87, 1);
}
.calc-symbol-ruble {
  position: absolute;
  top: 9px;
  right: -48px;
}
.calc-symbol-ruble-text {
  font-family: Nekst-Black;
  font-size: 54px;
  line-height: 48px;
  font-weight: 900;
  color: rgba(87, 87, 87, 1);
}

.calc-range {
  position: absolute;
  padding: 0;
  bottom: 0;
  left: 20px;
  height: 3px;
  width: 90%;
  color: #ff9514;
}
.calc-results {
  display: flex;
  justify-content: space-between;
  margin-top: 20px;
}
.calc-result {
  width: 430px;
  margin: 30px 0;
}
.cacl-value {
  position: relative;
  font-family: Nekst-Black;
  font-style: normal;
  font-weight: 900;
  font-size: 54px;
  line-height: 48px;
  color: rgba(87, 87, 87, 1);
}
.btn {
  position: static;
  width: 425px;
  height: 60px;
  margin: 50px 0;
  padding: 12px 24px;
  background: #ff9514;
  border: solid 1px #ff9514;
  border-radius: 40px;
  font-family: Nekst-Black;
  font-size: 30px;
  font-weight: 900;
  line-height: 36px;
  color: #fff;
  cursor: pointer;
}
.btn:hover {
  background-color: #111111;
  border-color: #111111;
  border-radius: 40px;
  transition: background-color linear 0.2s;
}

input[type="range"] {
  position: absolute;
  width: 90%;
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
  height: 2px;
  border: 1px solid #ff9514;
  background-color: #fff;
}
input[type="range"]::-moz-range-thumb {
  background: #ff9514;
  border: 1px solid #ff9514;
  border-radius: 10px/100%;
  cursor: pointer;
}

@media (max-width: 1439px) {
  .calculator {
    display: flex;
    flex-direction: column;
  }
  .calc-input {
    width: 100%;
    margin-bottom: 40px;
  }
  .calc-title {
    margin: 20px 0;
  }
  .calc-results {
    flex-wrap: wrap;
  }
  .calc-result {
    width: 50%;
  }
  .btn {
    width: 345px;
    height: 68px;
  }
  input[type="range"] {
    width: 95%;
  }
}

@media (max-width: 767px) {
  .container {
    max-width: 280px;
    margin: 0 auto;
  }
  .title {
    font-size: 34px;
    line-height: 30px;
  }
  .calc-title {
    margin: 10px 0;
    font-size: 14px;
    line-height: 19px;
  }
  .calc-input {
    margin-bottom: 20px;
  }
  .calc-input-number {
    width: 100%;
    padding: 24px 15px;
    font-size: 22px;
    line-height: 20px;
  }
  .calc-input-rate {
    padding-left: 8px;
    font-size: 22px;
    line-height: 20px;
  }
  .calc-symbol {
    font-size: 22px;
    line-height: 20px;
  }
  .calc-symbol-price {
    right: 15px;
    top: 25px;
  }
  .calc-symbol-rate {
    right: 15px;
    top: 15px;
  }
  .calc-symbol-rate-text {
    font-size: 20px;
    line-height: 20px;
  }
  .calc-symbol-ruble {
    top: 3px;
    right: -20px;
  }
  .calc-symbol-ruble-text {
    font-size: 22px;
    line-height: 20px;
  }
  .calc-result {
    width: 100%;
  }
  .btn {
    width: 280px;
    height: 60px;
  }
  input[type="range"] {
    width: 85%;
  }
  .calc-results {
    margin: 0;
  }
  .calc-result {
    margin: 10px 0;
  }
  .cacl-value {
    font-size: 22px;
    line-height: 20px;
  }
  .btn {
    font-size: 22px;
    line-height: 20px;
  }
}
</style>