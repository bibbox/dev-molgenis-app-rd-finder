<template>
  <div @click="$root.$emit('bv::hide::popover')">
    <div class="container">
      <b-alert v-if="errorMessage" show variant="danger" dismissible>{{errorMessage}}</b-alert>
      <router-view></router-view>
    </div>
  </div>
</template>

<style>
.mg-page-content {
  padding-top: 0 !important;
}
.app {
    background-color: #f1f1de;
}
.container {
  background-color: #fcfcf5;
}
</style>

<script>
import { mapGetters, mapActions } from 'vuex'

export default {
  computed: {
    ...mapGetters({ errorMessage: 'getErrorMessage' })
  },
  methods: {
    ...mapActions([
      'GetNegotiatorType',
      'GetNegotiatorEntities',
      'GetQualityStandardInformation'
    ])
  },
  mounted () {
    this.GetNegotiatorType()
    this.GetNegotiatorEntities()
    this.GetQualityStandardInformation()
  },
  name: 'biobank-explorer'
}
</script>
