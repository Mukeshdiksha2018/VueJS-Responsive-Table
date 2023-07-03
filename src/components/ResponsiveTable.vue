<template>
  <div>
    <div class="button-container">
      <div
        v-for="(buttonName, index) in buttonNames"
        :key="index"
        :class="['button', buttonName === 'Brand' ? 'draggable' : '', selectedColumns.includes(buttonName) ? 'selected' : '']"
        @dragstart="handleDragStart(buttonName)"
        draggable="true"
        @click="toggleColumn(buttonName)"
      >
        {{ buttonName }}
      </div>
    </div>

    <div class="drop-zone" @dragover.prevent @drop="handleDrop">
      <template v-if="showTable">
        <table class="data-table">
          <thead>
            <tr>
              <th
                v-for="column in selectedColumns"
                :key="column"
                class="table-heading"
              >
                {{ column }}
              </th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(item, index) in filteredData" :key="index">
              <td v-for="column in selectedColumns" :key="column">
                {{ item[column] }}
              </td>
            </tr>
          </tbody>
        </table>
      </template>
      <div v-else class="placeholder-text">Drop buttons here to create a table</div>
    </div>
  </div>
</template>

<script>
import jsonData from '../assets/smartphonetabledata.json';

export default {
  data() {
    return {
      buttonNames: [
        "Brand",
        "Model",
        "Price",
        "Camera",
        "Display",
        "Storage",
        "Video",
        "Color",
        "Face ID",
        "Audio ID"
      ],
      columnSequence: [
        "Brand",
        "Model",
        "Price",
        "Camera",
        "Display",
        "Storage",
        "Video",
        "Color",
        "Face ID",
        "Audio ID"
      ],
      selectedColumns: [],
      filteredData: [],
      showTable: false
    };
  },
  methods: {
    handleDragStart(buttonName) {
      event.dataTransfer.setData("text/plain", buttonName);
    },
    handleDrop(event) {
      event.preventDefault();
      const droppedButton = event.dataTransfer.getData("text/plain");
      this.toggleColumn(droppedButton);
    },
    toggleColumn(buttonName) {
      if (this.selectedColumns.includes(buttonName)) {
        // Remove the column
        this.selectedColumns = this.selectedColumns.filter(
          (column) => column !== buttonName
        );
      } else {
        // Add the column
        this.selectedColumns.push(buttonName);
      }
      this.selectedColumns.sort((a, b) => {
        return (
          this.columnSequence.indexOf(a) - this.columnSequence.indexOf(b)
        );
      });
      this.filteredData = jsonData.map((item) =>
        this.selectedColumns.reduce((filteredItem, column) => {
          filteredItem[column] = item[column];
          return filteredItem;
        }, {})
      );
      this.showTable = this.selectedColumns.length > 0;
    }
  }
};
</script>

<style>
.button-container {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  position: absolute;
  left: 0;
}

.button {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 10px 20px;
  background-color: #1C7076;
  border: 1px solid #ccc;
  border-radius: 4px;
  cursor: pointer;
  color: white;
  transition: transform 0.3s;
  margin-bottom: 10px;
}

.button:hover {
  transform: scale(1.2);
}

.draggable {
  cursor: move;
}

.selected {
  background-color: #A74A4A;
}

.drop-zone {
  margin-top: 20px;
  padding: 20px;
  border: 1px dashed #ccc;
  background-color: #f5f5f5;
}

.data-table {
  width: 100%;
  border-collapse: collapse;
}

.data-table th {
  padding: 8px;
  border: 1px solid #ccc;
  background-color: #1C7076;
  color: white;
  font-size: 20px;
}

.data-table td {
  padding: 8px;
  border: 1px solid #ccc;
  background-color: #E8E8DF;
}

.placeholder-text {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  font-size: 18px;
  color: #999;
}
</style>
