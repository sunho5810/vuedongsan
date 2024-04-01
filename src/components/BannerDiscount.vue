<template>
  <div class="discount">
    <h4>지금 결제하면 20% 할인!!</h4>
  </div>
</template>

<script>
export default {
  /* 
    name을 지어주는게 보편적이다.
    **최근 뷰는 최소 두단어로 컴포넌트 명을 만드는 것을 강요한다.
  */
  name: "BannerDiscount",
};
</script>

<style lang="scss">
.discount {
  background-color: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}
</style>
