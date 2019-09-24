<template>
  <div class="clearAllContainer">
    <span class="clearAllBtn" @click="clearTodo">Clear All</span>
  </div>
</template>

<script>
export default {
  methods: {
    //목록 전체 지우기
    clearTodo() {
      this.$emit("removeAll");
    }
  }
};
</script>

<style scoped>
.clearAllContainer {
  margin: 0 auto;
  width: 8.5rem;
  height: 50px;
  line-height: 50px;
  background-color: white;
  border-radius: 5px;
}
.clearAllBtn {
  display: block;
  color: #e20303;
}
</style>