<template>
  <a-card id="sh-card" :class="{ 'no-padding': $props.noPadding }">
    <slot />
  </a-card>
</template>
<script>
import VueTypes from "vue-types";
export default {
  props: {
    noPadding: VueTypes.bool.def(false),
    height: VueTypes.integer,
  },
};
</script>
<style lang="sass" scoped>
@import '@/assets/style-constants.sass'
#sh-card
  border-radius: $borderRadius
  box-shadow: $cardShadow
  overflow: hidden
  &.ant-card-bordered
    border: 0 !important
  &.no-padding
    ::v-deep .ant-card-body
      padding: 0 !important
</style>
