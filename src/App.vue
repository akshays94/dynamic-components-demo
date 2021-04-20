<template>
  <div id="app">
    <section style="width: 40%;">
      <div>
        <label>Name: </label>
        <input type="text" v-model="name">
      </div>

      <div>
        <label>Type: </label>
        <select v-model="vehicleType">
          <option value="CAR">Car</option>
          <option value="MOTORCYCLE">Motorcycle</option>
          <option value="TRUCK">Truck</option>
        </select>
      </div>

      <div>
        <component
          :is="selectedVehicleComponent"
          @on-change-car-config="onChangeCarConfig"
          @on-change-motorcycle-config="onChangeMotorcycleConfig"
          @on-change-truck-config="onChangeTruckConfig"
        />
      </div>

      <hr>

      <div>
        Vehicle type: {{ vehicleType }}
        <br><br>
        Vehicle name: {{ name }}
        <br><br>
        Vehicle Configuration: <br>
        {{ vehicleConfig }}
      </div>
    </section>
  </div>
</template>

<script>
import Car from '@/components/Car.vue'
import Motorcycle from '@/components/Motorcycle.vue'
import Truck from '@/components/Truck.vue'

export default {
  name: 'App',

  components: {
    Car,
    Motorcycle,
    Truck,
  },

  data() {
    return {
      name: '',
      vehicleType: 'CAR',
      vehicleConfig: {}
    }
  },

  computed: {
    selectedVehicleComponent() {
      switch(this.vehicleType) {
        case 'CAR':
          return 'Car'
        case 'MOTORCYCLE':
          return 'Motorcycle'
        case 'TRUCK':
          return 'Truck'       
      }
      return null
    }
  },

  methods: {
    onChangeCarConfig(carConfig) {
      this.vehicleConfig = carConfig
    },

    onChangeMotorcycleConfig(motorcycleConfig) {
      this.vehicleConfig = motorcycleConfig
    },

    onChangeTruckConfig(truckConfig) {
      this.vehicleConfig = truckConfig
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

div {
  margin-bottom: 8px;
}
</style>
