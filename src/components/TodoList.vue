<template>
  <section>
    <transition-group name="list" tag="ul">
      <li class="shadow" v-for="(todoItem, index) in propsdata">
        <i class="checkBtn fa fa-check" aria-hidden="true"></i>
        {{todoItem}}
        <span
          type="button"
          class="removeBtn"
          @click="removeTodo(TodoItem, index)"
        >
          <i class="fa fa-trash-o" aria-hidden="true"></i>
        </span>
      </li>
    </transition-group>
  </section>
</template>

<script>
export default {
  props: ["propsdata"],
  methods: {
    //선택한 할일 로컬 스토리지와 뷰 데이터에서 삭제
    removeTodo(todoItem, index) {
      this.$emit("removeTodo", todoItem, index);
    }
  }
};
</script>

<style scoped>
ul {
  margin-top: 0;
  padding-left: 0;
  list-style-type: none;
  text-align: left;
}
li {
  display: flex;
  margin: 0.5rem 0;
  padding: 0 0.9rem;
  height: 50px;
  min-height: 50px;
  line-height: 50px;
  border-radius: 5px;
  background-color: wheat;
}
.checkBtn {
  margin-right: 5px;
  line-height: 45px;
  color: #62acde;
}
.removeBtn {
  margin-left: auto;
  color: #de4343;
}
.list-item {
  display: inline-block;
  margin-right: 10px;
}
.list-move {
  transition: transform 1s;
}
.list-enter-active,
.list-leave-active {
  transition: all 1s;
}
.list-enter,
.list-leave-to {
  opacity: 0;
  transform: translateY(30px);
}
</style>