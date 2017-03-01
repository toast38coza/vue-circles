<template>
  <div id="app">
    <div>
      Text: <input v-model='text' />
      Percent: <input type='number' v-model='percent' />
      Size:
      <select v-model="selectedSize">
        <option v-for="size in sizes" v-model="selectedSize">
          {{ size }}
        </option>
      </select>
      Color:
      <select v-model="selectedColor">
        <option v-for="color in colors" v-model="selectedColor">
          {{ color }}
        </option>
      </select>
      <hr/>
    </div>
    <center>
    <vue-circle
      :text='text'
      :size='selectedSize'
      :color='selectedColor'
      :percent-complete='percentNumber' ></vue-circle>
    </center>
  </div>
</template>

<script>
import VueCircle from './components/Circle'

export default {
  name: 'app',
  components: {
    VueCircle
  },
  data () {
    return {
      percent: 50,
      sizes: ['big', 'medium', 'small'],
      colors: ['default', 'green', 'orange'],
      selectedSize: 'big',
      selectedColor: 'default',
      text: null
    }
  },
  computed: {
    percentNumber () {
      return parseInt(this.percent)
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
