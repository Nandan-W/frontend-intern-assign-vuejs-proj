<template>
  <div id="app">
    <AppHeader />
    <SectionI />
    
    <SectionII />
    <SectionIII />
    <AppFooter />
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue'
import SectionI from './components/SectionI.vue'
import SectionII from './components/SectionII.vue'
import SectionIII from './components/SectionIII.vue'
import AppFooter from './components/AppFooter.vue'

export default {
  name: 'App',
  components: {
    AppHeader,
    SectionI,
    SectionII,
    SectionIII,
    AppFooter
  }
}
</script>

<style>
@import './assets/styles.css';
</style>
