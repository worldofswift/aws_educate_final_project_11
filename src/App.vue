<template>
  <div id="app">
      <ul>
          <template v-for="(star, index) in stars">
              <star
                      :isEnabled="star.isEnabled"
                      :key="index"
                      :id="index"
                      :forceHighlighted="star.forceHighlighted"
                      @didHoverStarWithID="didHoverStar"
                      @didUnHoverStarWithID="didUnhoverStar"
                      @didClickedStarWithID="didClickStar"
              >

              </star>
          </template>
      </ul>
  </div>
</template>

<script>
import Star from './components/Star'

export default {
  name: 'App',
  components: {
    Star
  },
    data() {
      return {
          stars: [
                {isEnabled: false, forceHighlighted: false},
                {isEnabled: false, forceHighlighted: false},
                {isEnabled: false, forceHighlighted: false},
                {isEnabled: false, forceHighlighted: false},
                {isEnabled: false, forceHighlighted: false},
            ]
      }
    },

    methods: {
        didHoverStar(id) {
            const numbers = [...Array(id + 1).keys()]
            numbers.forEach(index => {
                this.stars[index].forceHighlighted = true
            })
        },

        didUnhoverStar(id) {
            const numbers = [...Array(id + 1).keys()]
            numbers.forEach(index => {
                this.stars[index].forceHighlighted = false
            })
        },

        didClickStar(id) {
            this.restoreDefaults()
            const numbers = [...Array(id + 1).keys()]
            numbers.forEach(index => {
                this.stars[index].isEnabled = true
            })
        },

        restoreDefaults() {
            this.stars.forEach(item => {
                item.isEnabled = false
                item.forceHighlighted = false
            })
        }
    }
}
</script>

<style scoped>
    ul {
        display: flex;
    }
</style>
