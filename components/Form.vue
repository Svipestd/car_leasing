<template>
  <div class="form-container">
    <div class="form">
      <div class="form-inner">
        <div class="btn-close-box">
          <div class="btn-close" @click="$emit('toggleForm')">
            <span class="btn-close-icon"></span>
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

            <div class="form-btn">
              <button class="btn">Оставить заявку</button>
            </div>
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

<style lang="scss" scoped>
@import "@/assets/scss/main";

.form-container {
  position: absolute;
  width: 100%;
  z-index: 1011;

  .form {
    position: fixed;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    background-color: rgba(0, 0, 0, 0.3);

    .form-inner {
      position: absolute;
      bottom: 0;
      height: 80%;
      width: 100%;
      background-color: #fff;
      border-top-left-radius: 20px;
      border-top-right-radius: 20px;
    }
  }

  @media (max-width: 767px) {
    .form {
      .form-inner {
        height: 85%;
      }
    }
  }
}

.btn-close-box {
  position: absolute;
  top: 48px;
  right: 48px;

  .btn-close {
    position: relative;
    width: 48px;
    height: 48px;
    background: #f3f3f4;
    border-radius: 100px;

    .btn-close-icon {
      position: absolute;
      right: 8px;
      top: 12px;
      width: 32px;
      height: 32px;
      opacity: 0.3;

      &:hover {
        opacity: 1;
      }
      &::before,
      &::after {
        position: absolute;
        left: 15px;
        content: " ";
        height: 25px;
        width: 2px;
        background-color: #333;
      }
      &::before {
        transform: rotate(45deg);
      }
      &::after {
        transform: rotate(-45deg);
      }
    }
  }

  @media (max-width: 767px) {
    top: 24px;
    right: 20px;

    .btn-close {
      width: 24px;
      height: 24px;

      .btn-close-icon {
        right: 4px;
        top: 6px;
        width: 24px;
        height: 24px;

        &:before,
        &:after {
          height: 13px;
          width: 2px;
        }
      }
    }
  }
}

.form-body {
  max-width: 655px;
  margin: 160px auto;

  .form-title {
    font-size: 54px;
    line-height: 48px;
    padding-bottom: 24px;
    font-family: Nekst-Black;
  }
  .form-description {
    max-width: 466px;
    padding-bottom: 44px;
    font-family: Gilroy-Regular;
    font-size: 16px;
    line-height: 24px;
    font-weight: 400;
  }

  @media (max-width: 767px) {
    max-width: 280px;
    margin: 12vh auto;

    .form-title {
      max-width: 280px;
      margin: 0 auto;
      font-size: 22px;
      line-height: 20px;
    }
    .form-description {
      max-width: 240px;
      padding-bottom: 10px;
      font-size: 14px;
      line-height: 19px;
    }
  }
}

.form-inputs {
  display: flex;
  justify-content: space-around;

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
    color: $greyColor;

    &:hover {
      background: #eaeaeb;
    }
    &:focus {
      background: rgb(248, 248, 248);
      border: 1px solid $orangeColor;
      box-sizing: border-box;

      .form-input {
        opacity: 0.2;
        border: 10px solid $orangeColor;
        border-radius: 16px;
      }
    }
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

  @media (max-width: 767px) {
    flex-direction: column;

    .form-input {
      margin: 5px 0;

      .form-input-number {
        max-width: 280px;
        padding: 24px 16px;
        font-size: 16px;
        line-height: 24px;
      }
    }

    .form-input-error-text {
      font-size: 14px;
    }
  }
}

.form-submit {
  display: flex;
  justify-content: space-between;
  max-width: 655px;
  height: 100px;
  margin: 32px 0;
  padding: 29px 33px;
  border: 2px solid #f3f3f4;
  border-radius: 16px;

  .form-permission {
    max-width: 350px;
    font-family: Gilroy-Regular;
    font-size: 14px;
    line-height: 21px;
    color: rgba(17, 17, 17, 0.5);

    a {
      color: #000;
      text-decoration: none;
    }
  }
  .form-btn {
    .btn {
      @include btn;
      width: 178px;
      height: 48px;
    }
  }

  @media (max-width: 767px) {
    flex-direction: column-reverse;
    margin: 3px 0;
    padding: 0;
    border: none;

    .form-permission {
      margin: -10px 0;
      text-align: center;
      font-size: 14px;
      line-height: 19px;
    }
    .form-btn {
      .btn {
        width: 280px;
        height: 48px;
        margin-top: 0px;
      }
    }
  }
}

.form-social {
  display: flex;
  justify-content: space-between;
  max-width: 112px;
  height: 48px;
  margin: 0 auto;

  .form-social-link {
    width: 48px;
    border: 2px solid #e7e7e7;
    border-radius: 200px;

    .form-social-link-whatsapp {
      display: block;
      margin: 12px auto;
    }
    .form-social-link-telegram {
      display: block;
      margin: 15px auto;
    }
  }

  @media (max-width: 767px) {
    margin-top: 20px;
  }
}
</style>