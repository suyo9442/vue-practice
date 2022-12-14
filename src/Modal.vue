<template>
  <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
      <img :src="원룸들[누른거].image" class="room-img" />
      <h4>{{ 원룸들[누른거].title }}</h4>
      <p>{{ 원룸들[누른거].content }}</p>
      <!-- <input @input="month = $event.target.value"/> <span> 개월</span> -->
      <input v-model="month" /> <span> 개월</span>
      <p>{{ month + "개월 선택함" + ": " + 원룸들[누른거].price * month }}</p>

      <button @click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  updated() {
    console.log(1);
    if (this.month === 2) {
      console.log(2);
    }
  },

  data() {
    return {
      month: 0,
    };
  },
  watch: {
    month(a) {
      if (a > 13) {
        alert("12개월 미만으로 입력해주삼");
      }

      // else if (typeof(a) === ) {
      //     alert('숫자만 입력해주삼')
      // }
    },
  },
  name: "Modal",
  props: {
    원룸들: Array,
    누른거: Number,
    모달창열렸니: Boolean,
  },
};
</script>

<style></style>
