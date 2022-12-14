<template>
  <div>
    <Discount :sale="sale" />

    <button @click="priceSort">가격순정렬</button>
    <button @click="sortBack">되돌리기</button>

    <!-- v-bind:작명="보낼데이터명" -->
    <Card
      v-bind:oneroom="oneroom"
      :count="count"
      @openModal="
        open = true;
        target = $event;
      "
    />

    <div class="offEffect" :class="{ onEffect: open }">
      <Modal
        :oneroom="oneroom"
        :target="target"
        :open="open"
        @closeModal="open = false"
      />
    </div>
  </div>
</template>

<script>
import data from "@/oneroom";
import Discount from "@/Discount.vue";
import Modal from "@/components/Modal.vue";
import Card from "@/components/Card.vue";

export default {
  mounted() {
    const timeout = () => {
      this.sale--;

      if (this.sale === 0) {
        clearInterval(interval);
      }
    };

    var interval = setInterval(timeout, 100);
  },

  data() {
    return {
      count: 0,
      open: false,
      oneroom_origin: [...data],
      oneroom: [...data],
      target: 0,
      sale: 30,
    };
  },

  methods: {
    increase() {
      this.count++;
    },
    priceSort() {
      this.oneroom.sort((a, b) => b.price - a.price);
    },
    sortBack() {
      // 데이터 원본 보존을 항상 생각 💡 상태값에 복사한 것 조차도 ❗️
      this.oneroom = [...this.oneroom_origin];
    },
  },

  components: {
    Discount,
    Modal,
    Card,
  },
};
</script>

<style>
body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  top: 0;
  left: 0;
  padding: 20px;
}
.offEffect {
  opacity: 0;
  transition: all 1s;
}
.onEffect {
  opacity: 1;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
img {
  width: 100%;
}
</style>
