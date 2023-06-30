<template>
    <div>
      <table class="smartphone-table">
        <thead>
          <tr>
            <th class="heading" v-show="isColumnVisible('Brand')">Brand <button class="toggle-button" @click="toggleColumnVisibility('Brand')">{{ isColumnVisible('Brand') ? 'Hide' : 'Show' }}</button></th>
          <th class="heading" v-show="isColumnVisible('Model')">Model <button class="toggle-button" @click="toggleColumnVisibility('Model')">{{ isColumnVisible('Model') ? 'Hide' : 'Show' }}</button></th>
          <th class="heading" v-show="isColumnVisible('Price')">Price <button class="toggle-button" @click="toggleColumnVisibility('Price')">{{ isColumnVisible('Price') ? 'Hide' : 'Show' }}</button></th>
          <th class="heading" v-show="isColumnVisible('Camera')">Camera <button class="toggle-button" @click="toggleColumnVisibility('Camera')">{{ isColumnVisible('Camera') ? 'Hide' : 'Show' }}</button></th>
          <th class="heading" v-show="isColumnVisible('Display')">Display <button class="toggle-button" @click="toggleColumnVisibility('Display')">{{ isColumnVisible('Display') ? 'Hide' : 'Show' }}</button></th>
          <th class="heading" v-show="isColumnVisible('Storage')">Storage <button class="toggle-button" @click="toggleColumnVisibility('Storage')">{{ isColumnVisible('Storage') ? 'Hide' : 'Show' }}</button></th>
          <th class="heading" v-show="isColumnVisible('Video')">Video <button class="toggle-button" @click="toggleColumnVisibility('Video')">{{ isColumnVisible('Video') ? 'Hide' : 'Show' }}</button></th>
          <th class="heading" v-show="isColumnVisible('Color')">Color <button class="toggle-button" @click="toggleColumnVisibility('Color')">{{ isColumnVisible('Color') ? 'Hide' : 'Show' }}</button></th>
          <th class="heading" v-show="isColumnVisible('Face ID')">Face ID <button class="toggle-button" @click="toggleColumnVisibility('Face ID')">{{ isColumnVisible('Face ID') ? 'Hide' : 'Show' }}</button></th>
          <th class="heading" v-show="isColumnVisible('Audio ID')">Audio ID <button class="toggle-button" @click="toggleColumnVisibility('Audio Id')">{{ isColumnVisible('Audio ID') ? 'Hide' : 'Show' }}</button></th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="phone in smartphones" :key="phone.Model" class="table-row">
            <td v-show="isColumnVisible('Brand')">{{ phone.Brand }}</td>
            <td v-show="isColumnVisible('Model')">{{ phone.Model }}</td>
            <td v-show="isColumnVisible('Price')">{{ phone.Price }}</td>
            <td v-show="isColumnVisible('Camera')">{{ phone.Camera }}</td>
            <td v-show="isColumnVisible('Display')">{{ phone.Display }}</td>
            <td v-show="isColumnVisible('Storage')">{{ phone.Storage }}</td>
            <td v-show="isColumnVisible('Video')">{{ phone.Video }}</td>
            <td v-show="isColumnVisible('Color')">{{ phone.Color }}</td>
            <td v-show="isColumnVisible('Face ID')">{{ phone['Face ID'] }}</td>
            <td v-show="isColumnVisible('Audio ID')">{{ phone['Audio ID'] }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </template>
  
 
  
  <script>
 import data from '../assets/smartphonetabledata.json';
  
  export default {
    name: 'SmartphoneTable',
    data() {
      return {
        smartphones: data,
        columnVisibility: {
        Brand: true,
        Model: true,
        Price: true,
        Camera: true,
        Display: true,
        Storage: true,
        Video: true,
        Color: true,
        'Face ID': true,
        'Audio ID': true
      }
      };
    },
    methods: {
      isColumnVisible(columnName) {
        return this.columnVisibility[columnName];
      },
      toggleColumnVisibility(columnName) {
        this.columnVisibility[columnName] = !this.columnVisibility[columnName];
      }
    }
  };
  </script>
  



  <style>
  .smartphone-table {
    width: 100%;
    border-collapse: collapse;
  }
  
  .smartphone-table th,
  .smartphone-table td {
    padding: 20px;
    text-align: left;
    border-bottom: 1px solid #ddd;
  }
  
  .smartphone-table th {
    font-weight: bold;
    color: white; /* Updated text color for table heading */
    background-color: #664545; /* Updated background color for table heading */
    border-top: 2px solid #ddd;
  }
  
  .smartphone-table tbody .table-row {
    background-color: #94524A; /* Updated background color for table rows */
    color: white; /* Updated text color for table rows */
    transition: transform 0.3s; /* Added transition for the transform property */
  }
  
  .smartphone-table tbody .table-row:hover {
    transform: translateZ(10px); /* Added translation along the z-axis for the 3D effect */
    background-color: #A27E6F; /* Updated hover background color for table rows */
  }
  
  .smartphone-table td {
    border-top: 1px solid #ddd;
  }
  
  .smartphone-table td:first-child,
  .smartphone-table th:first-child {
    border-left: 1px solid #ddd;
  }
  
  .smartphone-table td:last-child,
  .smartphone-table th:last-child {
    border-right: 1px solid #ddd;
  }

  .toggle-button {
  display: inline-block;
  margin-left: 5px;
  font-size: 12px;
  padding: 2px 5px;
  background-color: #ccc;
  border: none;
  border-radius: 3px;
  cursor: pointer;
}

  </style>