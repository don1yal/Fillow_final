<template>
    <div>
      <div class="progress-bar-container">
        <div class="progress-bar" :style="{ width: `${percentage}%`, backgroundColor: progressBarColor }"></div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      percentage: {
        type: Number,
        required: true,
        default: 80,
      },
      progressBarColor: {
        type: String,
        default: '#000',
      },
    },
    data() {
      return {
        hover: false,
      };
    },
  };
  </script>
  
  <style scoped>
  .label {
    font-size: 20px;
    font-weight: 800;
    display: block;
    color: #3c3c3c;
    font-size: 14px;
    text-align: center;
    margin-bottom: 5px;
  }
  
  .progress-bar-container {
    width: 100%;
    height: 20px;
    background-color: #eee;
    border-radius: 5px;
    overflow: hidden;
    transition: background-color 0.3s;
    margin-bottom: 20px;
  }
  
  .progress-bar {
    height: 100%;
    transition: width 0.3s, background-color 0.3s;
  }
  
  .progress-bar-container:hover {
    background-color: #ddd;
  }
  
  .progress-bar:hover {
    background-color: #333;
  }
  
  .progress-bar-container:hover,
  .progress-bar:hover {
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
  }
  </style>