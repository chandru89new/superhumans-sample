<template>
  <div>
    <div class="title" v-if="$slots['title'] || $props.title">
      <slot name="title">{{ $props.title }}</slot>
    </div>
    <div class="content">
      <slot />
    </div>
  </div>
</template>
<script>
import VueTypes from "vue-types";
export default {
  props: {
    title: VueTypes.string
  }
};
</script>
<style lang="sass" scoped>
@import '@/assets/style-constants.sass'
.title
  font-size: $baseFontSize * 1.5
  margin-bottom: 1.5rem
</style>