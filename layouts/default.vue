<template>
  
    <Nav />
  
      <div class="dashboard-layout">
        <aside class="sidebar">
          <leftSidebar />
        </aside>
        <div class="main-content">
          <slot />
        </div>
      </div>
    </template>
    
    <script setup>
      // Any setup specific to the dashboard layout
    </script>
    
    <style>
      .dashboard-layout {
        display: flex;
      }
      .main-content {
        flex: 1;
        padding: 20px;
      }
    </style>