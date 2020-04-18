<template>
  <div id="app-header">
    <div class="search-area">
      <a-input placeholder="Search">
        <a-icon slot="suffix" type="search" />
      </a-input>
    </div>
    <div>
      <AvatarMenu
        :user="{
          name: 'Ben Franklin',
          img: 'https://randomuser.me/api/portraits/men/17.jpg',
        }"
      />
    </div>
  </div>
</template>
<script>
export default {
  components: {
    AvatarMenu: () => import("@/components/AvatarMenu.vue"),
  },
};
</script>
<style lang="sass" scoped>
@import '@/assets/style-constants.sass'
#app-header
  z-index: 99
  position: fixed
  top: 0
  right: 0
  left: $sidebarWidth
  height: $headerHeight
  border-bottom: 1px solid rgba(black, 0.1)
  background: $appBackgroundColor
  padding: 2.5rem
  display: flex
  align-items: center
  justify-content: space-between
  &.expanded
    left: $sidebarCollapsedWidth
  .search-area
    width: 75%
    ::v-deep .ant-input
      border-radius: 50px
      border: none
      width: 100%
      padding: 1.25rem
      font-size: $baseFontSize
</style>
