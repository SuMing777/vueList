<template>
  <div class="index">
    <navHeader
      v-on:type="getType"
      v-on:orderType="getOrderType"
      v-on:input="getValue"
    ></navHeader>
    <navList
      :message="type"
      :order="orderType"
      :value="value"
    ></navList>
  </div>
</template>

<script>
  import navHeader from './navHeader.vue';
  import navList from './navList.vue';
  export default {
    name:'parent',
    components:{
      navHeader,
      navList
    },
    data(){
      return{
        type: 0,
        orderType: 0,
        value: '',
      }
    },
    methods:{
      getType(data){
        this.type = data;
      },
      getOrderType(data){
        this.orderType = data;
      },
      getValue(data){
        this.value = data;
      },
    },
  }
</script>

<style scoped>
  .index{
    margin:70px auto;
    width:700px;
  }
</style>