<template>
  <div class="program column">
    <div class="program__inner">
      <h1 class="h1">{{ program.title }}</h1>
      <p>{{ program.text }}</p>
      <ul class="program__list">
        <li
          @click="showId(item)"
          v-for="item in program.list"
          :class="{ 'active': item.active }"
          :key="program.list.id"
        >
          <span :style="{backgroundColor : item.bgColor}" >
            <img :src="require(`@/assets/img/${item.img}.svg`)" :alt="item.img">
          </span>
          {{ item.text }}
        </li>
      </ul>
    </div>
  </div>
  <div class="description column">
    <svg width="720" height="834" fill="none" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 720 834"><path d="M0 76.059.001 0H720v373.891c0 50.414-29.147 96.282-74.788 117.693l-136.777 64.165c-33.049 15.503-36.38 61.207-5.928 81.338l173.175 114.487A98.81 98.81 0 0 1 720 834H.001V537.003a185.054 185.054 0 0 1 59.255-135.717l170.033-157.605c15.68-14.534 8.518-40.703-12.378-45.226L73.733 167.461C30.705 158.147 0 120.084 0 76.059Z" fill="#5A58CF"/></svg>
    <div class="description__wrapper">
      <div class="description__inner">
        <div
          v-for="(description, index) in descriptions"
          :style="{zIndex : descriptions.length - index }"
          :key="description.id"
          :class="['description-item', description.active ? 'active' : '']"
        >
          <div>
            <div class="title">
              <h2 class="h2">{{ description.title }}</h2>
              <img class="icon" :src="require(`@/assets/img/${description.img}.svg`)" :alt="description.img">
            </div>
            <h4 v-if="description.titleSecond" class="h4">
              {{ description.titleSecond }}
            </h4>
            <ul class="description-item__list">
              <li
                v-for="item in description.items"
                :key="item.id"
              >
              <span :style="{backgroundColor : item.bgColor }" >
                <svg width="10" height="8" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="m1.364 4.242 2.424 2.424 4.848-4.849" :stroke="item.checkColor" stroke-width="1.75" stroke-linecap="round" stroke-linejoin="round"/></svg>
              </span>
                {{ item.text }}
              </li>
            </ul>
            <a class="button" href="#">{{ description.buttonText }}</a>
            <p>Starting at ${{99}}/month</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
/*import HelloWorld from "./components/HelloWorld.vue'*/

export default {
  name: 'App',
  components: {
    /*HelloWorld*/
  },
  data() {
    return {
      activeIndex: 1,
      program: {
        title: 'The Found Program',
        text: 'There’s no one-and-done solution when it comes to sustainable weight care. With Found, five key factors come together on your journey to reach your goals',
        list: [
          { id: 1, img: 'icon-nav-doc', bgColor: '#5A58CF', text: 'Doctor', active: true },
          { id: 2, img: 'icon-nav-shoe', bgColor: '#408BFC', text: 'Coach', active: false },
          { id: 3, img: 'icon-nav-tel', bgColor: '#4F6258', text: 'App', active: false },
          { id: 4, img: 'icon-nav-pill', bgColor: '#F9D270', text: 'Medication', active: false },
          { id: 5, img: 'icon-nav-heart', bgColor: '#FBDECA', text: 'Community', active: false },
        ]
      },
      descriptions: [
        {
          id: 1,
          img: 'icon-cont-plus',
          title: 'Board-certified doctors',
          items: [
            { id: 1, text: 'Board-certified and specifically trained on weight loss medication', bgColor: '#E6E6F8', checkColor: '#5A58CF' },
            { id: 2, text: 'Virtual appointments, no in-person office visits required', bgColor: '#E6E6F8', checkColor: '#5A58CF' },
            { id: 3, text: 'Found doctors customize the program to your specific needs', bgColor: '#E6E6F8', checkColor: '#5A58CF' }
          ],
          buttonText: 'Continue',
          text: '99',
          active: true
        },
        {
          id: 2,
          img: 'icon-cont-shoe',
          title: 'Personal health coach',
          items: [
            { id: 1, text: 'Coaches tailor your movement and nutrition plan to fit your needs', bgColor: '#E2EEFF', checkColor: '#408BFC' },
            { id: 2, text: 'On-demand availability to answer all of your questions', bgColor: '#E2EEFF', checkColor: '#408BFC' },
            { id: 3, text: 'Build sustainable habits with the help of your coach', bgColor: '#E2EEFF', checkColor: '#408BFC' }
          ],
          buttonText: 'Continue',
          text: '99',
          active: false
        },
        {
          id: 3,
          img: 'icon-cont-tel',
          title: 'Found mobile app',
          items: [
            { id: 1, text: 'Keep track of your progress by logging your routines', bgColor: '#D4E7DD', checkColor: '#4F6258' },
            { id: 2, text: 'Coaches use logged routines to personalize your weight loss program', bgColor: '#D4E7DD', checkColor: '#4F6258' },
            { id: 3, text: 'Integrates with Apple Health and Google Fit', bgColor: '#D4E7DD', checkColor: '#4F6258' }
          ],
          buttonText: 'Continue',
          text: '99',
          active: false
        },
        {
          id: 4,
          img: 'icon-cont-pill',
          title: 'Prescription medication',
          titleSecond: 'Our medical team provides access to the widest set of prescriptions on the market, including (but not limited to):',
          items: [
            { id: 1, text: 'Board-certified and specifically trained on weight loss medication', bgColor: '#E6E6F8', checkColor: '#5A58CF' },
            { id: 2, text: 'Virtual appointments, no in-person office visits required', bgColor: '#E6E6F8', checkColor: '#5A58CF' },
            { id: 3, text: 'Found doctors customize the program to your specific needs', bgColor: '#E6E6F8', checkColor: '#5A58CF' }
          ],
          buttonText: 'Continue',
          text: '99',
          active: false
        },
        {
          id: 5,
          img: 'icon-cont-heart',
          title: 'Board-certified doctors',
          items: [
            { id: 1, text: 'Board-certified and specifically trained on weight loss medication', bgColor: '#E6E6F8', checkColor: '#5A58CF' },
            { id: 2, text: 'Virtual appointments, no in-person office visits required', bgColor: '#E6E6F8', checkColor: '#5A58CF' },
            { id: 3, text: 'Found doctors customize the program to your specific needs', bgColor: '#E6E6F8', checkColor: '#5A58CF' }
          ],
          buttonText: 'Continue',
          text: '99',
          active: false
        },
      ]

    }
  },
  methods : {
    showId(item){
      this.program.list.map(task => {
        if (task.active) {
          return task.active = false;
        }
      });
      item.active = !item.active;
      this.descriptions.map(task => {
        if (task.active) {
          return task.active = false;
        }
        if (task.id === item.id) {
          return task.active = true;
        }
      })
    },
    handleScroll(e) {
      console.log(e);
    },
    created() {
      window.addEventListener("scroll", this.handleScroll);
    }
  }
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Roboto+Serif:opsz@8..144&display=swap');

body {
  margin: 0;
  padding: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #10100E;
  display: flex;
  min-height: 100vh;
}
.h1 {
  font-weight: 700;
  font-size: 62px;
  line-height: 100%;
  letter-spacing: -0.02em;
  margin: 0;
}
.h2 {
  font-weight: 700;
  font-size: 28px;
  line-height: 1.46;
  margin: 0;
}
.h4 {
  font-size: 18px;
  line-height: 1.7;
}
.column {
  width: 50%;
}
.program {
  display: flex;
  justify-content: center;
  align-items: center;
  &__inner {
    width: 100%;
    max-width: 580px;
  }
  p {
    font-family: 'Roboto Serif', serif;
  }
  &__list {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    list-style-type: none;
    padding: 0 60px 0 0;
    li {
      display: flex;
      font-size: 18px;
      line-height: 1;
      align-items: center;
      padding: 12px 24px 12px 12px;
      background-color: #F6F6F6;
      border-radius: 100px;
      opacity: .7;
      &:not(.active) {
        cursor: pointer;
        &:hover {
          opacity: 1;
        }
      }
      &.active {
        font-weight: 700;
        background-color: lighten(#5A58CF, 26%);
        opacity: 1;
        pointer-events: none;
      }
      span {
        width: 28px;
        height: 28px;
        background-color: #E6E6F8;
        border-radius: 50%;
        display: flex;
        justify-content: center;
        align-items: center;
        margin-right: 10px;
      }
    }
  }
}

.description {
  position: relative;
  overflow: hidden;
  > svg {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: auto;
    object-fit: contain;
  }
  &__wrapper {
    z-index: 2;
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: stretch;
  }
  &__inner {
    position: relative;
    height: 100%;
    min-width: 452px;
  }
  &-item {
    position: absolute;
    left: 0;
    bottom: -10vh;
    transform: translateY(100%);
    width: 100%;
    border-radius: 10px;
    transition: all .5s ease;
    &.active {
      top: 50%;
      transform: translateY(-50%);
      transition: all .5s ease;
      > div {
        top: 50%;
        transform: translateY(-50%);
        transition: all .5s ease;
      }
    }
    > div {
      position: absolute;
      top: 0;
      padding: 51px 48px 48px 48px;
      border-radius: 10px;
      background-color: white;
      overflow: hidden;
      box-sizing: border-box;
      box-shadow: 0px 20px 40px rgba(47, 47, 47, 0.2);
      transition: all .5s ease;
    }
    .title {
      padding-left: 43px;
      position: relative;
      .icon {
        position: absolute;
        left: 0;
        top: 50%;
        transform: translateY(-50%);
      }
    }
    &__list {
      padding-left: 0;
      list-style-type: none;
      margin-bottom: 29px;
      li {
        position: relative;
        padding: 8px 0 8px 33px;
        font-size: 18px;
        line-height: 1.44;
        span {
          display: inline-block;
          width: 16px;
          height: 16px;
          background-color: #E6E6F8;
          border-radius: 50%;
          position: absolute;
          left: 4px;
          top: 11px;
        }
        svg {
          position: absolute;
          left: 50%;
          top: 50%;
          transform: translate(-50%, -50%);
        }
      }
    }
    .button {
      color: #fff;
      text-decoration: none;
      font-size: 16px;
      line-height: 1;
      display: block;
      transition: opacity .3s ease;
      padding: 15px 22px;
      background: #10100E;
      border-radius: 5px;
      text-align: center;
      border: none;
      &:hover {
        text-decoration: none;
        color: #fff;
      }
    }
    p {
      margin-top: 28px;
      margin-bottom: 0;
      font-size: 16px;
      text-align: center;
    }
  }
}
</style>
