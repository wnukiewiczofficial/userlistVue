<template>
  <v-table
    theme="dark"
    density="compact"
    fixed-header
    class="text-left w-75 mx-auto rounded-xl"
    v-if="data"
  >
    <thead>
      <tr>
        <th class="font-weight-bold text-subtitle-1">Username</th>
        <th class="font-weight-bold text-subtitle-1">Location</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="user in data" :key="user.displayName">
        <td>{{ user.displayName || "---" }}</td>
        <td>{{ user.location || "---" }}</td>
      </tr>
    </tbody>
  </v-table>
  <p v-if="!data" class="text-center text-h5">Fetching data...</p>
</template>

<script>
export default {
  name: "MyTable",
  props: {
    data: Array,
  },
};
</script>
