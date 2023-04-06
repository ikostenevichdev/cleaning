<template>
  <main class="content">
    <section class="main-screen">
      <div class="main-screen__image">
        <img src="@/assets/images/main-screen.jpg" alt="" />
      </div>
      <div class="main-screen__content">
        <div class="main-screen__container container">
          <div class="main-screen__body">
            <div class="main-screen__box">
              <h1 class="anim-items">Уборка квартир в Киеве</h1>
              <p class="anim-items">
                Мы уберем у вас дома или в офисе. Наведем чистоту после ремонта
                и проведем генеральную уборку.
              </p>
            </div>
          </div>
        </div>
      </div>
    </section>
    <!-- <section class="advantage">
      <div class="advantage__container container">
        <Card
          v-for="item in advantage"
          :key="'advantage-' + item.image"
          :item="item"
          class="anim-items anim-no-hide"
        />
      </div>
    </section> -->
    <section class="cleaning anim-items anim-items-1/3">
      <!-- anim-items anim-items-1/3 anim-no-hide -->
      <div class="cleaning__box">
        <div class="cleaning__container">
          <div class="cleaning__head">
            <h2 class="cleaning__title">Как мы убираем</h2>
            <div class="cleaning__descr">
              Клинер приезжает в назначенное время со всем необходимым и сразу
              приступает к делу. Вам остаётся только оценить результат.
            </div>
          </div>
        </div>
        <div class="cleaning__footer">
          <div class="cleaning__row">
            <div class="cleaning__image">
              <img src="@/assets/images/kitchen.png" alt="" />
              <div class="qweq">wqeew</div>
            </div>
          </div>
          <div class="cleaning__menu cleaning-menu anim-items">
            <h3 class="cleaning-menu__title">Как мы убираем</h3>
            <div class="cleaning-menu__body">
              <ul class="cleaning-menu__list">
                <li :class="test ? 'active' : ''" @click="test = !test">
                  Кухня
                </li>
                <li>Комнаты</li>
                <li :class="test ? '' : 'active'" @click="test = !test">
                  Ванная
                </li>
                <li>Прихожая</li>
              </ul>
            </div>
          </div>
        </div>
      </div>
      <!-- <div class="cleaning__animation"> -->
      <!-- <div class="cleaning__row">
        <div class="cleaning__column">
          <div class="cleaning__menu cleaning-menu anim-items anim-no-hide
            "
          >
            <h3 class="cleaning-menu__title">Как мы убираем</h3>
            <div class="cleaning-menu__body">
              <ul class="cleaning-menu__list">
                <li :class="test ? 'active' : ''" @click="test = !test">
                  Кухня
                </li>
                <li>Комнаты</li>
                <li :class="test ? '' : 'active'" @click="test = !test">
                  Ванная
                </li>
                <li>Прихожая</li>
              </ul>
            </div>
          </div>
        </div>
        <div class="cleaning__column">
          <div class="cleaning__image anim-items anim-no-hide">
            <img src="@/assets/images/kitchen.png" alt="" />
          </div>
        </div>
      </div> -->
      <!-- </div> -->
    </section>
  </main>
</template>

<script>
import Card from '@/components/Card'

export default {
  components: { Card },
  data() {
    return {
      test: false,
      isActiveAnimate: false,
      advantage: [
        {
          title: 'Тщательно отобранный персонал',
          image: '1',
          content:
            'Lorem ipsum dolor sit amet consectetur, adipisicing elit. Praesentium eius officiis unde, in molestias est! Lorem ipsum dolor sit amet consectetur, adipisicing elit. Praesentium eius officiis unde, in molestias est!',
        },
        {
          title: 'Качественная эко-химия',
          image: '2',
          content:
            'Lorem ipsum dolor sit amet consectetur, adipisicing elit. Praesentium eius officiis unde, in molestias est! ipsum dolor sit amsicing elit. Praesentium eius officiis unde,',
        },
        {
          title: 'Контролируем качество',
          image: '3',
          content:
            'Lorem ipsum dolor sit amsicing elit. Praesentium eius officiis unde, in molestias est!',
        },
        {
          title: 'Работаем круглосуточно',
          image: '4',
          content:
            'Lorem ipsum dolor sit amet consectetur, adipisicing elit. Praesentium eius of',
        },
      ],
    }
  },

  methods: {
    animOnScroll() {
      const animItems = document.querySelectorAll('.anim-items')

      console.log(animItems, '2213131313sqedweq')

      if (animItems.length > 0) {
        animItems.forEach((item, idx) => {
          const animItemHeight = item.offsetHeight
          const animItemOffset = this.offset(item).top
          let animStart = 4

          if (item.classList.contains('anim-items-1/3')) {
            animStart = 1
          } else {
            // animStart = 4
          }

          console.log(animItemHeight, animItemOffset)

          let animItemPoint = window.innerHeight - animItemHeight / animStart

          console.log(animItemOffset, '===>')

          if (animItemHeight > window.innerHeight) {
            animItemPoint = window.innerHeight - window.innerHeight / animStart
            console.log('231313131131')
          }

          console.group('Anim')
          console.log(item, '--> item')
          console.log(animItemOffset, '--> animItemOffset')
          console.log(animItemPoint, '-->animItemPoint')
          console.log(pageYOffset, '-->pageYOffset')
          console.log(animItemHeight, '-->animItemHeight')
          console.groupEnd()

          if (
            pageYOffset > animItemOffset - animItemPoint &&
            pageYOffset < animItemOffset + animItemHeight
          ) {
            // if (!item.classList.contains('anim-full') || (item.classList.contains('anim-full') && pageYOffset > animItemHeight)) {
            item.classList.add('active')
          } else if (
            item.classList.contains('anim-full') &&
            pageYOffset < animItemHeight
          ) {
            item.classList.remove('active')
          } else {
            if (!item.classList.contains('anim-no-hide')) {
              item.classList.remove('active')
            }
          }

          // this.$refs.row.classList.contains('active') ? this.isActiveAnimate = true : this.isActiveAnimate = false

          // if (
          //   item.classList.contains('anim-full') &&
          //   pageYOffset >= animItemOffset
          // ) {
          //   item.classList.add('active')
          // } else if (
          //   item.classList.contains('anim-full') &&
          //   pageYOffset <= animItemOffset - animItemHeight / 4
          // ) {
          //   item.classList.remove('active')
          // }
        })
      }
    },
    offset(el) {
      const rect = el.getBoundingClientRect()
      const scrollLeft =
        window.pageXOffset || document.documentElement.scrollLeft
      const scrollTop = window.pageYOffset || document.documentElement.scrollTop
      return {
        top: rect.top + scrollTop,
        left: rect.left + scrollLeft,
      }
    },
  },

  mounted() {
    this.animOnScroll()
    window.addEventListener('scroll', this.animOnScroll)

    console.log()
  },

  destroyed() {
    window.removeEventListener('scroll', this.animOnScroll)
  },
}
</script>

<style scoped lang='scss'>
.main-screen {
  min-height: 100vh;
  display: flex;
  position: relative;

  &__image {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;

    img {
      position: absolute;
      width: 100%;
      height: 100%;
      top: 0;
      left: 0;
      object-fit: cover;
    }

    @media (min-width: 767px) {
      flex: 0 0 50%;
      position: relative;
    }
  }

  &__content {
    display: flex;
    align-items: center;
    justify-content: center;
    flex: 0 0 100%;
    position: relative;
    padding: 100px 0px;

    @media (min-width: 767px) {
      transform: translate(-50%, 0px);
    }
  }

  &__container {
    width: 100%;
  }

  &__body {
    @media (min-width: 767px) {
      width: 50%;
      margin-left: auto;
    }
  }

  &__box {
    max-width: 400px;
    margin: 0 auto;
    margin-bottom: 10px;

    @media (min-width: 767px) {
      max-width: 330px;
    }

    @media (max-width: 767px) {
      background: rgba(245, 245, 245, 0.8);
      padding: 10px 20px;
    }

    h1 {
      font-size: 76px;
      line-height: 86px;
      font-weight: 400;
      margin-bottom: 30px;
    }

    p {
      font-size: 18px;
      font-weight: 400;
      line-height: 25px;
    }

    @media (max-width: 480px) {
      max-width: 80%;

      h1 {
        font-size: 48px;
        line-height: 56px;
      }

      p {
        font-size: 16px;
        line-height: 22px;
      }
    }
  }
}

.advantage {
  padding: 73px 0;

  &__container {
    display: flex;
  }
}

.cleaning {
  padding-top: 76px;

  &.active {
    .cleaning__footer {
      top: 0;
    }

    .cleaning__row {
      // margin: 0 0 0 calc(100vw - ((100vw - 375px) + (100vw - 100%)));
      margin: 0 0 0 calc(100vw - ((100vw - 375px) + (100vw - 100%)));
      max-width: 100%;

      @media (max-width: 1200px) {
        margin: 0 0 0 calc(100vw - ((100vw - 280px) + (100vw - 100%)));
      }

      @media (max-width: 600px) {
        margin: 0;
      }
    }

    .cleaning__image {
      img {
        @media (max-width: 992px) {
          height: initial;
          top: 50%;
          transform: translate(0, -50%);
        }

        @media (max-width: 600px) {
          bottom: 0;
          transform: translate(0, 0%);
          top: 50%;
        }
      }
      // background: $brand-color;
      // transition: background-color .1s ease 2s;
    }

    .cleaning__menu {
      transform: translate(0, 0);
      visibility: visible;
      transition: all 1s ease 0.6s;
    }

    .cleaning-menu__body {
      // justify-content: flex-start;
      // padding-bottom: 55px;
      
    }
  }

  &__box {
    position: relative;
    height: 100vh;
    overflow: hidden;
  }

  &__container {
    max-width: 1094px;
    margin: 0 auto;
  }

  &__head {
    display: flex;
    justify-content: space-between;
    margin-bottom: 52px;
  }

  &__footer {
    // display: flex;
    // justify-content: center;
    position: absolute;
    left: 0;
    right: 0;
    top: 160px;
    transition: all 1s ease;
  }

  &__title {
    font-weight: 400;
    font-size: 44px;
    line-height: 53px;
  }

  &__descr {
    font-size: 18px;
    line-height: 25px;
    font-weight: 400;
    max-width: 414px;
  }

  &__row {
    display: flex;
    max-width: 1094px;
    margin: 0 0 0 calc((100vw - 1094px) / 2);
    transition: margin 2.5s ease, max-width 3s ease-in;

    // &:hover {
    //   margin: 0 0 0 calc(100vw - 1094px);
    // }

    // margin: 0 auto;
    // height: 100vh;
  }

  &__menu {
    // background: blue;
    // width: 26%;
    width: 0;
  }

  &__image {
    width: 100%;
    position: relative;
    height: 100vh;
    // padding-bottom: 48%;

    img {
      // max-width: 100%;
      position: absolute;
      height: 100%;
      width: inherit;
      right: 0;
      top: 0;
      object-fit: cover;
      z-index: 5;

      @media (max-width: 992px) {
        // height: 50%;
        // top: 50%;
        object-fit: contain;
      }

      @media (max-width: 480px) {
        object-fit: contain;
        bottom: 0;
        top: 50%;
        height: initial;
      }
    }
  }
}

.cleaning-menu {
  flex: 0 0 375px;
  max-width: 375px;
  width: 375px;
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;

  @media (max-width: 1200px) {
    padding: 35px 25px 45px 25px;
    width: 280px;
    flex: 0 0 280px;
  }

  @media (max-width: 992px) {
    bottom: 0;
    width: 100%;
    flex: 0 1 100%;
    // height: 50%;
    max-width: initial;
  }

  @media (max-width: 480px) {
    height: 100%;
  }

  color: $light;
  background: $brand-color;
  font-weight: 500;
  // font-size: 16px;
  line-height: 130%;
  height: 100%;
  // width: 375px;
  padding: 35px 60px 35px 36px;
  transform: translate(-100%, 0);
  // visibility: hidden;
  transition: all 0.7s ease 0s;

  // &.active {
  //   transform: translate(0, 0);
  //   visibility: visible;
  // }

  &__body {
    display: flex;
    flex-direction: column;
    height: 100%;
    justify-content: center;
    overflow: hidden;
    
    @media (max-width: 992px) {
      position: absolute;
      top: 0;
    }

    @media (max-width: 600px) {
      top: -25%;
      width: 100%;
    }
  }

  &__title {
    font-weight: 500;
    font-size: 16px;
    line-height: 21px;
    flex: 0 1 50%;
  }
  &__list {
    @media (max-width: 480px) {
      margin-top: 30px;
    }

    li {
      font-weight: 400;
      font-size: 44px;
      line-height: 120%;
      opacity: 0.7;
      transition: all 0.7s, transform 0.7s 1.8s;
      position: relative;

      @media (max-width: 1200px) {
        font-size: 36px;
      }

      @media (max-width: 600px) {
        font-size: 26px;
        margin-bottom: 7px;

        &:last-child {
          margin-bottom: 0;
        }
      }

      &.active {
        font-family: 'TTTravels-I';
        transition: all 0.7s, transform 0.7s 1.8s;
        opacity: 1;
        transform: translate(55px, 0);

        @media (max-width: 1200px) {
          transform: translate(45px, 0);
        }

        @media (max-width: 600px) {
          transform: translate(35px, 0);
        }
      }

      &:before {
        // content: '→';
        content: '';
        transition: all 0.3s;
        position: absolute;
        background: url('@/assets/images/icons/arrow.svg') center no-repeat;
        left: -55px;
        height: 100%;
        // width: 15%;
        width: 35px;

        @media (max-width: 1200px) {
          left: -45px;
        }

        @media (max-width: 600px) {
          left: -35px;
          width: 30px;
        }
      }

      &:hover {
        cursor: pointer;
      }
    }
  }
}

// &__row {
//     // display: flex;
//     // justify-content: space-between;
//     // margin: 0 auto;
//     // transition: all 2s ease-in-out;
//   }

//   &__column {
//     &:nth-child(1) {
//       // flex: 0 0 375px;
//       // flex: 0 0 100%;
//       // width: 0;
//     }

//     &:nth-child(2) {
//       // flex: 1 1 auto;
//       // flex: 0 1 100%;
//       // max-width: 1094px;
//     }
//   }

//   &__image {
//     text-align: right;
//     position: relative;
//     height: 100vh;

//     &.active img {
//       transform: translate(0, 0);
//       opacity: 1;
//     }

//     img {
//       max-width: 100%;
//       position: absolute;
//       width: 100%;
//       height: 100%;
//       top: 0;
//       left: 0;
//       object-fit: cover;
//       transform: translate(0, 10%);
//       transition: all 0.6s ease 0s;
//       opacity: 0;
//     }
//   }

// &.active {
//   // overflow: hidden;
//   .cleaning__container {
//     margin-bottom: -20%;
//     transition: all 2s ease-in-out;
//   }

//   .cleaning__row {
//     // max-width: 100%;
//     // margin: 0;
//     // justify-content: space-between;
//     margin: 0;
//     transition: all 2s ease-in-out;

//     .cleaning__column {
//       &:nth-child(1) {
//         width: 26%;
//         // flex: 0 0 26%;
//         transition: all 2s;
//         // animation: 4s linear 0s alternate move_eye;
//       }

//       &:nth-child(2) {
//         flex: 1 1 74%;
//         max-width: 100%;
//       }
//     }
//   }
// }
</style>
























