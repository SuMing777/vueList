<template>
  <div class="header">
    <button
      class="btn"
      :class="{ 'btn-ck': isActive == 1 }"
      @click="btnClick(1)"
    >列表视图</button>
    <button
      class="btn"
      :class="{ 'btn-ck': isActive == 2 }"
      @click="btnClick(2)"
    >网格视图</button>
    <input
      class="input"
      type="text"
      @input="childInput"
      v-model="value"
      placeholder="请输入列表中的关键字进行搜索"
    />
    <button
      class="btn"
      :class="{ 'btn-ck': btnActive == 1 }"
      @click="setOrderType(1, 1)"
    >列表升序</button>
    <button
      class="btn"
      :class="{ 'btn-ck': btnActive == 2 }"
      @click="setOrderType(2, 2)"
    >列表降序</button>
  </div>
</template>

<script>
function debounce(func, wait){
  let timeout;
  return function(event){
    clearTimeout(timeout);
    timeout = setTimeout(() => {
      func.call(this, event);
    }, wait);
  }
}
export default {
  name: "navHeader",
  data() {
    return {
      isActive: 1,
      btnActive: 1,
      orderType: 0,
      type: 0,
      value: ''
    };
  },
  methods: {
    btnClick(index) {
      this.isActive = index;
      if (index === 1) {
        this.$emit("type", 1);
      } else {
        this.$emit("type", 2);
      }
    },
    setOrderType(orderType, index) {
      this.orderType = orderType;
      this.btnActive = index;
      if (orderType === 1) {
        this.$emit("orderType", 1);
      } else {
        this.$emit("orderType", 2);
      }
    },
    childInput:debounce(function(){
      this.$emit('input', this.value);
    }, 500)
  },
};
</script>

<style scoped>
.header {
  border: 1px solid black;
  width: 650px;
  height: 70px;
  display: flex;
  align-items: center;
}
.btn {
  width: 80px;
  height: 40px;
  margin-left: 20px;
  color: black;
  font-weight: bold;
  border-radius: 8px;
}
.input {
  height: 30px;
  padding: 0;
  margin-left: 20px;
  width:200px;
  border-radius: 4px;
  border-color: limegreen;
}
input::-webkit-input-placeholder {
  color:limegreen;
}
.btn-ck {
  background-color: orange;
}
</style>
