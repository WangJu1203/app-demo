<template>
  <div>
    List User

    <ul>
      <li v-for="(item, index) in response" :key="index">
        {{ item }}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "AppDemoListUser",

  data() {
    return {
      response: [],
    };
  },
  created() {
    axios.get("https://fakestoreapi.com/users").then((res) => {
      //   console.log("2");
      this.response = [res.data];
    });
  },

  mounted() {
    console.log("1");
  },
  watch: {
    response: function () {
      //   console.log("3");
      //   console.log(this.response);
    },
  },
  updated() {
    // console.log("4");
    // console.log(this.response);
  },

  methods: {},
};
</script>

<style lang="scss" scoped></style>
