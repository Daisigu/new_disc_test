<template>
  <div id="app">
    <mainHeader />
    <StudentsView />
  </div>
</template>

<script>
import mainHeader from './shared/components/main-header.vue';
import StudentsView from './views/StudentsView.vue';
export default {
  name: 'App',
  components: {
    mainHeader, StudentsView
  }
}
</script>