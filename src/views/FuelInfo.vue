<template>
  <div class="fuel-info">
    <p>Fuel Present: {{currFuelCapacity}} Litres
        <!-- v-show -->
      <span v-if="isMaxFuelCapacity">[[Tank is Full]]</span>
      <span v-else-if="isLowFuelCapacity">[[Low Fuel! Please Refill]]</span>
      <span v-else-if="isFuelEmpty">[[Tank is Empty]]</span>
      <span v-else>[[Safe Journey!]]</span>
    </p>
  </div>
</template>

<script>
export default {
  name: 'fuel-info',
  props: {
    maxFuelCapacity: {
      type: Number,
      required: false,
      default () {
        return 3
      }
    },
    currFuelCapacity: {
      type: Number,
      required: true
    }
  },
  computed: {
    isMaxFuelCapacity () {
      return this.currFuelCapacity === this.maxFuelCapacity
    },
    isLowFuelCapacity () {
      return this.currFuelCapacity <= Math.floor(this.maxFuelCapacity / 2) && this.currFuelCapacity > 0
    },
    isFuelEmpty () {
      return this.currFuelCapacity === 0
    }
  }
}
</script>
