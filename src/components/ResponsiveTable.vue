<template>
    <div>
      <table class="smartphone-table">
        <thead>
          <tr>
            <th class="heading">Brand</th>
            <th class="heading">Model</th>
            <th class="heading">Price</th>
            <th class="heading">Camera</th>
            <th class="heading">Display</th>
            <th class="heading">Storage</th>
            <th class="heading">Video</th>
            <th class="heading">Color</th>
            <th class="heading">Face ID</th>
            <th class="heading">Audio ID</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="phone in smartphones" :key="phone.Model" class="table-row">
            <td>{{ phone.Brand }}</td>
            <td>{{ phone.Model }}</td>
            <td>{{ phone.Price }}</td>
            <td>{{ phone.Camera }}</td>
            <td>{{ phone.Display }}</td>
            <td>{{ phone.Storage }}</td>
            <td>{{ phone.Video }}</td>
            <td>{{ phone.Color }}</td>
            <td>{{ phone["Face ID"] }}</td>
            <td>{{ phone["Audio ID"] }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </template>
  
  <style>
  .smartphone-table {
    width: 100%;
    border-collapse: collapse;
  }
  
  .smartphone-table th,
  .smartphone-table td {
    padding: 8px;
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
  </style>
  
  <script>
 import data from '../assets/smartphonetabledata.json';
  
  export default {
    name: 'SmartphoneTable',
    data() {
      return {
        smartphones: data,
      };
    },
  };
  </script>
  