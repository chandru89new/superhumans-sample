<template>
  <Card :noPadding="true" style="overflow: hidden">
    <div id="sh-scroll-card">
      <div class="highlight" v-if="$slots['highlight']">
        <slot name="highlight" />
      </div>
      <div class="scroll-area">
        <div class="navigation-arrow left">
          <a>
            <a-icon type="left" />
          </a>
        </div>
        <div class="scroll-content">
          <slot name="scroll-content">Put your scroll content in `v-slot:scroll-content`</slot>
        </div>
        <div class="navigation-arrow right">
          <a>
            <a-icon type="right" />
          </a>
        </div>
      </div>
    </div>
  </Card>
</template>
<script>
export default {
  components: {
    Card: () => import("./Card")
  }
};
</script>
<style lang="sass" scoped>
@import '../assets/style-constants.sass'

#sh-scroll-card
  position: relative
  display: grid
  grid-gap: 0
  grid-template-columns: minmax(150px, 2fr) 6fr
  overflow: hidden
  .highlight
    z-index: 2
    color: white
    background-color: orange
    padding: $cardPadding
  .scroll-area
    padding: $cardPadding $cardPadding*2 $cardPadding $cardPadding
    position: relative
    white-space: nowrap
    overflow-x: scroll
    .scroll-content
      // position: absolute
      // left: 3rem
      // right: 3rem
      // top: 0
      // bottom: 0
      ::v-deep > div + div
        margin-left: 1rem
    .navigation-arrow
      z-index: 3
      background: white
      position: absolute
      top: 0
      bottom: 0
      display: flex
      align-items: center
      font-size: $baseFontSize * 2
      padding: 0 0.5rem
      display: none
      &.left
        left: 0
      &.right
        right: 0
</style>