<template>
  <div>
    <div class="black-bg" v-if="open === true">
      <div class="white-bg">
        <img :src="oneroom[target].image" />
        <h4>{{ oneroom[target].title }}</h4>
        <h4>{{ oneroom[target].content }}</h4>
        <h4>{{ oneroom[target].price }}</h4>
        <input @input="month = $event.target.value" />
        <p>{{ month }}</p>
        <br />
        <button @click="$emit('closeModal')">닫기</button>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Modal",

  data() {
    return {
      month: 1,
    };
  },

  methods: {
    // test() {
    //   console.log(1);
    // },
  },

  watch: {
    month(a) {
      if (isNaN(a) === true) {
        console.log("숫자를 입력하셈");
        this.month = 1;
      }
    },
  },

  props: {
    // props에 데이터타입 명시
    oneroom: Array,
    target: Number,
    open: Boolean,
  },
};
</script>
<style></style>
