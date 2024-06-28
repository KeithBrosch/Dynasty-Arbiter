<script setup>
import SideNav from './components/SideNav.vue'
</script>

<template>
  <div>
    <SideNav />
    <main>
      <router-view />
    </main>
  </div>
</template>

<style lang="scss" scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins&display=swap');

:root {
  font-size: 16px;
  font-family: 'Poppins', sans-serif;
}

body {
  color: black;
  background-color: white;
  margin: 0;
  padding: 0;
}

#app {
  min-height: 100vh;
  background: #fff;
  color: #000;
  &.darkmode {
    background: #000;
    color: #fff;
  }
}

body::-webkit-scrollbar {
  width: 0.25rem;
}

body::-webkit-scrollbar-track {
  background: #1e1e24;
}

body::-webkit-scrollbar-thumb {
  background: #ff7eee;
}

main {
  margin: 5rem 17rem;
}

.vue-notification-group {
  background: #ff7eee;
  .vue-notification {
    background: rgba(255, 126, 238, 0.75);
    border: none;
  }
}
</style>
