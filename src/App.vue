<template>

  <div class="black-bg" v-if="modalState == true">
    <div class="white-bg">
      <h4>상세페이지</h4>
      <p>내용</p>
      <button @click="modalState = false">닫기</button>
    </div>

  </div>

  <div class="menu">
    <a v-for="menu in menuList" :key="menu">{{menu}}</a>
  </div>

  <img alt="Vue logo" src="./assets/logo.png">


  <div v-for="(data,idx) in oneRoomList" :key="data"> 
    <img :src=" data.image" class="room-img" alt="" />
    <h4 @click="modalState = true">{{data.title}}</h4>    
    <p>{{ data.price }} 만원</p>
    <button @click="increase(idx)">허위매물 신고</button> <span>신고수 : {{altCnt[idx]}}</span>
  </div>
  <!-- <div v-for="(product,idx) in products" :key="product"> 
    <img src="./assets/images/room0.jpg" class="room-img" alt="" />
    <h4 @click="modalState = true">{{product}}</h4>    
    <p>{{ price[idx] }} 만원</p>
    <button @click="increase(idx)">허위매물 신고</button> <span>신고수 : {{altCnt[idx]}}</span>
  </div> -->

</template>

<script>

import dataList from './assets/oneroom.js';

export default {
  name: 'App',
  data(){
    return {
      oneRoomList: dataList,
      modalState: false,
      menuList: ['Home', 'Shop', 'About'],
      price: [50, 70, 100],
      products: ['역삼동', '천호동', '마포구'],
      altCnt: [0, 0, 0]
    }
  },
  methods: {
    increase(idx){
      this.altCnt[idx]++;
    }
  },
  components: {
  }
}
</script>

<style>

body {
  margin: 0
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

.room-img {
  width: 100%;
  margin-top: 40px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}

</style>
