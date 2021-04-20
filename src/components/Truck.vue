<template>
  <div class="container">
    <div>
      <label>Cabin type: </label>
      <input type="text" v-model="cabinType">
    </div>

    <div>
      <label>Transmission: </label>
      <input type="text" v-model="transmission">
    </div>
  </div>
</template>

<script>
export default {
  name: 'Truck',
  data() {
    return {
      cabinType: '',
      transmission: '',
    }
  },

  created() {
    this.emitTruckConfig()
  },

  methods: {
    emitTruckConfig() {
      this.$emit('on-change-truck-config', {
        cabinType: this.cabinType,
        transmission: this.transmission,
      })
    }
  },

  watch: {
    cabinType() { this.emitTruckConfig() },
    transmission() { this.emitTruckConfig() },
  }
}
</script>

<style scoped>
.container {
  background: lightgreen;
  padding: 12px;
}
</style>