<template>
  <div class="nav-container">
    <div class="nav">
      <div class="nav-inner">
        <div class="nav-box">
          <div class="btn-close-box">
            <div class="btn-close" @click="$emit('toggleNav')">
              <span class="close"></span>
            </div>
          </div>
          <div class="nav-links">
            <a class="nav-link" href="">Лизинг</a>
            <a class="nav-link" href="">Каталог</a>
            <a class="nav-link" href="">О нас</a>
            <div class="nav-btn">
              <button class="btn" @click="$emit('toggleForm')">
                Оставить заявку
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
.nav-container {
  position: absolute;
  width: 100%;
  z-index: 1010;
}
.nav {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background-color: rgba(0, 0, 0, 0.3);
}
.nav-inner {
  position: absolute;
  bottom: 0;
  right: 0;
  width: 45%;
  height: 100%;
  background-color: #fff;
  border-top-left-radius: 32px;
  font-family: Nekst-Black;
  z-index: 101000;
}
.nav-box {
  position: absolute;
  height: 100%;
  width: 100%;
  display: flex;
  flex-direction: column;
}
.nav-links {
  display: flex;
  flex-direction: column;
  margin: 64px 44px;
}
.nav-link {
  padding: 16px 0;
  font-family: Gilroy-Regular;
  font-size: 24px;
  font-weight: 700;
  line-height: 24px;
  color: rgba(87, 87, 87, 1);
  text-decoration: none;
}
.nav-btn {
  position: absolute;
  bottom: 44px;
  margin: 0 auto;
}
.btn {
  width: 250px;
  height: 48px;
  padding: 12px 24px;
  background: #ff9514;
  border: solid 1px #ff9514;
  border-radius: 20px;
  font-family: Gilroy-Regular;
  font-size: 16px;
  font-weight: 700;
  line-height: 100%;
  color: #fff;
  cursor: pointer;
}

.btn-close-box {
  position: absolute;
  top: 33px;
  right: 41px;
}
.btn-close {
  position: absolute;
  right: 8px;
  top: 12px;
  width: 32px;
  height: 32px;
  opacity: 1;
}
.btn-close:before,
.btn-close:after {
  position: absolute;
  left: 15px;
  content: " ";
  height: 25px;
  width: 2.75px;
  background-color: #333;
}
.btn-close:before {
  transform: rotate(45deg);
}
.btn-close:after {
  transform: rotate(-45deg);
}

@media (max-width: 767px) {
  .btn-close-box {
    top: 20px;
    right: 10px;
  }
  .nav-inner {
    width: 80%;
  }
  .nav-links {
    margin: 64px 24px;
  }
  .nav-btn {
    bottom: 24px;
    right: 20px;
  }
  .btn {
    width: 216px;
  }
}
</style>