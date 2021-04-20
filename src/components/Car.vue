<template>
  <div class="container">
    <div>
      <label>No. of airbags: </label>
      <input type="text" v-model="noOfAirbags" />
    </div>

    <div>
      <input type="checkbox" v-model="isTractionControl" />
      <label>Traction Control</label>
    </div>

    <div>
      <input type="checkbox" v-model="isABS" />
      <label>ABS</label>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Car',
  data() {
    return {
      noOfAirbags: 0,
      isTractionControl: false,
      isABS: false
    }
  },

  created() {
    this.emitCarConfig()
  },

  methods: {
    emitCarConfig() {
      this.$emit('on-change-car-config', {
        noOfAirbags: this.noOfAirbags,
        isTractionControl: this.isTractionControl,
        isABS: this.isABS,
      })
    }
  },

  watch: {
    noOfAirbags() { this.emitCarConfig() },
    isTractionControl() { this.emitCarConfig() },
    isABS() { this.emitCarConfig() }
  }
}
</script>

<style scoped>
.container {
  background: lightblue;
  padding: 12px;
}
</style>
