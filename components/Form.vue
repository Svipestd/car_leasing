<template>
  <div class="form-container">
    <div class="form">
      <div class="form-inner">
        <div class="btn-close-box">
          <div class="btn-close" @click="$emit('toggleForm')">
            <span class="close"></span>
          </div>
        </div>

        <div class="form-body">
          <div class="form-title">Онлайн-заявка</div>
          <div class="form-description">
            Заполняйте форму, и мы скоро свяжемся с вами, чтобы ответить на все
            вопросы
          </div>

          <div class="form-inputs">
            <div class="form-input">
              <div class="form-input-box">
                <input
                  :class="[
                    inputErrors.numberError && 'form-input-error',
                    'form-input-number',
                  ]"
                  @blur="validateNumber"
                  type="tel"
                  placeholder="8 (9xx) xxx-xxxx"
                  v-phone
                />
              </div>
              <div v-if="inputErrors.numberError" class="form-input-error-text">
                {{ inputErrors.numberError }}
              </div>
            </div>

            <div class="form-input">
              <div class="form-input-box">
                <input
                  :class="[
                    inputErrors.nameError && 'form-input-error',
                    'form-input-number',
                  ]"
                  @blur="validateName"
                  type="text"
                  placeholder="Имя"
                />
              </div>

              <div v-if="inputErrors.nameError" class="form-input-error-text">
                {{ inputErrors.nameError }}
              </div>
            </div>
          </div>

          <div class="form-submit">
            <div class="form-permission">
              Нажимая на кнопку "Оставить заявку", я даю согласие
              <a href="">на обработку персональных данных</a>
            </div>

            <button class="btn">Оставить заявку</button>
          </div>

          <div class="form-social">
            <a href="#" target="_blank" class="form-social-link">
              <img
                class="form-social-link-whatsapp"
                src="@/assets/icons/Vector.svg"
                alt=""
              />
            </a>
            <a href="#" target="_blank" class="form-social-link">
              <img
                class="form-social-link-telegram"
                src="@/assets/icons/Shape.svg"
                alt=""
              />
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>


<script>
export default {
  data() {
    return {
      inputErrors: {
        numberError: "",
        nameError: "",
      },
    };
  },
  methods: {
    validateNumber(event) {
      if (event.target.value.trim() === "") {
        this.inputErrors.numberError = "Обязательное поле";
      } else if (event.target.value.length < 15) {
        this.inputErrors.numberError = "Неверный формат номера";
      } else {
        this.inputErrors.numberError = "";
      }
    },
    validateName(event) {
      if (event.target.value.trim() === "") {
        this.inputErrors.nameError = "Обязательное поле";
      } else {
        this.inputErrors.nameError = "";
      }
    },
  },
};
</script>

<style scoped>
.form-container {
  position: absolute;
  width: 100%;
  z-index: 1011;
}
.form {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background-color: rgba(0, 0, 0, 0.3);
}
.form-inner {
  position: absolute;
  bottom: 0;
  height: 80%;
  width: 100%;
  background-color: #fff;
  border-top-left-radius: 20px;
  border-top-right-radius: 20px;
  font-family: Nekst-Black;
}

.btn-close-box {
  position: absolute;
  top: 48px;
  right: 48px;
}
.btn-close {
  position: relative;
  width: 48px;
  height: 48px;
  background: #f3f3f4;
  border-radius: 100px;
}

.close {
  position: absolute;
  right: 8px;
  top: 12px;
  width: 32px;
  height: 32px;
  opacity: 0.3;
}
.close:hover {
  opacity: 1;
}
.close:before,
.close:after {
  position: absolute;
  left: 15px;
  content: " ";
  height: 25px;
  width: 2px;
  background-color: #333;
}
.close:before {
  transform: rotate(45deg);
}
.close:after {
  transform: rotate(-45deg);
}

.form-body {
  max-width: 655px;
  margin: 160px auto;
}
.form-title {
  font-size: 54px;
  line-height: 48px;
  padding-bottom: 24px;
}
.form-description {
  max-width: 466px;
  padding-bottom: 44px;
  font-family: Gilroy-Regular;
  font-size: 16px;
  line-height: 24px;
  font-weight: 400;
}
.form-inputs {
  display: flex;
  justify-content: space-around;
}

.form-input-number {
  position: relative;
  width: 312px;
  height: 48px;
  background: #f3f3f4;
  border-radius: 16px;
  border: 1px solid #f3f3f4;

  padding: 16px 15px 24px;
  font-family: Next-Black;
  font-size: 30px;
  line-height: 36px;
  font-weight: 900;
  color: rgba(87, 87, 87, 1);
}
.form-input-number:hover {
  background: #eaeaeb;
}
.form-input-number:focus {
  background: rgb(248, 248, 248);
  border: 1px solid #ff9514;
  box-sizing: border-box;
}
.form-input-number:focus .form-input {
  opacity: 0.2;
  border: 10px solid #ff9514;
  border-radius: 16px;
}
.form-input-number.form-input-error {
  border-color: rgba(213, 50, 52, 1);
}
.form-input-error-text {
  font-family: Gilroy-Regular;
  font-size: 16px;
  line-height: 24px;
  color: rgba(213, 50, 52, 1);
}

.form-submit {
  display: flex;
  justify-content: space-between;
  max-width: 655px;
  height: 100px;
  margin: 32px 0;
  padding: 29px 33px;
  border: 2px solid #f3f3f4;
  box-sizing: border-box;
  border-radius: 16px;
}
.form-permission {
  max-width: 350px;
  font-family: Gilroy-Regular;
  font-size: 14px;
  line-height: 21px;
  color: rgba(17, 17, 17, 0.5);
}
.form-permission a {
  color: #000;
  text-decoration: none;
}
.form-social {
  display: flex;
  justify-content: space-between;
  max-width: 112px;
  height: 48px;
  margin: 0 auto;
}
.form-social-link {
  width: 48px;
  border: 2px solid #e7e7e7;
  box-sizing: border-box;
  border-radius: 200px;
}
.form-social-link-whatsapp {
  display: block;
  margin: 12px auto;
}
.form-social-link-telegram {
  display: block;
  margin: 15px auto;
}
.btn {
  width: 175px;
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
}
.btn:hover {
  background-color: #111111;
  border-color: #111111;
  border-radius: 40px;
  transition: background-color linear 0.2s;
}

@media (max-width: 767px) {
  .btn-close-box {
    top: 24px;
    right: 20px;
  }
  .btn-close {
    width: 24px;
    height: 24px;
  }
  .close {
    right: 4px;
    top: 6px;
    width: 24px;
    height: 24px;
  }
  .close:before,
  .close:after {
    height: 13px;
    width: 2px;
  }
  .form-inner {
    height: 85%;
  }
  .form-body {
    margin: 24px 20px;
  }
  .form-title {
    max-width: 280px;
    margin: 0 auto;
    font-size: 22px;
    line-height: 20px;
  }
  .form-description {
    max-width: 240px;
    padding-bottom: 32px;
    font-size: 14px;
    line-height: 19px;
  }
  .form-inputs {
    flex-direction: column;
  }
  .form-input {
    margin: 5px 0;
  }
  .form-input-number {
    max-width: 280px;
    padding: 24px 16px;
    font-size: 16px;
    line-height: 24px;
  }
  .form-submit {
    flex-direction: column-reverse;
    margin:  3px 0;
    padding: 0;
    border: none;
  }
  .form-permission {
    margin: -16px 0 -24px 0;
    text-align: center;
    font-size: 14px;
    line-height: 19px;
  }
  .btn {
    width: 280px;
    height: 48px;
  }
  .form-social {
    margin-top: 40px;
  }
}
</style>