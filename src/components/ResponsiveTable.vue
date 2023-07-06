<template>
  <div class="table-wrapper">
    <div v-for="(column, key) in jsonData[0]" :key="key" class="table-column">
      <table
        :class="{ 'table-fade-out': selectedTable === key }"
        class="custom-table custom-table--large"
      >
        <thead>
          <tr>
            <th @click="removeTable(key)">
              <div class="table-heading-duplicate">
                {{ key }}
              </div>
            </th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(item, index) in jsonData" :key="index" class="table-row">
            <td>{{ item[key] }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<style>
.table-wrapper {
  display: flex;
  overflow-x: auto;
  white-space: nowrap;
  animation: tableFadeIn 1s ease-in-out;
  position: relative;
  gap: 0;
}

@keyframes tableFadeIn {
  from {
    opacity: 0;
    transform: translateY(-20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.table-column {
  flex-grow: 1;
  position: relative;
  margin-right: 0;
}

.custom-table {
  border-collapse: collapse;
  background-color: #f5f5f5;
}

.custom-table--large {
  font-size: 20px;
}

.table-heading-duplicate {
  background-color: #56797C;
  color: #fff;
  border: none;
  position: sticky;
  top: 0;
  z-index: 1;
  box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
  padding: 5px;
  cursor: pointer;
}

.table-row {
  background-color: #f2f2f2;
}

.table-row:hover {
  background-color: #e0e0e0;
}

td {
  padding: 12px;
}

.table-fade-out {
  animation: tableFadeOut 0.5s ease-in-out forwards;
}

@keyframes tableFadeOut {
  from {
    opacity: 1;
    transform: translateY(0);
  }
  to {
    opacity: 0;
    transform: translateY(-20px);
  }
}
</style>

<script>
import jsonData from '../assets/smartphonetabledata.json';

export default {
  data() {
    return {
      jsonData: [],
      selectedTable: null,
    };
  },
  mounted() {
    this.jsonData = jsonData;
  },
  methods: {
    removeTable(key) {
      this.selectedTable = key;
      setTimeout(() => {
        this.jsonData = this.jsonData.map(item => {
          const newItem = { ...item };
          delete newItem[key];
          return newItem;
        });
        this.selectedTable = null;
      }, 500);
    },
  },
};
</script>
