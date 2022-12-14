<template>
  <div>
    <div v-for="(a, i) in oneroom" :key="i">
      <img :src="a.image" />
      <h4 @click="$emit('openModal', a.id)">
        {{ a.title }}
      </h4>
      <p>{{ a.price }}</p>
      <button @click="increase">허위매물신고</button>
      <span>신고수 : {{ count }}</span>
    </div>
  </div>
</template>
<script>
export default {
  name: "Card",

  props: {
    oneroom: Array,
    count: Number,
  },
};
</script>
<style></style>
