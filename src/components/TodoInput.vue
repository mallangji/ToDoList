<template>
  <div>
    <div class="btn addItem" @click="showInput = 1" v-bind:class="{hidden : showInput == 1}">
      <i class="addBtn fa fa-plus"></i>
      일정 추가
    </div>

    <div v-if="showInput == 1">
      <div>
        <input
          class="message"
          type="text"
          v-model="newTodoItem"
          placeholder="Type what you have to do"
          v-on:keyup.enter="addTodo"
        />
      </div>
      <div class="btnWrap state">
        <button class="btn upload" v-on:click="addTodo">일정 등록</button>
        <button class="btn cancel" @click="showInput = 0">취소</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodoItem: "",
      showInput: 0
    };
  },
  created() {
    this.showInput = 0;
  },
  methods: {
    //입력받은 텍스트 로컬스토리지에 저장
    addTodo() {
      //input에 입력된 텍스트가 있으면
      if (this.newTodoItem !== "") {
        var value = this.newTodoItem && this.newTodoItem.trim();
        this.$emit("addTodo", value);
        this.clearInput();
        this.showInput = 0;
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
.btn.addItem {
  font-size: 15px;
  vertical-align: middle;
}
.btn.addItem.hidden {
  display: none;
}
.btn.addItem .addBtn {
  margin-right: 10px;
  color: #de4343;
}

.message {
  display: block;
  padding: 10px 5px;
  margin-bottom: 10px;
  width: 100%;
  font-size: 15px;
}
.message:focus {
  outline: none;
}

.btnWrap.state .btn {
  padding: 8px 13px;
  font-size: 15px;
  border: none;
}
.btnWrap.state .btn.upload {
  color: #fff;
  border-radius: 3px;
  background-color: #ed4343;
}
</style>