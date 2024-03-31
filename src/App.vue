<template>
  <!-- v-for 사용 시 key값은 필수 -->
  <div class="menu">
    <a href="javascript:void(0);" v-for="menu in menuList" :key="menu">{{menu}}</a>
  </div>

  <!-- v-for 사용 시 밑에 i처럼 인덱스를 받아올 수 있음 -->
  <div v-for="(item, i) in products" :key="i">
    <h4>{{ item.name }}</h4>
    <p>{{ item.price }} 만원</p>
    <!-- v-on은 @로 축약 가능 -->
    <button type="button" v-on:click="increase(i)">허위매물신고</button><span>신고수 : {{ item.report }}</span>
  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return {
      menuList: ["Home", "Shop", "About"],
      products: [
        {
          id: 0,
          name: "성동구원룸",
          price: 50,
          report: 0,
        },
        {
          id: 1,
          name: "일산동구원룸",
          price: 60,
          report: 0,
        },
        {
          id: 2,
          name: "팔달구원룸",
          price: 70,
          report: 0,
        },
      ],
    }
  },
  /* 함수 만드는 공간 */
  methods: {
    increase(i){
      /* data안에 있는 데이터를 사용하고 싶으면 this로 불러올 수 있음. */
      this.products[i].report++;
    }
  },
  components: {
  }
}
</script>

<style lang="scss">
#app{
  text-align: center;
}
.menu{
  background-color: darkslateblue;
  padding: 15px;
  border-radius: 5px;

  a{
    color: white;
    padding: 10px;
  }
}

button{
  cursor: pointer;
}

</style>
