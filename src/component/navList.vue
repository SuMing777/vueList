<template>
  <ul class="list-table">
    <li
      v-for="p in filterPersons"
      :key="p.id"
      class="list-row"
      :class="{'list-area' : isActive == 2}"
      :style="randomRgb()"
    >{{p.text}}</li>
  </ul>
</template>

<script>
export default {
  name: "navList",
  props: {
    message: {},
    order: {},
    value: {},
  },
  data() {
    return {
      persons: [
        { id: 1, text: "Aquamarine" },
        { id: 2, text: "Hotpink" },
        { id: 3, text: "Gold" },
        { id: 4, text: "Crimson" },
        { id: 5, text: "Blueviolet" },
        { id: 6, text: "Lightblue" },
        { id: 7, text: "flowerblue" },
        { id: 8, text: "Skyblue" },
        { id: 9, text: "Burlywood" },
        { id: 10, text: "orangered" },
      ],
      isActive: 1,
      orderType: 0,
      serchName: "",
      childrenType: "",
    };
  },
  computed: {
    filterPersons() {
      const { serchName, persons, orderType } = this;
      let fPersons;
      fPersons = persons.filter((p) => p.text.indexOf(serchName) !== -1);
      if (orderType !== 0) {
        fPersons.sort(function (p1, p2) {
          if (orderType === 2) {
            return p2.id - p1.id;
          } else {
            return p1.id - p2.id;
          }
        });
      }
      return fPersons;
    },
  },
  watch: {
    message(val) {
      this.childrenType = val;
      this.isActive = val;
    },
    order(val) {
      this.orderType = val;
    },
    value(val) {
      this.serchName = val;
    },
  },
  methods: {
    randomRgb() {
      let R = Math.floor(Math.random() * 250);
      let G = Math.floor(Math.random() * 250);
      let B = Math.floor(Math.random() * 250);
      let A = 0.5;
      return {
        background: `rgba(${R},${G},${B},${A})`,
        color: `rgb(${B},${R},${G})`,
        border: `2px solid rgb(${G},${G},${R})`,
      };
    },
  },
};
</script>

<style scoped>
.list-table {
  border-bottom: 1px solid black;
  border-left: 1px solid black;
  border-right: 1px solid black;
  width: 650px;
  list-style: none;
  padding: 0;
  margin: 0;
  height: 775px;
  overflow: hidden;
}
.list-row {
  height: 50px;
  line-height: 50px;
  width: 500px;
  margin: 20px auto;
  text-align: center;
  font-weight: bold;
}
.list-area {
  display: inline-block;
  height: 100px;
  width: 100px;
  margin-left: 22px;
  margin-top: 20px;
  line-height: 100px;
  text-align: center;
}
</style>