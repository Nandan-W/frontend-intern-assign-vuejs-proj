<template>
    <header>
      <div class="header-container">
        <img src="../assets/logo.png" alt="Company Logo" class="logo" />
      </div>
    </header>
  </template>
  
  <script>
  export default {
    name: 'AppHeader'
  }
  </script>
  
  <style scoped>
  header {
    background: #fff;
    width:100%;
    margin-bottom:10px;
  }
  .header-container {
    box-shadow: 2px 4px 8px rgba(0, 0, 0, .25);
    height: 60px;
    width:100%;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .logo {
    height: 40px;
  }
  </style>
  