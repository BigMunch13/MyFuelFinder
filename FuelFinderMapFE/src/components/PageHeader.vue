<template>
    <div class="nav">
      <div class="nav-left">
        <img src="./icons/icon.png" alt="Logo" class="logo2">
        <span class="title">FuelFinder</span>
      </div>
      <div class="nav-links">
        <router-link to="/">HomeView</router-link>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'PageHeader'
  };
  </script>
  
  <style>
  .nav {
    background-color: #1E60BC;
    display: flex;
    justify-content: space-between; /* Push left and right content apart */
    align-items: center;
    padding: 10px 20px;
    width: 100%;
    position: fixed; /* Makes it stick at the top */
    top: 0;
    left: 0;
    z-index: 1000; /* Ensures it stays above other elements */
  }
  
  .nav-left {
    display: flex;
    align-items: center;
  }
  
  .title {
    color: white;
    font-size: 20px;
    font-weight: bold;
    margin-left: 10px;
  }
  
  .logo2 {
    width: 50px;
    height: auto;
  }
  
  .nav-links {
    display: flex;
    gap: 20px; /* Adds space between links */
  }
  
  .nav a {
    color: #f2f2f2;
    padding: 10px 15px;
    font-size: 17px;
    text-decoration: none;
  }
  
  .nav a:hover {
    background: #ddd;
    color: #333;
  }
  
  #app {
    padding-top: 90px; /* Prevents content from being hidden under fixed header */
  }
  </style>