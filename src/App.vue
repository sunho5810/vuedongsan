<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <div>
    <h4>{{ products[0].name }}</h4>
    <p>{{ products[0].price }} 만원</p>
  </div>
  <div>
    <h4>{{ products[1].name }}</h4>
    <p>{{ products[1].price }} 만원</p>
  </div>
  <div>
    <h4>{{ products[2].name }}</h4>
    <p>{{ products[2].price }} 만원</p>
  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return {
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

</style>
