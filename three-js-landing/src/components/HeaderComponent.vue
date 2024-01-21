<script setup lang="ts"></script>

<template>
  <div class="header">
    <div class="logo">
      <img src="../../favicon.ico" alt="Logo" />
    </div>
    <nav>
      <ul class="nav-links">
        <li><a href="/">Home</a></li>
        <li><a href="/about">About</a></li>
        <li><a href="/contact">Contact</a></li>
      </ul>
    </nav>
  </div>
</template>

<style scoped>
.header {
  display: flex;
  gap: 20px;
  margin-bottom: 20px;
}

.nav-links {
  display: flex;
  gap: 20px;
}
</style>
