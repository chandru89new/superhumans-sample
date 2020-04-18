<template>
  <div id="app">
    <AppSidebar v-model="isSidebarCollapsed" />
    <AppHeader :class="{ expanded: isSidebarCollapsed }" />
    <div id="app-content" :class="{ expanded: isSidebarCollapsed }">
      <ReviewsPage />
    </div>
  </div>
</template>

<script>
import ReviewsPage from "./pages/ReviewsPage.vue";

export default {
  name: "App",
  components: {
    ReviewsPage,
    AppSidebar: () => import("@/components/AppSidebar.vue"),
    AppHeader: () => import("@/components/AppHeader.vue"),
  },
  data: () => ({
    isSidebarCollapsed: false,
  }),
};
</script>

<style lang="sass">
@import '@/assets/style-constants.sass'
#app
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif
  -webkit-font-smoothing: antialiased
  -moz-osx-font-smoothing: grayscale
  background: $appBackgroundColor
  position: relative
  font-size: 1rem
#app-content
  margin-left: $sidebarWidth
  margin-top: $headerHeight
  padding: 2rem 3rem
  transition: all 0.1s ease-in-out
  &.expanded
    margin-left: $sidebarCollapsedWidth
  @media (max-width: 767px)
    margin-left: 0
</style>
