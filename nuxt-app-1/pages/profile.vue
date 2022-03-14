<template>
  <div>
    Hello dear <b style="color: red">{{ getUserInfo.name }}</b> you're in profile page
    <hr />
    This is your information:
    <br /><br />

    <!-- <v-data-table
      dense
      :headers="headers"
      :items="users"
      item-key="id"
      class="elevation-1"
    ></v-data-table> -->

    <table class="table">
      <thead class="v-data-table-header">
        <tr>
          <th scope="col">ID</th>
          <th scope="col">Name</th>
          <th scope="col">Email</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>{{ getUserInfo.id }}</td>
          <td>{{ getUserInfo.name }}</td>
          <td>{{ getUserInfo.email }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "Profile",
  middleware: "isAuthenticated",
  // data() {
  //   return {
  //     users: [
  //       {
  //         id: this.getUserInfo.id,
  //         name: this.getUserInfo.name,
  //         email: this.getUserInfo.email,
  //       },
  //     ],
  //     headers: [
  //       {
  //         text: "Users",
  //         align: "start",
  //         sortable: false,
  //         value: "id",
  //       },
  //       { text: "Name", value: "name" },
  //       { text: "Email", value: "email" },
  //     ],
  //   };
  // },
  computed: {
    getUserInfo() {
      return this.$store.getters.getUserInfo;
    },
  },
};
</script>
