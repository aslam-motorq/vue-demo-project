<template>
  <div class="color-picker">
    <div v-for="(carVal,index) in carList" :key="carVal.id"
    class="color-box"
    :style="{backgroundColor: carVal.color}"
    @mouseover="updateCarIndex(index)"
    >
    </div>
  </div>
</template>

<script>
export default {
  name: 'car-painter',
  props: {
    carList: {
      type: Array,
      required: true
    }
  },
  methods: {
    updateCarIndex (currIndex) {
      console.log('CI', currIndex)
      this.$emit('car-index-updated', currIndex)
    }
  }
}
</script>

<style lang="scss">
.color-box {
  width: 40px;
  height: 40px;
  margin-top: 5px;
}
</style>
