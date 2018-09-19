<template>
    <div
            :class="classObject"
            @mouseover="mouseOver"
            @mouseout="mouseOut"
            @click="clicked"
    >

    </div>
</template>

<script>
    export default {
        props: {
            isEnabled: Boolean,
            id: Number,
            forceHighlighted: Boolean
        },

        data() {
          return {
              currentClass: "star-five"
          }
        },

        computed: {
          classObject() {
              return [
                  this.currentClass,
                  {
                      'star-five-enabled': this.isEnabled,
                      'star-five-highlighted': this.forceHighlighted
                  }
              ]
          }
        },

        methods: {
            mouseOver() {
                if (this.isEnabled) {
                    return
                }

                this.currentClass = "star-five-highlighted"

                this.$emit('didHoverStarWithID', this.id)
            },

            mouseOut() {
                if (this.isEnabled) {
                    return
                }

                this.currentClass = "star-five"

                this.$emit('didUnHoverStarWithID', this.id)
            },

            clicked() {
                this.$emit('didClickedStarWithID', this.id)
            }
        },

        mounted() {

        }
    }
</script>

<style scoped>
    .star-five {
        margin: 50px 0;
        position: relative;
        display: block;
        color: red;
        width: 0px;
        height: 0px;
        border-right:  100px solid transparent;
        border-bottom: 70px  solid red;
        border-left:   100px solid transparent;
        -moz-transform:    rotate(35deg);
        -webkit-transform: rotate(35deg);
        -ms-transform:     rotate(35deg);
        -o-transform:      rotate(35deg);
    }
    .star-five:before {
        border-bottom: 80px solid red;
        border-left: 30px solid transparent;
        border-right: 30px solid transparent;
        position: absolute;
        height: 0;
        width: 0;
        top: -45px;
        left: -65px;
        display: block;
        content: '';
        -webkit-transform: rotate(-35deg);
        -moz-transform:    rotate(-35deg);
        -ms-transform:     rotate(-35deg);
        -o-transform:      rotate(-35deg);

    }
    .star-five:after {
        position: absolute;
        display: block;
        color: red;
        top: 3px;
        left: -105px;
        width: 0px;
        height: 0px;
        border-right: 100px solid transparent;
        border-bottom: 70px solid red;
        border-left: 100px solid transparent;
        -webkit-transform: rotate(-70deg);
        -moz-transform:    rotate(-70deg);
        -ms-transform:     rotate(-70deg);
        -o-transform:      rotate(-70deg);
        content: '';
    }

    .star-five-enabled, .star-five-highlighted {
        margin: 50px 0;
        position: relative;
        display: block;
        color: yellow;
        width: 0px;
        height: 0px;
        border-right:  100px solid transparent;
        border-bottom: 70px  solid yellow;
        border-left:   100px solid transparent;
        -moz-transform:    rotate(35deg);
        -webkit-transform: rotate(35deg);
        -ms-transform:     rotate(35deg);
        -o-transform:      rotate(35deg);
    }
    .star-five-enabled:before, .star-five-highlighted:before {
        border-bottom: 80px solid yellow;
        border-left: 30px solid transparent;
        border-right: 30px solid transparent;
        position: absolute;
        height: 0;
        width: 0;
        top: -45px;
        left: -65px;
        display: block;
        content: '';
        -webkit-transform: rotate(-35deg);
        -moz-transform:    rotate(-35deg);
        -ms-transform:     rotate(-35deg);
        -o-transform:      rotate(-35deg);

    }
    .star-five-enabled:after, .star-five-highlighted:after {
        position: absolute;
        display: block;
        color: yellow;
        top: 3px;
        left: -105px;
        width: 0px;
        height: 0px;
        border-right: 100px solid transparent;
        border-bottom: 70px solid yellow;
        border-left: 100px solid transparent;
        -webkit-transform: rotate(-70deg);
        -moz-transform:    rotate(-70deg);
        -ms-transform:     rotate(-70deg);
        -o-transform:      rotate(-70deg);
        content: '';
    }
</style>