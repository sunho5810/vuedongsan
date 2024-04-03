<template>
  <div class="modal" v-if="modal === true">
    <div class="modal-container">
      <img :src="products[currentIdx].image" alt="" />
      <h4>{{ products[currentIdx].title }}</h4>
      <p>{{ products[currentIdx].content }}</p>

      <!-- v-model 1 : $event 는 js에서의 event매개변수와 같음 @input="month = $event.target.value"와 같이 사용
        form요소에 v-model을 사용하면 위에 사용한것과 같은 효과를 가져올 수 있다.
        *초기값과 받아올 값의 자료형을 잘 맞춰줘야 함
        **폼요소로 값을 받아오면 문자열로 받아오기 때문에 v-model.number와 같이 자료형을 변환해 줄 수 있다.
      -->
      <!-- watcher 1 : 데이터를 감시하는 함수
        특히 사용자에게서 input으로 데이터를 입력 받아 유효성 검사를 할 때 자주 사용한다.
      -->
      <input type="text" v-model="month">
      <p>{{ month }}개월 선택함 : {{ month * products[currentIdx].price }} 만원</p>

      <p>신고수 : {{ products[currentIdx].report }}</p>
      <button type="button" @click="$emit('closeModal')">닫기</button>
      <!-- ex) props 3 : props는 read-only
        closeModal함수 형식 말고 modal = false 이런식으로 값의 재할당을 금지한다. -->
    </div>
  </div>
</template>

<script>
export default {
  name: "ModalDetail",
  /* props 2 : 부모에게서 받은 데이터를 저장한다. 
    data명: 자료형(굳이굳이 사용할 필요는 없지만 적어주는게 좋다.)
  */
  data(){
    return{
      month: 1,
    }
  },
  /* 데이터를 감시할 수 있다. ex) observer */
  watch: {
    /* watcher 2 : 감시하고 싶은 데이터 이름으로 함수를 만들어준다.
      파라미터는 (데이터, 변경 전 데이터)로 두개까지 받아올 수 있다.
    */
    month(data, before){
      if(data >= 13){
        alert("13이상 입력하지 마세요");
        this.month = before;
      } else if(typeof(data) === "string"){
        alert("숫자만 입력해주세요.");
        this.month = before;
      }
    }
  },
  props: {
    products: Array,
    currentIdx: Number,
    modal: Boolean,
  }
};
</script>

<style lang="scss">
.modal {
  position: fixed;
  padding: 20px;
  width: 100%;
  height: 100%;
  background-color: rgba(black, 0.5);
  &-container {
    width: 100%;
    padding: 20px;
    background-color: white;
    border-radius: 8px;
  }
}
</style>
