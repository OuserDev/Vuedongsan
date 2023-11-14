<template>

<transition name = "fade">
  <Modal @모달창닫기발신="모달창닫기" :원룸들="원룸들" :누른거="누른거" :모달창열렸니="모달창열렸니"/>
</transition>

  <div class='menu'>
    <a v-for="a in 메뉴" :key="a">{{ a }}</a>
  </div>
  <Discount v-if="showDiscount == true" />

  <button @click="priceSort">가격순정렬</button>
  <button @click="alphabetSort">알파벳정렬</button>
  <button @click="sortBack">기본순정렬</button>
  <Card @모달창열기발신="모달창열기" :원룸="원룸들[index]" v-for="(원룸,index) in 원룸들" :key="index" />

</template>

<script>
import Card from '@/views/Card.vue'
import Discount from '@/views/Discount.vue'
import Modal from '@/views/Modal.vue'
import data from '@/assets/oneroom.js'
import { tSMethodSignature } from '@babel/types'

export default {
  name: 'HomeView',
  // eslint-disable-next-line
  data() {
    return {
      showDiscount : true,
      오브젝트: {name:"kim", age:20},
      누른거: 0,
      원룸들오리지널: [...data],
      원룸들: data,
      모달창열렸니: false,
      메뉴: ['Home', 'Products', 'About'],
      스타일: 'font-weight: bold; color: red;',
    }
  },
  methods: {
    increase (index) {
      this.신고수[index] += 1
    },
    모달창열기 (receiveId) {
      this.모달창열렸니 = true;
      this.누른거 = receiveId;
    },
    모달창닫기 () {
      this.모달창열렸니 = false;
    },
    priceSort() {
      this.원룸들.sort(function(a,b) {
        return a.price - b.price
      });
    },
    alphabetSort() {
      this.원룸들.sort((a,b) => a.title.localeCompare(b.title));
    },
    sortBack() {
      this.원룸들 = [...this.원룸들오리지널];
    }
  },
  components: {
    Discount: Discount,
    Modal: Modal,
    Card: Card
  }
}
</script>

<style>
body {
  margin:0
}

div {
  box-sizing:border-box;
}

.black-bg {
  width: 100%; height:100%;
  background: rgba(0,0,0,0.5);
  position: fixed; padding: 20px;
}

.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding-left: 10px;
}

.start {
  opacity:0;
  transition: all 1s;
}

.end {
  opacity:1;
}

.fade-enter-from { transform : translateY(-1000px); }
.fade-enter-active { transition: all 0.5s; }
.fade-enter-to { transform : translateY(0px); }
.fade-leave-from { opacity : 1; } 
.fade-leave-active { transition: all 0.5s; }
.fade-leave-to { opacity : 0; }

</style>
