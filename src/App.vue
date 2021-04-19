<template>
  <header class="header">
    <h1 class="header__title">Random Color Palette Generator</h1>
    <button
      @click.prevent="generatePalette"
      class="generate-btn header__btn"
    >
      Generate
    </button>
  </header>
  <main>
    <ul class="colors">
      <li
        v-for="(color, idx) in colors"
        :key="idx"
        :style="{ background: color }"
        class="colors__item"
      >
          {{ color }}
      </li>
    </ul>
  </main>
  <footer class="footer">
    The end of the page ;)
  </footer>
</template>

<script>

export default {
  name: 'App',
  components: {
  },
  created() {
    this.generatePalette();
  },
  data() {
    return {
      colors: [],
    };
  },
  methods: {
    generateRandomColor() {
      const chars = '0123456789abcdef';
      /* eslint-disable no-param-reassign, no-return-assign */
      return Array.from({ length: 6 }, () => chars[Math.floor(Math.random() * chars.length)])
        .reduce((color, char) => color += char, '#');
      /* eslint-enable no-param-reassign, no-return-assign */
    },
    generatePalette() {
      this.colors = Array.from({ length: 96 }, () => this.generateRandomColor());
    },

  },
};
</script>

<style lang="sass">

@import "~@/assets/sass/reset.sass"
@import "~@/assets/sass/mixins"
@import "~@/assets/sass/style"

$font: Avenir, Helvetica, Arial, sans-serif

#app
  font-family: $font
  -webkit-font-smoothing: antialiased
  -moz-osx-font-smoothing: grayscale

.header
  padding: 20px 0
  text-align: center
  background-color: #191919
  color: #fff

  &__title
    font-size: 2em
    margin-bottom: 20px

.generate-btn
  font-family: $font
  font-weight: 700
  font-size: 1.4em
  padding: 8px 14px
  color: #fff
  background-color: aqua
  border-radius: 4px
  border: none
  outline: none
  cursor: pointer
  transition: all 400ms ease-in-out

  &:hover
    // color: #fff
    // background-color: #a4ffa3

.colors
  font-size: 0
  border: 2px solid #fff

.colors__item
  display: inline-block
  vertical-align: top
  width: 25%
  height: calc((100vh - 142px) / 6)
  font-size: 20px
  font-weight: 700
  color: #fff
  line-height: calc((100vh - 142px) / 6)
  border: 2px solid #fff
  text-align: center
  text-shadow: 2px 2px #000

.footer
  padding: 40px 0
  background-color: #191919
  font-size: 1.4em
  color: #fff
  font-weight: 700
  text-align: center
</style>
