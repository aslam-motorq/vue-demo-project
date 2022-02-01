<template>
  <div class="cars">
    <h1>{{product}}</h1>
    <div class="car-image">
      <img v-bind:src="imagePath" :alt-text="altTextVal">
    </div>

    <!-- <div class="car-info">
      <ul>
        <li v-for="(spec,index) in specifications" :key="index"> {{spec}}</li>
      </ul>
    </div> -->

    <p> {{randomVal}} </p>
    <car-info :specificationProp="specifications"/>
    <car-info :specificationProp="specifications"/>

    <div>
      <!-- <div class="fuel-info">
        <p>Fuel Present: {{fuelCapacity}} Litres
          <span v-if="fuelCapacity == 5">[[Tank is Full]]</span>
          <span v-else-if="fuelCapacity <= 2 && fuelCapacity > 0">[[Low Fuel! Please Refill]]</span>
          <span v-else-if="fuelCapacity == 0">[[Tank is Empty]]</span>
        </p>
      </div> -->

      <fuel-info :currFuelCapacity="fuelCapacity" :maxFuelCapacity="5" />

      <button v-on:click="fuelCapacity<5 ? fuelCapacity += 1 : null"> Add 1 Litre </button>
      <button @click="consume1Litre()" :disabled="fuelCapacity==0" :class="{disabledButton: fuelCapacity==0}"> Consume 1 Litre </button>
    </div>

    <!-- <div class="color-picker">
      <div v-for="(carVal,index) in carList" :key="carVal.id"
        class="color-box"
        :style="{backgroundColor: carVal.color}"
        @mouseover="updateCar(index)"
      >
      </div>
    </div> -->

    <car-painter :carList="carList" @car-index-updated="updateCar" />

    <send-email/>
  </div>
</template>

<script>
import redImagePath from '@/assets/redCar.jpeg'
import blackImagePath from '@/assets/blackCar.jpeg'
import carInfo from './carInfo.vue'
import FuelInfo from './FuelInfo.vue'
import CarPainter from './carPainter.vue'
import SendEmail from './sendEmail.vue'
import { sampleMixin } from './sampleMixin.js'

export default {
  components: { carInfo, FuelInfo, CarPainter, SendEmail },
  name: 'about',
  mixins: [sampleMixin],
  data: function () {
    return {
      product: 'cars',
      selectedCarIndex: 0,
      redPath: redImagePath,
      blackPath: blackImagePath,
      altTextVal: 'Car Image',
      fuelCapacity: 5,
      specifications: ['Engine (upto) 6498 cc', 'BHP 759.01', 'Automatic Transmission'],
      carList: [
        {
          id: 1234,
          color: 'black',
          pathVal: blackImagePath
        },
        {
          id: 1235,
          color: 'red',
          pathVal: redImagePath
        }
      ],
      randomVal: 1234
    }
  },
  created () {
    console.log('cars created')
    this.mixinRandomMethod()
  },
  mounted () {
    console.log('cars mounted')
  },
  computed: {
    // imagePath: blackImagePath,
    imagePath () {
      return this.carList[this.selectedCarIndex].pathVal
    }
  },
  methods: {
    consume1Litre () {
      if (this.fuelCapacity > 0) {
        this.fuelCapacity -= 1
      }
    },
    updateCarImage (inpPathValue) {
      this.imagePath = inpPathValue
    },
    updateCar (index) {
      console.log('index', index)
      this.selectedCarIndex = index
    }
  },
  watch: {
    selectedCarIndex: function (newVal, oldVal) {
      console.log('selectedCarIndex watcher triggered', newVal, oldVal)
    }
  }
}
</script>

<style lang="scss">
#cars{
  text-align: left;
}
.color-box {
  width: 40px;
  height: 40px;
  margin-top: 5px;
}

button {
  background-color: #065eab;
  height: 35px;
  width: 115px;
  margin-right: 10px;
}

.disabledButton {
  background-color: #d8d8d8;
}

.car-image{
  img {
    height: 150px;
    width: 246px;
  }
}
</style>
