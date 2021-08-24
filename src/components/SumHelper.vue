<template>
  <div class="sum-helper col-12 col-sm2-6 col-lg-5 col-xl-3" :id="helper.id">
    <b-icon icon="x-square" v-on:click="removeHelper" class="remove-helper"></b-icon>

  </div>
</template>

<script>
  export default {
    props:['helper'],
    data: function() {
      return {
        hideMissingField: true,
        hideRequiredField: true,
        hideLengthField: true,
        hideSumField: true,
        size: 0,
        total: 0,
        notes: '',
        included: '',
        excluded: '',
        minSize: 0,
        maxSize: 0,
        minTotal: 0,
        maxTotal: 0,
        combos: [],
        activeCombos: []
      }
    },
    methods: {
      removeHelper: function() {
        this.$parent.removeHelper(this.helper.id)
      }
    }
  }
</script>

<style>
  .remove-helper {
    float: right;
    margin-right: 5px;
    margin-top: 5px;
  }
</style>