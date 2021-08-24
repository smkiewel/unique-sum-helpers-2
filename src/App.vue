<template>
  <div id="app" class="container-fluid">
    <div class="row">
      <div class="col-12 col-md-auto"><h1>Unique Sum Helpers</h1></div>
      <div class="col-12 col-md-6 button-div"><add-helper-button></add-helper-button></div>
    </div>
  </div>
</template>

<script>
  import Vue from 'vue'
  import { BootstrapVue, BootstrapVueIcons } from 'bootstrap-vue'
  import AddHelperButton from './components/AddHelperButton.vue'

  import 'bootstrap/dist/css/bootstrap.css'
  import 'bootstrap-vue/dist/bootstrap-vue.css'

  Vue.use(BootstrapVue)
  Vue.use(BootstrapVueIcons)

export default {
  name: 'App',
  components: {
    AddHelperButton
  },
  methods: {
    getNextHelperId: function() {
      return 'helper-' + ++(this.count)
    },
    addHelper: function(){
      this.helpers.push({id: this.getNextHelperId()})
    },
  },
  data: function() {
    return {
      helpers: [],
      count: 0
    }
  }
}
</script>

<style>

</style>
