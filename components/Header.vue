<template>
  <nav class="header">
    <div class="header-info">
      <div class="header-logo">
        <span class="header-logo-leasing">Leasing</span>
        <span class="header-logo-car">Car</span>
      </div>
      <div class="header-name">
        <span> лизинговая компания </span>
      </div>
    </div>

    <div class="header-nav">
      <div class="header-links">
        <a class="header-link dropdown" href=""
          >Лизинг
          <div class="dropdown-content">
            <a href="">Для личного пользования</a>
            <a href="">Для юридических лиц</a>
            <a href="">Калькулятор</a>
          </div>
        </a>
        <a class="header-link" href="">Каталог</a>
        <a class="header-link" href="">О нас</a>
      </div>
      <div class="header-btn">
        <button class="btn-transparent" @click="$emit('toggleForm')">
          Оставить заявку
        </button>
      </div>
    </div>
    <button class="nav-toggle" @click="$emit('toggleNav')">
      <span class="nav-toggle-item"></span>
    </button>
  </nav>
</template>

<script>
export default {};
</script>


<style lang="scss" scoped>
@import "@/assets/scss/main";

.nav-toggle {
  display: none;
  width: 30px;
  padding: 10px 0;
  font-size: 0;
  color: transparent;
  border: none;
  background: none;
  cursor: pointer;
  position: absolute;
  top: 32px;
  right: 32px;
  z-index: 1;

  .nav-toggle-item {
    display: block;
    width: 100%;
    height: 3px;
    position: absolute;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
    margin: auto;
    background-color: #000;

    &::before,
    &::after {
      content: "";
      width: 100%;
      height: 3px;
      z-index: 1;
      background-color: #000;
      position: absolute;
      left: 0;
      transition: transform 0.1s linear;
    }
    &::before {
      top: -8px;
    }
    &::after {
      width: 80%;
      bottom: -8px;
    }
  }

  @media (max-width: 1023px) {
    display: block;
  }

  @media (max-width: 767px) {
    .nav-toggle-item {
      background-color: #fff;

      &::before,
      &::after {
        background-color: #fff;
      }
    }
  }
}

.header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  display: flex;
  justify-content: space-between;
  height: 90px;
  background: #ffffff;
  box-shadow: 0px 4px 44px rgba(0, 0, 0, 0.1);
  z-index: 1009;

  .header-info {
    display: flex;
    justify-content: space-between;
    margin: 30px 17px;

    .header-logo {
      display: flex;
      justify-content: center;
      padding: 0 17px;
      border-right: 1px solid #c4c4c4;
      font-family: Gilroy-black;
      font-size: 34px;
      font-weight: bold;
      line-height: 100%;

      .header-logo-leasing {
        color: $orangeColor;
      }
      .header-logo-car {
        color: #000;
      }
    }

    .header-name {
      padding: 0 0;
      color: rgba(17, 17, 17, 0.5);

      span {
        display: block;
        padding: 5px 17px;
      }
    }
  }

  @media (max-width: 767px) {
    background-color: #000;

    .header-info {
      margin: 20px 17px;

      .header-name {
        display: none;
      }

      .header-logo {
        padding: 8px 0 0 0;
        border: none;

        .header-logo-car {
          color: #fff;
        }
      }
    }
  }
}

.header-nav {
  margin: 25px 30px;
  display: flex;
  justify-content: space-between;

  .header-links {
    display: flex;
    flex-direction: row;
    align-items: flex-start;
    padding: 0px;

    .header-link {
      padding: 10px 16px;
      font-weight: 700;
      text-decoration: none;
      border-radius: 8px;
      color: rgba(87, 87, 87, 1);

      &:hover {
        background-color: #f3f3f4;
      }
    }
  }

  .header-btn {
    padding: 0 24px;

    .btn-transparent {
      @include btn;
      background-color: transparent;
      color: $orangeColor;

      &:hover {
        background-color: $orangeColor;
        border-color: $orangeColor;
      }
      &:active {
        background-color: #e18618;
      }
    }
  }

  @media (max-width: 1023px) {
    display: none;
  }
}

.dropdown {
  position: relative;

  &:hover .dropdown-content {
    display: block;
  }

  .dropdown-content {
    display: none;
    position: absolute;
    top: 35px;
    left: 0;
    padding: 12px;
    background-color: #f9f9f9;
    border: 1px solid #f3f3f4;
    border-radius: 15px;
    min-width: 245px;
    box-shadow: 0px 4px 4px rgba(51, 51, 51, 0.04),
      0px 14px 24px rgba(51, 51, 51, 0.12);
    z-index: 1;

    a {
      display: block;
      padding: 10px;
      text-decoration: none;
      font-size: 16px;
      color: rgba(17, 17, 17, 1);

      &:hover {
        background-color: #f1f1f1;
      }
    }
  }
}
</style>