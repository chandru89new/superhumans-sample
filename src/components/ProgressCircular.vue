<template>
  <div id="sh-progress-circular">
    <a-progress
      type="circle"
      :percent="$props.progress"
      strokeColor="#F4A478"
    />
    <div class="subtext" v-if="$props.subtext">
      {{ $props.subtext }}
    </div>
    <div
      class="change"
      v-if="![undefined, null].includes($props.change)"
    >
      <span v-if="$props.change > 0">
        <a-icon :style="{ color: 'green' }" type="arrow-up" />
      </span>
      <span v-else>
        <a-icon :style="{ color: 'red' }" type="arrow-down" />
      </span>
      {{ $props.change }}
    </div>
  </div>
</template>
<script>
import VueTypes from "vue-types";
export default {
  props: {
    progress: VueTypes.number.isRequired,
    subtext: VueTypes.string.def(""),
    change: { type: Number, default: null },
  },
  computed: {},
};
</script>
<style lang="sass" scoped>
@import '@/assets/style-constants.sass'
#sh-progress-circular
  display: inline-flex
  flex-direction: column
  justify-items: center
  align-items: center
  position: relative
  max-width: 150px
  padding: 1em
  ::v-deep .ant-progress-circle .ant-progress-text
    font-size: $baseFontSize * 1.5
  .subtext
    margin-top: 1em
    text-align: center
    font-size: $baseFontSize
  .change
    font-size: $baseFontSize
    position: absolute
    top: 0
    right: 0
</style>
