<template>
  <div class="py-20 text-center">
    <h1 class="text-3xl mb-4 text-white">Form Component</h1>

    <hr />

    <form @submit.prevent="handleSubmit" class="mt-5">
      <input
        class="input input-bordered input-primary w-full max-w-xs block m-auto mb-3"
        type="text"
        v-model.lazy="formValues.name"
        placeholder="Name"
      />

      <input
        class="input input-bordered input-primary w-full max-w-xs block m-auto mb-3"
        type="number"
        v-model.lazy.number="formValues.age"
        placeholder="Age"
      />

      <input
        class="input input-bordered input-primary w-full max-w-xs block m-auto mb-3"
        type="text"
        v-model.lazy="formValues.address"
        placeholder="Address"
      />

      <select
        class="select select-bordered select-primary w-full max-w-xs mb-3"
        v-model="formValues.role"
      >
        <option class="text-white" disabled selected>Role</option>
        <option class="text-lg" value="user">User</option>
        <option class="text-lg" value="admin">Admin</option>
      </select>

      <button
        class="btn btn-primary block m-auto w-[15%] text-base"
        type="submit"
      >
        Submit
      </button>
    </form>



    <div class="text-center my-4">
      <button class="btn mr-3" id="user" @click="changeRole">User</button>
      <button class="btn" id="admin" @click="changeRole">Admin</button>
    </div>


    
    <div v-if="roleInput === 'user' && userData.length">
      <User :userData="userData" :deleteRow="deleteRow" />
    </div>

    <div v-if="roleInput === 'admin' && adminData.length">
      <Admin :adminData="adminData" :deleteRow="deleteRow" />
    </div>
  </div>
</template>

<script>
import User from "./User.vue";
import Admin from "./Admin.vue";

export default {
  name: "Form",
  components: {
    User,
    Admin,
  },
  data() {
    return {
      userData: [],
      adminData: [],
      formValues: {
        name: "",
        age: "",
        address: "",
        role: "",
      },
      roleInput: "",
    };
  },
  methods: {
    handleSubmit() {
      console.log(this.formValues);

      if (this.formValues.role === "user") {
        this.userData.push(this.formValues);
        console.log("User", this.userData);
      } else if (this.formValues.role === "admin") {
        this.adminData.push(this.formValues);
        console.log("Admin", this.adminData);
      } else;

      this.formValues = {
        name: "",
        age: "",
        address: "",
        role: "",
      };
    },

    changeRole(e) {
      if (e.target.id === "user") {
        return (this.roleInput = "user");
      } else if (e.target.id === "admin") {
        return (this.roleInput = "admin");
      }
    },

    deleteRow(index, role) {
      console.log("delete");
      if (role === "user") {
        this.userData.splice(index, 1);
      } else if (role === "admin") {
        this.adminData.splice(index, 1);
      }
    },
  },
};
</script>

<style></style>
