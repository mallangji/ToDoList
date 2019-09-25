<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoList v-bind:propsdata="todoItems" @removeTodo="removeTodo"></TodoList>
    <TodoInput v-on:addTodo="addTodo"></TodoInput>
    <TodoFooter v-on:removeAll="clearAll"></TodoFooter>
  </div>
</template>

<script>
import TodoHeader from "./components/TodoHeader.vue";
import TodoInput from "./components/TodoInput.vue";
import TodoList from "./components/TodoList.vue";
import TodoFooter from "./components/TodoFooter.vue";

export default {
  data() {
    return {
      todoItems: [
        "사용방법은 '작업추가'버튼을 클릭하여 일정을 등록해 보세요.",
        "등록된 일정의 오른쪽 '휴지통' 아이콘을 클릭하면 해당일정이 삭제됩니다.",
        "등록된 일정을 전부 지우고 싶을땐 페이지 상단의 'All Clear'를 클릭해 주세요!"
      ] //데이터 속성 todoItems선언
    };
  },
  created() {
    if (localStorage.length > 0) {
      for (let i = 0; i < localStorage.length; i++) {
        this.todoItems.push(localStorage.key(i));
      }
    }
  },

  methods: {
    //로컬 스토리지에 데이터를 추가하는 로직
    addTodo(todoItem) {
      localStorage.setItem(todoItem, todoItem);
      this.todoItems.push(todoItem);
    },

    //목록 전체 지우기
    clearAll() {
      localStorage.clear();
      this.todoItems = [];
    },

    removeTodo(todoItem, index) {
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1);
    }
  },

  components: {
    TodoHeader: TodoHeader,
    TodoInput: TodoInput,
    TodoList: TodoList,
    TodoFooter: TodoFooter
  }
};
</script>

<style>
#app {
  width: 600px;
  margin: 0 auto;
  font-weight: 300;
  color: #202020;
}
</style>