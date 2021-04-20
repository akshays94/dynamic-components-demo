<template>
  <div class="container">
    <div>
      <label>Engine: </label>
      <input type="text" v-model="engine">
    </div>

    <div>
      <label>Power: </label>
      <input type="text" v-model="power">
    </div>
  </div>
</template>

<script>
export default {
  name: 'Motorcycle',
  data() {
    return {
      engine: '',
      power: '',
    }
  },

  created() {
    this.emitMotorcycleConfig()
  },

  methods: {
    emitMotorcycleConfig() {
      this.$emit('on-change-motorcycle-config', {
        engine: this.engine,
        power: this.power,
      })
    }
  },

  watch: {
    engine() { this.emitMotorcycleConfig() },
    power() { this.emitMotorcycleConfig() },
  }
}
</script>

<style scoped>
.container {
  background: lightsalmon;
  padding: 12px;
}
</style>