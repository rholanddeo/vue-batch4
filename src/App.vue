

<template>

  <navbar></navbar>

  


  <div class="container py-4">
    <router-view>
      
    </router-view>
    <Home/>
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue'

export default {
  components: {
    Navbar,
  },
};
</script>
