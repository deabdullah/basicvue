<template>
  <div class="q-pa-md">
    <q-table
      title="Users"
      :data="users.data"
      :columns="columns"
      row-key="login"
      selection="multiple"
      :selected.sync="selected"
    >
      <template v-slot:header-selection="scope"> Action </template>

      <template v-slot:body-selection="scope">
        <q-btn
          :to="'/user/' + scope.row.login"
          label="View User"
          outline
          color="purple"
        />
      </template>
    </q-table>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Users",
  data() {
    return {
      selected: [],
      methods: {
        Display() {
          console.log("clicked");
        },
      },
      columns: [
        {
          name: "name",
          required: true,
          label: "Name",
          align: "left",
          field: "login",
          sortable: true,
        },
        {
          name: "id",
          align: "center",
          label: "Id",
          field: "id",
          sortable: true,
        },
        { name: "type", label: "Type", field: "type", sortable: true },
        { name: "url", label: "Url", field: "url" },
      ],
      users: [],
    };
  },
  mounted() {
    axios
      .get("https://api.github.com/users")
      .then((response) => (this.users = response));
  },
};
</script>