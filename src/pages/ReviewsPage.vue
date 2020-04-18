<template>
  <div>
    <a-row :gutter="48" type="flex" align="middle">
      <a-col :xs="24" :sm="18">
        <AButton type="tab" active>Today</AButton>
        <AButton type="tab">7 Days</AButton>
        <AButton type="tab">30 Days</AButton>
        <AButton type="tab">Custom</AButton>
      </a-col>
      <a-col :xs="24" :sm="6" class="text-right">
        <AButton icon="filter" size="large" iconDirection="right"
          >Filter</AButton
        >
      </a-col>
    </a-row>

    <!-- engagement score board -->
    <a-row :gutter="48">
      <a-col :sm="24">
        <EngagementScrollCard />
      </a-col>
    </a-row>

    <!-- response rate, focus chart -->
    <a-row :gutter="48">
      <a-col :sm="7">
        <PageSection title="Response Rate">
          <ProgressCircularWithInfo
            :progress="55"
            :stats="responseRateStats"
            :height="220"
          />
        </PageSection>
      </a-col>
      <a-col :sm="17">
        <PageSection title="Focus On">
          <Card><Chart /></Card>
        </PageSection>
      </a-col>
    </a-row>
  </div>
</template>
<script>
import AButton from "@/components/AButton.vue";
export default {
  components: {
    AButton,
    Card: () => import("@/components/Card.vue"),
    Chart: () => import("@/components/Chart.vue"),
    ProgressCircularWithInfo: () =>
      import("@/components/ProgressCircularWithInfo.vue"),
    PageSection: () => import("@/components/PageSection.vue"),
    EngagementScrollCard: () =>
      import("@/components/EngagementScrollCard.vue"),
  },
  data: () => ({
    responseRateStats: [
      { label: "Responses", value: 28 },
      { label: "Teams", value: 4 },
      { label: "Pending", value: 32 },
    ],
  }),
};
</script>
<style lang="sass" scoped>
.text-right
  text-align: right
div > div + .ant-row
  margin-top: 3rem
</style>
