<template>
  <div>
    <input
      type="text"
      v-model="newTodoItem"
      placeholder="Type what you have to do"
      v-on:keyup.enter="addTodo"
    />
    <span class="addContainer" v-on:click="addTodo">
      <i class="addBtn fa fa-plus" aria-hidden="true"></i>
    </span>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodoItem: ""
    };
  },
  methods: {
    //입력받은 텍스트 로컬스토리지에 저장
    addTodo() {
      //input에 입력된 텍스트가 있으면
      if (this.newTodoItem !== "") {
        var value = this.newTodoItem && this.newTodoItem.trim();
        this.$emit("addTodo", value);
        this.clearInput();
      }
    },

    //input 입력값 초기화
    clearInput() {
      this.newTodoItem = "";
    }
  }
};
</script>

<style scoped>
input:focus {
  outline: none;
}
.inputBox {
  height: 50px;
  line-height: 50px;
  border-radius: 5px;
  background-color: wheat;
}
.inputBox input {
  font-size: 0.9rem;
  border-style: none;
}
.addContainer {
  float: right;
  display: block;
  width: 3rem;
  border-radius: 0 5px 5px 0;
  background: linear-gradient(to right, #6478fb, #8763fb);
}
.addBtn {
  color: white;
  vertical-align: middle;
}
</style>