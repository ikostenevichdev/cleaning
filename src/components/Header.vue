<template>
  <header class="header">
    <!-- <div class="header__container container">
      <router-link to="/home" class="header-logo">
        <img
          data-goto="#main-section"
          src="@/assets/images/logo.png"
          alt="logotype"
        />
      </router-link>
      <div class="header__switcher">
        <span class="active">Дом</span>
        <span>Офис</span>
      </div>
      <Navbar class="header__menu" />
      <div class="header__contacts">
        <a href="tel:380674016977">+380 67 401 69 77</a> 24/7
      </div>
    </div> -->
  </header>
</template>

<script>
import Navbar from './Navbar'

export default {
  components: { Navbar },
}
</script>

<style scoped lang='scss'>
.header {
  // width: 100vw;
  // position: fixed;
  // top: 0;
  // left: 0;
  // z-index: 30;
  position: absolute;
  width: 100%;
  z-index: 100;

  &__container {
    display: flex;
    align-items: center;
    min-height: 70px;
  }

  &__switcher {
    display: flex;
    justify-content: space-around;
    align-items: center;
    width: 130px;
    height: 37px;
    border-radius: 48px;
    background: #fff;
    color: #636c81;
    margin-left: 20px;
    border: 1px solid #E2E8F0; 

    span {
      color: #E5E5E5;
      font-weight: 500;
      font-size: 14px;

      &.active {
        display: flex;
        justify-content: center;
        align-items: center;
        width: 55px;
        height: 31px;
        border-radius: 34px;
        background: $brand-color;
        color: #fff;
      }
    }
  }

  &__menu {
    flex: 1 1 auto;
    display: flex;
    justify-content: center;
  }

  &__contacts {
    font-weight: 500;
    font-size: 16px;

    a {
      position: relative;
      margin-right: 15px;
      padding-right: 15px;
      color: $dark;

      &:after {
        content: '';
        position: absolute;
        border-right: 2px solid $dark;
        height: 75%;
        right: 0;
        transform: translate(100%, 0);
      }
    }
  }
}
</style>