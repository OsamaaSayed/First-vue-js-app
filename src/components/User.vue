<template>
  <div class="text-white mt-10">
    <h1 class="text-3xl mb-4">User Component</h1>
    <hr />
    <div class="mt-5">
      <table class="table w-[80%] text-center p-5 m-auto mt-5">
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
          <tr v-for="(user, index) in userData" :key="user.name">
            <td>{{ user.name }}</td>
            <td>{{ user.age }}</td>
            <td>{{ user.address }}</td>
            <td>{{ user.role }}</td>
            <td>
              <button
                class="btn bg-red-600 text-white border-none"
                @click="deleteRow(index, 'user')"
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
  name: "User",
  // props: {
  //   userData: {
  //     type: Array,
  //     required: true,
  //   },
  //   deleteRow: {
  //     type: Function,
  //     required: true,
  //   },
  // },
  props: ["userData", "deleteRow"],
};
</script>

<style></style>
