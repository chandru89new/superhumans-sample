<template>
  <a-button
    :class="{
      'btn-tab': $props.type === 'tab',
      active: $props.active,
      large: $props.size === 'large',
    }"
    :style="computedStyle"
  >
    <a-icon
      :type="$props.icon"
      v-if="$props.iconDirection == 'left'"
    />
    <slot />
    <a-icon
      :type="$props.icon"
      v-if="$props.iconDirection == 'right'"
    />
  </a-button>
</template>
<script>
import VueTypes from "vue-types";
export default {
  props: {
    icon: VueTypes.string,
    iconDirection: VueTypes.string,
    type: VueTypes.string,
    active: VueTypes.bool.def(false),
    size: VueTypes.string.def("default"),
  },
  computed: {
    computedStyle() {
      return {
        backgroundColor: "transparent",
      };
    },
  },
};
</script>
<style lang="sass" scoped>
@import '@/assets/style-constants.sass'
.ant-btn
  border: 0
  border-radius: 100px
  box-shadow: $cardShadow
  padding: 0.5rem 1rem
  height: auto !important
  font-size: $baseFontSize
  &.large
    padding: 0.75rem 1.5rem
    font-size: $baseFontSize * 1.2
  &.btn-tab
    box-shadow: none !important
    border-radius: 0 !important
    &.active
      border-bottom: 4px solid rgba(orange, 0.4)
</style>
