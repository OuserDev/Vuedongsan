<template>
  <div>
    <!-- 보통은 :key에 index 넣는게 관습적임 -->
    <img :src="원룸.image" class="room-img" />
    <h4 @click="모달창열기발신">
      {{ 원룸.title }}
    </h4>
    <p>{{ 원룸.price }} 만원</p>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    원룸: Object
  },
  methods: {
    모달창열기발신() {
        this.$emit('모달창열기발신', this.원룸.id);
    }
  }
};
</script>

<style></style>