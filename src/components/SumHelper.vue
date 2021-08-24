<template>
  <div class="sum-helper" :id="helper.id">
    <b-icon icon="x-square" v-on:click="removeHelper" class="remove-helper"></b-icon>
    <div class="sum-helper-wrapper">
      <div>
        <label class="helper-label" :for="inputId('size')">Size:</label>
        <input type="number"
               :id="inputId('size')"
               v-model="size"
               v-on:input="updateHelper"
               v-on:click="(e) => e.target.select()" />
      </div>
      <div>
        <label class="helper-label" :for="inputId('total')">Total:</label>
        <input type="number"
               :id="inputId('total')"
               v-model="total"
               v-on:input="updateHelper"
               v-on:click="(e) => e.target.select()" />
      </div>
      <hr/>
      <div>
        <label class="helper-label" :for="inputId('included')">Included:</label>
        <input type="text"
               :id="inputId('included')"
               v-model="included"
               v-on:input="updateHelper" />
      </div>
      <div>
        <label class="helper-label" :for="inputId('excluded')">Excluded:</label>
        <input type="text"
               :id="inputId('excluded')"
               v-model="excluded"
               v-on:input="updateHelper" />
      </div>
      <hr/>
      <div>
        <label class="helper-label" :for="inputId('min-size')">Min Size:</label>
        <input type="number"
               :id="inputId('min-size')"
               v-model="minSize"
               v-on:input="updateHelper"
               v-on:click="(e) => e.target.select()"
               v-bind:disabled="sizeDisabled" />
      </div>
      <div>
        <label class="helper-label" :for="inputId('max-size')">Max Size:</label>
        <input type="number"
               :id="inputId('max-size')"
               v-model="maxSize"
               v-on:input="updateHelper"
               v-on:click="(e) => e.target.select()"
               v-bind:disabled="sizeDisabled" />
      </div>
      <hr/>
      <div>
        <label class="helper-label" :for="inputId('min-total')">Min Total:</label>
        <input type="number"
               :id="inputId('min-total')"
               v-model="minTotal"
               v-on:input="updateHelper"
               v-on:click="(e) => e.target.select()"
               v-bind:disabled="totalDisabled" />
      </div>
      <div>
        <label class="helper-label" :for="inputId('max-total')">Max Total:</label>
        <input type="number"
               :id="inputId('max-total')"
               v-model="maxTotal"
               v-on:input="updateHelper"
               v-on:click="(e) => e.target.select()"
               v-bind:disabled="totalDisabled" />
      </div>
      <hr/>
    </div>
    <table class="table table-striped">
      <tbody>
      </tbody>
    </table>
    <textarea v-model="notes" class="form-control"></textarea>
  </div>
</template>

<script>
  import * as helperUtils from '../lib/helperUtils.js'
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
      },
      updateHelper: function() {
        console.log('update')
      },
      inputId: function(input){
        return input + '-' + this.helper.id
      }
    },
    computed: {
      sizeDisabled: function(){
        return this.size != '' && helperUtils.cleanZeroes(this.size) != '0'
      },
      totalDisabled: function(){
        return this.total != '' && helperUtils.cleanZeroes(this.total )!= '0'
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
  .sum-helper {
    margin-bottom: .75em;
    margin-right: .75em;
    padding: 0 !important;
    height: max-content !important;
    background-color: lightgrey;
    width: 20rem;
  }
  .sum-helper-wrapper {
    padding: 5px;
  }
  #sum-form .row {
    margin-bottom: 10px !important;
  }
  input {
    padding-left: 5px;
    width: 12rem;
  }
  hr {
    margin: .3rem !important;
  }
  #sum-form > div > div  {
    text-align: right;
  }
  .hidden {
    color: #666;
    background-color: #666;
  }
  .hidden:before {
    content: "\200D";
    display:inline;
   }
  .hidden-field {
    width: 12rem;
    display: inline-block;
  }
  .hidden-field-label, .helper-label {
    width: 5.5rem;
    display: inline-block;
    margin-bottom: 0;
  }
</style>