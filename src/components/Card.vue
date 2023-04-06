<template>
  <div class="card">
    <div class="card__body">
      <h2 class="card__title">{{ item.title }}</h2>
      <div class="card__img">
        <img
          :src="require(`@/assets/images/advantage/${item.image}.png`)"
          alt=""
        />
      </div>
    </div>
    <div class="card__content">{{ item.content }}</div>
  </div>
</template>

<script>
export default {
  props: ['item'],
}
</script>

<style scoped lang='scss'>
.card {
  height: 328px;
  width: 300px;
  background: #f3f6fb;
  border-radius: 8px;
  padding: 20px 40px;
  position: relative;
  margin-right: 40px;
  transition: all 0.5s ease-in-out;
  cursor: pointer;
  transition: all .8s ease 0s;
  transform: translate(0, 40%);
  opacity: 0;

  &.active {
    transform: translate(0, 0);
    opacity: 1;
  }

  &:hover &__img {
    opacity: 0;
  }

  &:hover &__title {
    opacity: 0;
  }

  &:hover {
    background: $brand-color;
  }

  &:hover &__content {
    opacity: 1;
  }

  &__body {
  }
  &__title {
    font-weight: 500;
    font-size: 24px;
    line-height: 130%;
    color: $dark;
    text-align: center;
    transition: all 0.5s ease-in-out;
  }
  &__img {
    position: absolute;
    bottom: 0;
    left: 50%;
    transform: translate(-50%, 0);
    opacity: 1;
    transition: all 0.6s ease-in-out;
    z-index: 5;
  }

  &__content {
    font-weight: 400;
    font-size: 18px;
    line-height: 25px;
    position: absolute;
    top: 0;
    padding: 20px 30px 0 0;
    color: $light;
    opacity: 0;
    transition: all 0.5s ease-in-out;
  }
}
</style>