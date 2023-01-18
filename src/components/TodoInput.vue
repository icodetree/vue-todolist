<template>
  <div class="inputBox shadow">
    <input
      type="text"
      v-model="newTodoItem"
      placeholder="Type what you have to do"
      v-on:keyup.enter="addTodo"
    />
    <span class="addContainer" v-on:click="addTodo">
      <font-awesome-icon icon="fa-solid fa-plus" class="addBtn" />
    </span>

    <!-- 경고팝업
    <modal v-if="showModal" @close="showModal = false">
      <slot name="header">
        <h3>알림</h3>
      </slot>
      <slot name="footer" @click="showModal = false">
        <span>
          할 일을 입력하세요!
          <font-awesome-icon icon="closeModalBtn fa-solid fa-xmark" />
        </span>
      </slot>
    </modal> -->
  </div>
</template>
<script>
export default {
  props: ["propsdata"],
  data() {
    return {
      newTodoItem: "",
    };
  },
  methods: {
    addTodo() {
      if (this.newTodoItem !== "") {
        let value = this.newTodoItem && this.newTodoItem.trim();
        // localStorage.setItem(value, value);
        this.$emit("addTodo", value);
        this.clearInput();
      }
    },
    clearInput() {
      this.newTodoItem = "";
    },
  },
  components: {},
};
</script>
<style scoped>
input:focus {
  outline: none;
}
.inputBox {
  background-color: #fff;
  height: 50px;
  line-height: 50px;
  border-radius: 5px;
}
.inputBox input {
  border-style: none;
  font-size: 0.9rem;
}
.addContainer {
  float: right;
  background: linear-gradient(to right, #6478fb, #8763fb);
  display: block;
  width: 3rem;
  border-radius: 0 5px 5px 0;
}
.addBtn {
  color: #fff;
  vertical-align: middle;
}
</style>
