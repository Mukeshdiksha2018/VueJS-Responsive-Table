<template>
  <div>
    <div v-for="(value, key) in jsonData[0]" :key="key" class="table-wrapper">
      <table class="custom-table custom-table--large">
        <thead>
          <tr>
            <th>
              <div
                :class="['table-heading-duplicate', { 'active': isHeadingClicked(key) }]"
                @click="toggleRowVisibility(key)"
              >
                {{ key }}
              </div>
            </th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(item, index) in jsonData" :key="index" class="table-row">
            <td>
              <div v-show="!isRowHidden(key)" class="slide-content">
                {{ item[key] }}
              </div>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>


<style>
.table-wrapper {
  display: inline-block;
  overflow-x: auto;
  white-space: nowrap;
  margin-right: 10px; /* Adjust the spacing between tables */
}


.custom-table {
  margin-bottom: 20px;
  border-collapse: collapse;
  background-color: #f5f5f5;
}


.custom-table--large {
  font-size: 20px;
}


.table-heading-duplicate {
  background-color: #56797c;
  color: #fff;
  border: none;
  position: sticky;
  top: 0;
  z-index: 1;
  box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
  padding: 5px;
  cursor: pointer;
}


.table-heading-duplicate.active {
  background-color: #8F5049;
}


.table-row {
  background-color: #f2f2f2;
}


.table-row:hover {
  background-color: #e0e0e0;
}


.custom-table--large td {
  margin: 0 5px; /* Add a 5-pixel gap between each column */
}


.slide-content {
  padding: 12px;
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
  height: auto;
  transition: height 1s ease-out;
}


.slide-content[style*="height: 0"] {
  height: 0;
}
</style>


<script>
import jsonData from '../assets/smartphonetabledata.json';


export default {
  data() {
    return {
      jsonData: [],
      hiddenColumns: {},
      clickedHeadings: {}
    };
  },
  mounted() {
    this.jsonData = jsonData;
  },
  methods: {
    toggleRowVisibility(column) {
      this.hiddenColumns[column] = !this.hiddenColumns[column];
      this.clickedHeadings[column] = !this.clickedHeadings[column];
    },
    isRowHidden(column) {
      return this.hiddenColumns[column];
    },
    isHeadingClicked(column) {
      return this.clickedHeadings[column];
    }
  }
};
</script>
