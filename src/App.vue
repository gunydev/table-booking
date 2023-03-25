<script setup>
import { computed, reactive, ref } from "vue";

let isLoading = ref(false);
let inputName = ref("");

let data = reactive([
  {
    name: "Gun",
    tableNumber: "49",
    phone: "0837267797",
  },
  {
    name: "John",
    tableNumber: "11",
    phone: "0958953333",
  },
  {
    name: "Terry",
    tableNumber: "23",
    phone: "08475674333",
  },
  {
    name: "Gun",
    tableNumber: "49",
    phone: "0837267797",
  },
  {
    name: "John",
    tableNumber: "11",
    phone: "0958953333",
  },
  {
    name: "Terry",
    tableNumber: "23",
    phone: "08475674333",
  },
  {
    name: "Gun",
    tableNumber: "49",
    phone: "0837267797",
  },
  {
    name: "John",
    tableNumber: "11",
    phone: "0958953333",
  },
  {
    name: "Terry",
    tableNumber: "23",
    phone: "08475674333",
  },
  {
    name: "Gun",
    tableNumber: "49",
    phone: "0837267797",
  },
  {
    name: "John",
    tableNumber: "11",
    phone: "0958953333",
  },
  {
    name: "Terry",
    tableNumber: "23",
    phone: "08475674333",
  },
]);

const filterData = computed(() => {
  const search = inputName.value.toLowerCase();
  return inputName.value
    ? data.filter((e) => e.name.toLowerCase().includes(search))
    : data;
});
</script>

<template>
  <div class="landing-page">
    <h1>Wedding Table Booking System</h1>
    <p>Please enter the name of the guest you'd like to book a table for:</p>
    <div class="input-container">
      <input
        type="text"
        autocomplete="off"
        class="name-input"
        v-model="inputName"
      />
    </div>
    <div v-if="isLoading" class="loading-message">Loading...</div>
    <div v-if="!isLoading && !data.length" class="no-data-message">
      No data found for "{{ inputName }}"
    </div>
    <div v-if="!isLoading && data.length" class="data-table">
      <table>
        <thead>
          <tr>
            <th>Name</th>
            <th>Phone</th>
            <th>Table Number</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(item, index) in filterData" :key="index">
            <td>{{ item.name }}</td>
            <td>{{ item.phone }}</td>
            <td>{{ item.tableNumber }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<style scoped>
.landing-page {
  display: flex;
  flex-direction: column;
  align-items: center;
  /* justify-content: center; */
  height: 100vh;
}

.input-container {
  display: flex;
  align-items: center;
  justify-content: center;
}

.name-input {
  padding: 10px;
  margin-right: 10px;
  border-radius: 5px;
  border: 1px solid #ccc;
}

.search-btn {
  padding: 10px;
  border-radius: 5px;
  border: none;
  background-color: #4285f4;
  color: #fff;
  cursor: pointer;
}

.loading-message {
  margin-top: 20px;
  font-weight: bold;
}

.no-data-message {
  margin-top: 20px;
  font-weight: bold;
  color: #f00;
}

.data-table {
  margin-top: 20px;
  min-height: 100px;
}

table {
  border-collapse: collapse;
  width: 100%;
}

th,
td {
  padding: 10px;
  text-align: left;
  border-bottom: 1px solid #ccc;
}
td:nth-child(3){
  text-align: center;
}
th {
  background-color: #eee;
}
</style>
