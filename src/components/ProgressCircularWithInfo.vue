<template>
  <Card :noPadding="true" :height="$props.height">
    <div id="sh-progress-circular-info">
      <ProgressCircular
        :progress="$props.progress"
        :subtext="$props.subtext"
        :change="$props.change"
      />
      <div class="stats">
        <div v-for="stat in $props.stats" :key="stat.label">
          <div class="statistic-value">{{ stat.value }}</div>
          <div class="statistic-label">{{ stat.label }}</div>
        </div>
      </div>
    </div>
  </Card>
</template>
<script>
import VueTypes from "vue-types";
export default {
  components: {
    Card: () => import("./Card"),
    ProgressCircular: () => import("./ProgressCircular"),
  },
  props: {
    progress: VueTypes.number.isRequired,
    subtext: VueTypes.string.def(""),
    change: { type: Number, default: null },
    stats: VueTypes.arrayOf({
      label: VueTypes.string,
      value: VueTypes.number,
    }).isRequired,
    height: VueTypes.number,
  },
};
</script>
<style lang="sass" scoped>
@import '@/assets/style-constants'
#sh-progress-circular-info
  position: relative
  padding: 2rem 8rem 2rem 1rem
  display: flex
  align-items: center
  .stats
    top: 0
    bottom: 0
    right: 0
    position: absolute
    display: flex
    flex-direction: column
    justify-content: center
    align-items: center
    max-width: 100px
    font-size: $baseFontSize * 0.8
    > div
      margin-top: 0.25rem
      overflow: hidden
      width: 100%
      text-align: center
      padding: 0.25rem 1rem
      border: 1px solid rgba(black, 0.1)
      border-right: 0 !important
      border-top-left-radius: 10px
      border-bottom-left-radius: 10px
      .statistic-value
        font-size: $baseFontSize
        font-weight: bold
</style>
