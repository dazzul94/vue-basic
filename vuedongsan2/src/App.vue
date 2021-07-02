<template>
  <div id="app">

    <div v-if="1==2">
      안녕하세요
    </div>
    <div v-else>
      안녕하세요2
    </div>

    <!-- 모달창 -->
   <Modal @closeModal="모달창열렸니 = false" :원룸들="원룸들" :누른거="누른거" :모달창열렸니="모달창열렸니"/>

    <div class="menu">
      <a v-for="(menu,i) in menus" :key="i">{{menu}}</a>
    </div>

    <Discount v-bind="오브젝트" />

    <img alt="Vue logo" src="./assets/logo.png">

    <!-- <div> 
      <img src="./assets/room0.jpg" class="room-img">
      <h4 @click="모달창열렸니=true" :style="스타일">{{products[0]}}</h4>
      <p>{{ price1 }} 만원</p>
      <button @click="increase1">허위매물신고</button> <span>신고수 : {{count1}}</span>
    </div>
    <div>
      <img src="./assets/room1.jpg" class="room-img">
      <h4 :style="스타일">{{products[1]}}</h4>
      <p>{{ price2 }} 만원</p>
      <button @click="increase2">허위매물신고</button> <span>신고수 : {{count2}}</span>
    </div>
    <div>
      <img src="./assets/room2.jpg" class="room-img">
      <h4 :style="스타일">{{products[2]}}</h4>
      <p>{{ price1 }} 만원</p>
      <button @click="increase3">허위매물신고</button> <span>신고수 : {{count3}}</span>
    </div> -->

    <Card @openModal="모달창열렸니 = true; 누른거 = $event" v-for="(원룸,j) in 원룸들" :key="j" :원룸="원룸들[j]"/>

    <!-- <div v-for="(prd,i) in products" :key="i">
      <h4 style="color:red">{{prd}}</h4>
      <p>{{price2}} 만원</p>
    </div> -->
  </div>
</template>

<script>
import {apple, apple2, data} from './oneroom.js'

import Discount from './Discount.vue'
import Modal from './Modal.vue'
import Card from './Card.vue'

export default {
  name: 'App',
  data() {
    return {
      // 데이터 보관함
      price1 : 60,
      price2 : 70,
      logo : '원룸샵',
      스타일 : 'color : blue',
      menus : ['Home', 'Shop', 'About'],
      products : ['역삼동원룸', '천호동원룸', '화곡동원룸'],
      count1: 0,
      count2: 0,
      count3: 0,
      신고수: [0,0,0],
      모달창열렸니 : false,
      apple: apple,
      apple2: apple2,
      원룸들: data,
      누른거: 0,
      오브젝트: {name: 'kim', age : 20}
    }
  },
  methods : {
    increase1() {
      this.count1 ++;
    },
    increase2() {
      this.count2 ++;
    },
    increase3() {
      this.count3 ++;
    }
  },
  components: {
    Discount : Discount,
    Modal : Modal,
    Card : Card,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.menu {
  background : darkslateblue;
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
body {
  margin :0
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%; height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed; padding: 20px;
}
.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
}
.discount {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}

</style>
