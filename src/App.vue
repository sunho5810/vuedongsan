<template>
  <div class="menu">
    <a href="javascript:void(0);" v-for="menu in menuList" :key="menu">{{menu}}</a>
  </div>

  <div v-for="(item, i) in products" :key="i">
    <h4>{{ item.name }}</h4>
    <p>{{ item.price }} 만원</p>
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
        },
        {
          id: 1,
          name: "일산동구원룸",
          price: 60,
        },
        {
          id: 2,
          name: "팔달구원룸",
          price: 70,
        },
      ],
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

</style>
