<template>
  <div class="text-white mt-10">
    <h1 class="text-3xl mb-4">Admin Component</h1>

    <hr />
    <div class="mt-5">
      <table class="table w-[80%] text-center m-auto">
        <thead>
          <tr>
            <th>Name</th>
            <th>Age</th>
            <th>Address</th>
            <th>Role</th>
            <th></th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(admin, index) in adminData" :key="admin.name">
            <td>{{ admin.name }}</td>
            <td>{{ admin.age }}</td>
            <td>{{ admin.address }}</td>
            <td>{{ admin.role }}</td>
            <td>
              <button
                class="btn bg-red-600 text-white border-none"
                @click="deleteRow(index, 'admin')"
              >
                Delete
              </button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  name: "Admin",
  // props: {
  //   adminData: {
  //     type: Array,
  //     required: true,
  //   },
  //   deleteRow: {
  //     type: Function,
  //     required: true,
  //   },
  // },
  props: ["adminData", "deleteRow"],
};
</script>

<style></style>
