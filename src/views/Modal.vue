<template>
  <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
      <h4>{{ 원룸들[누른거].title }}</h4>
      <p>{{ 원룸들[누른거].content }}</p>
      <!--<input @input= "month = $event.target.value">-->
      <input v-model.number="month" />
      <p>{{ month }}개월 선택함 : {{ 원룸들[누른거].price + month }} 만원</p>
      <img :src="원룸들[누른거].image" class="room-small" />
      <button @click="모달창닫기발신" class="bg-button">닫기</button>
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
  watch : {
  },
  props: {
    원룸들: Array,
    누른거: Number,
    모달창열렸니: Boolean,
  },
  methods: {
    모달창닫기발신() {
      this.$emit("모달창닫기발신");
    },
  },
  beforeUpdate() {
    if (this.month == 2) {
        alert("우리는 3개월 이상 해!")
        this.month = 1;
    } else if (isNaN(this.month) == true ) {
        alert("숫자만 입력하세요")
        this.month = 1;
    } else if (this.month >= 13) {
        alert("13이상 입력하지 마셈")
        this.month = 1;
        }
  }
};
</script>

<style>
.room-img {
  width: 100%;
  margin-top: 40px;
}

.room-small {
  width: 50%;
}
</style>
