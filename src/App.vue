<template>
  <Test />

  <hr />
  <div class="menu">
    <a v-for="(a, i) in 메뉴들" :key="i">{{ a }}</a>
  </div>
  <Discount v-if="showDiscount == true" />
  <button @click="priceSort">가격순정렬</button>
  <button @click="sortBack">되돌리기</button>
  <transition name="fade">
    <Modal
      :원룸들="원룸들"
      :누른거="누른거"
      :모달창열렸니="모달창열렸니"
      @closeModal="모달창열렸니 = false"
    />
  </transition>
  <!-- <div class="start" :class="{ end: 모달창열렸니 }">
    <Modal
      :원룸들="원룸들"
      :누른거="누른거"
      :모달창열렸니="모달창열렸니"
      @closeModal="모달창열렸니 = false"
    />
  </div> -->
  <Card
    v-for="(a, i) in 원룸들"
    :key="i"
    :원룸="원룸들[i]"
    @openModal="
      모달창열렸니 = true;
      누른거 = $event;
    "
  />
</template>

<script>
import data from "./oneroom";
import Discount from "./Discount.vue";
import Modal from "./Modal.vue";
import Card from "./Card.vue";
import Test from "./Test.vue";

export default {
  name: "App",

  // 데이터 보관함
  data() {
    return {
      price1: 60,
      color: "color : red",
      메뉴들: ["Home", "Shop", "About"],
      products: ["역삼동원룸", "천호동원룸", "마포구원룸"],
      신고수: [1, 2, 3],

      // UI
      모달창열렸니: false,
      showDiscount: true,

      // 상품데이터
      원룸들오리지널: [...data], // 데이터 사본을 만드는 방법
      원룸들: data,

      // 클릭한 번호
      누른거: 0,

      예스올노: false,

      // 테스트
      open: false,
    };
  },
  methods: {
    increase(i) {
      this.신고수[i] += 1;
    },
    priceSort() {
      this.원룸들.sort(function (a, b) {
        return a.price - b.price;
      });
    },
    sortBack() {
      // 데이터 원본 보존을 위해 !
      this.원룸들 = [...this.원룸들오리지널]; // 복사본을 넣어야함
    },
  },

  // HTML 렌더링 전 데이터만 존재할 때
  // created() {

  // },

  // HTML 렌더링된 후
  mounted() {
    // this를 쓸 땐 arrow 함수를 써야함 ❗️
    // setTimeout(() => {
    //   this.showDiscount = false;
    // }, 3000);
  },

  components: {
    Discount,
    Modal,
    Card,
    Test,
  },
};
</script>

<style>
/* transition 입장 */
.fade-enter-from {
  opacity: 0;
}
.fade-enter-active {
  transition: all 1s;
}
.fade-enter-to {
  opacity: 1;
}
/* transition 입장 */
.fade-leave-from {
  opacity: 1;
}
.fade-leave-active {
  transition: all 1s;
}
.fade-leave-to {
  opacity: 0;
}

/* .start {
  opacity: 0;
  transition: all 1s;
}
.end {
  opacity: 1;
} */

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
}
.room-img {
  width: 100%;
  margin-top: 40px;
}
/* .black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
} */
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
</style>
