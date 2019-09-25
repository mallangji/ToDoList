<template>
  <section>
    <transition-group name="list" tag="ul" class="wrap">
      <li class="shadow item" v-for="(todoItem, index) in propsdata" :key="index">
        <i class="checkBtn fa fa-check" aria-hidden="true"></i>
        {{todoItem}}
        <span
          type="button"
          class="removeBtn"
          @click="removeTodo(todoItem, index)"
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
.wrap {
  margin-top: 0;
  padding-left: 0;
  list-style-type: none;
  text-align: left;
}
.item {
  display: flex;
  padding: 15px 0;
  border-bottom: solid 1px #e7e7e7;
}
.checkBtn {
  margin-right: 5px;
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