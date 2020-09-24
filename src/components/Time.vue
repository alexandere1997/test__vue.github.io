<template>
    <div class="app__item">
        <div class="app__time">
          <p>{{ item.hour }}:{{ item.min }}:{{ item.sec }}</p>
        </div>
        <div class="app__line"></div>
        <div class="app__button">
          <div class="app__play">
            <img v-on:click="ticTime"  v-if="!isActive"  src="треугольник.png" alt="треугольник">
            <img v-on:click="cleanInt" v-if="isActive" src="Пауза.png" alt="Пауза">
          </div>
          <div class="app__stop">
            <img v-on:click="stopTime" src="квадрат.png" alt="">
          </div>
        </div>
      </div>
</template>

<script>
export default {
  props: ['item'],
  name: 'Time',
    data: () => ({
    isActive: false,
    interavlSec: null,
    interavlMin: null,
    interavlHour: null,
  }),
  methods: {
    ticTime: function() {
      this.interavlSec = setInterval(() => {
        if(this.item.sec++ == 59) {
          this.item.sec = 0;
        }
      }, 1000)
    this.interavlMin = setInterval(() => {
        if(this.item.min++ == 59){
          this.item.min = 0;
        }
      }, 60000)
    this.interavlHour = setInterval(() => {
        this.item.hour++
      }, 3600000)

      this.isActive = !this.isActive;
    },

    cleanInt: function() {
      clearInterval(this.interavlSec)
      clearInterval(this.interavlMin)
      clearInterval(this.interavlHour)
      this.isActive = !this.isActive;
    },
    stopTime: function() {
      clearInterval(this.interavlSec)
      clearInterval(this.interavlMin)
      clearInterval(this.interavlHour)
      this.item.sec = 0,
      this.item.min = 0,
      this.item.hour = 0;
      if(!this.isActive) {
        this.isActive;
      }
      else{
        this.isActive = !this.isActive;
      }
    }
  }
}
</script>
