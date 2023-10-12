<template>
  <div>
    List User

    <table class="table">
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">Firstname</th>
          <th scope="col">Phone</th>
          <th scope="col">Email</th>
          <th scope="col">Action</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in listUser" :key="index">
          <td>{{ index }}</td>
          <td>{{ item.username }}</td>
          <td>{{ item.phone }}</td>
          <td>{{ item.email }}</td>
          <td>
            <button class="btn btn-danger" @click="modalShow = !modalShow">
              Delete
            </button>
            <b-modal v-model="modalShow"
              >Are you sure delete this user have email =
              <b>{{ item.email }}</b>
            </b-modal>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "AppDemoListUser",

  data() {
    return {
      modalShow: false,
      listUser: [],
    };
  },
  async created() {
    await axios.get("https://fakestoreapi.com/users").then((res) => {
      console.log(res.data);
      //   console.log("2");
      this.listUser = res.data;
    });
  },

  mounted() {
    // console.log("1");
  },
  watch: {
    response: function () {
      //   console.log("3");
      //   console.log(this.response);
    },
  },
  updated() {
    // console.log("4");
    console.log(this.listUser);
  },

  methods: {},
};
</script>

<style lang="scss" scoped></style>
