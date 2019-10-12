<template>
  <div>
    <Navbar />
    <Home />
  </div>
</template>

<script>
import 'bootstrap'
import 'bootswatch/dist/pulse/bootstrap.min.css'
import '@fortawesome/fontawesome-free/css/all.min.css'

import Navbar from './components/Navbar'
import Home from './components/Home'

export default {
  name: 'app',
  components: {
    Navbar,
    Home 
  }
}
</script>
