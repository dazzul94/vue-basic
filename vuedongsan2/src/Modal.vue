<template>
    <div class="black-bg" v-if="모달창열렸니">
      <div class="white-bg">
        <h4>{{원룸들[누른거].title}}</h4>
        <img :src="원룸들[누른거].image" class="room-img">
        <p>{{원룸들[누른거].content}}</p>
        <input v-model="month" @blur="focus = false">
        <p>{{month}}개월선택함: {{원룸들[누른거].price * month}} 원</p>
        <Discount/>
        <button @click="$emit('closeModal')">닫기</button>
      </div>
    </div>  
</template>

<script>
import Discount from './Discount.vue'
export default {
    name: 'Modal',
    data() {
      return {
        month : 1,
      }
    },
    watch : {
      month(a) {
        if(a != '') {
          if(isNaN(a)) {
            alert("숫자만 입력해주세요.");
            this.month = 1;
          } else {
            if(a >= 13) {
              alert('13이상 입력하지 마셈');
              this.month = 1;
            }
          }
        }
      },
    },
    updated() {
      if(this.month == 2) {
        alert("우리는 2개월은 안쳐줌");
        this.month = 1;
      }
    },
    props : {
        원룸들 : Array,
        누른거 : Number,
        모달창열렸니 : Boolean,
    },
    components: {
        Discount : Discount,
    }
}
</script>

<style>

</style>