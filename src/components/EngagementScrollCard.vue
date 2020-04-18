<template>
  <ScrollCard>
    <template v-slot:highlight>
      <div class="highlight-content">
        <div class="title">Engagement Score</div>
        <div class="value">
          {{ engagementMetrics.score }}
          <span class="change">
            <a-icon :type=" engagementMetrics.change > 0 ? 'arrow-up' : 'arrow-down' " />
            {{ engagementMetrics.change }}
          </span>
        </div>
        <div class="fraction">{{ engagementMetrics.answered }} / {{ engagementMetrics.total }}</div>
      </div>
    </template>
    <template v-slot:scroll-content>
      <ProgressCircular
        v-for="(item, itemIndex) in scores"
        :key="itemIndex"
        :progress="item.score"
        :change="item.change"
        :subtext="item.label"
      />
    </template>
  </ScrollCard>
</template>
<script>
export default {
  components: {
    ScrollCard: () => import("./ScrollCard"),
    ProgressCircular: () => import("./ProgressCircular")
  },
  data: () => ({
    engagementMetrics: {
      score: 60,
      change: 3,
      answered: 28,
      total: 30
    },
    scores: [
      { label: "Motivation", score: 55, change: 3 },
      { label: "Work Stress", score: 55, change: -5 },
      { label: "Autonomy", score: 90, change: 3 },
      { label: "Autonomy", score: 90, change: 3 },
      { label: "Autonomy", score: 90, change: 3 }
    ]
  })
};
</script>
<style lang="sass" scoped>
@import '@/assets/style-constants.sass'
.highlight-content
  position: relative
  height: 100%
.title
  font-size: $baseFontSize * 1.2
.value
  font-size: $baseFontSize * 3
  display: flex
  align-items: center
  .change
    margin-left: 0.5rem
    font-size: $baseFontSize * 0.9
.fraction
  position: absolute
  bottom: 0.5rem
  right: 0.5rem
</style>