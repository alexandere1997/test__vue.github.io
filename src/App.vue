<template>
  <div id="app">
    <div class="app__box" v-for="component in dataArr" :key="component.id">
      <Time :item="component"/>
    </div>
      <div class="app__item app__item_mod">
        <img v-on:click="addComponent" src="plus.png" alt="plus">
      </div>
  </div>
</template>

<script>
import Time from './components/Time.vue'

export default {
  name: 'App',
  components: {
    Time
  },
  data: () => ({
    dataArr: [],
    count: 0
  }),
  methods: {
    addComponent: function() {
      this.dataArr.push({
        id: this.count++,
        sec: 0,
        min: 0,
        hour: 0,
      })
    }
  }
}
</script>

<style>
  #app{
    display: flex;
    justify-content: center;
    align-items: center;
    height: 768px;
    flex-wrap: wrap;
  }
  body{
    background-color: #353638;
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  .app__box{
    width: 245px;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .app__item{
    width: 225px;
    height: 120px;
    background-color: #696969;
    margin-bottom: 10px;
  }
  .app__time{
    height: 50px;
    width: 100%;
    text-align: center;
  }
  .app__time img{
    cursor: pointer;
  }
  .app__item{
    font-size: 22px;
    line-height: 21px;
    text-align: center;
    color: #9E9E9E;
    font-family: sans-serif;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
  }
  .app__button{
    height: 50px;
    width: 80%;
    display: flex;
    justify-content: space-around;
  }
  .app__button img{
    cursor: pointer;
  }
  .app__act{
    display: none;
  }
  .app__item_mod {
      display: flex;
      justify-content: center;
  }
  .app__item_mod img{
    cursor: pointer;
  }
  .app__line{
    width: 225px;
    height: 1px;
    background-color: #9E9E9E;
  }
</style>
