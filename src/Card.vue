<template>
  <div>
    <img :src="원룸.image" class="room-img" />
    <h4 @click="$emit('openModal', 원룸.id)">{{ 원룸.title }}</h4>
    <p>{{ 원룸.price }} 원</p>
    <button @click="declar">허위매물신고</button>
    <span>신고수 : {{ count }}</span>
  </div>
</template>

<script>
export default {
  name: "Card",
  data() {
    {
      return {
        count: 0,
      };
    }
  },
  props: {
    원룸: Object,
  },

  methods: {
    declar() {
      this.count++;
    },
  },
};
</script>

<style></style>
