<template>
  <div id="app">
    <div class='light' >
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

    <div v-for='theme in lightdark' :class='theme' >
      <center>
        <div>
          <h2>Customize</h2>
          <vue-circle
            :text='text'
            :size='selectedSize'
            :color='selectedColor'
            :dark='isDarkCircle(theme)'
            :percent-complete='percentNumber' ></vue-circle>
        </div>
        <div style='clear:both;' ></div>
        <div>
          <h2>Variations</h2>
          <h3>Size:</h3>
          <div v-for='size in sizes'>
            <vue-circle
            :text='size'
            :size='size'
            :color='selectedColor'
            :dark='isDarkCircle(theme)'
            :percent-complete='percentNumber' ></vue-circle>
          </div>
          <div style='clear:both;' >
            <h3>Color:</h3>
            <div v-for='color in colors'>
              <vue-circle
              :text='color'
              :size='selectedSize'
              :color='color'
              :dark='isDarkCircle(theme)'
              :percent-complete='percentNumber' ></vue-circle>
            </div>
          </div>
          <div style='clear:both;' ></div>
        </div>
      </center>
    </div>

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
      text: null,
      lightdark: ['light', 'dark-area']
    }
  },
  methods: {
    isDarkCircle (isDark) {
      if (isDark === 'dark-area') {
        return true
      }
      return false
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

.dark-area {
    background-color: #666;
    padding: 140px 20px 20px 20px;
    margin-bottom: 160px;
}
</style>
