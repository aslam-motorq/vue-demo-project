<template>
  <div class="car-info">
    <ul>
      <li v-for="(spec,index) in specificationProp" :key="index"> {{spec}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'car-info',
  props: {
    specificationProp: {
      type: Array,
      required: true,
      default () {
        return ['Engine (upto) 6498 cc', 'BHP 759.01', 'Automatic Transmission']
      }
    }
  },
  data: function () {
    return {
    }
  }
}
</script>
