<template lang="html">
  <div id="app">
    <div class="ic logo"></div>
    <hello></hello>
  </div>
</template>

<script lang="babel">
  import Hello from 'src/components/Hello'

  export default {
    name: 'app',

    data () {
      return {
        ORIGINAL_VIEWPORT_WIDTH: 1080
      }
    },

    methods: {
      onResize () {
        let widthRatio = window.innerWidth / this.ORIGINAL_VIEWPORT_WIDTH
        this.$el.style.transform = 'scale(' + widthRatio + ')'
      }
    },

    mounted () {
      this.onResize()
      window.addEventListener('resize', this.onResize)
    },

    components: {
      Hello
    }
  }
</script>

<style lang="stylus">
  @import '~reset-css/reset.css'
  @import '~generated/sprite'

  #app {
    width 1080px
    text-align: center;
    transform-origin left top
    will-change transform

    .ic {
      display inline-block
    }

    .logo {
      sprite($logo)
    }
  }
</style>
