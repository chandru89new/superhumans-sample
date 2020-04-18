<template>
  <a-dropdown :trigger="['click']">
    <span class="user">
      {{ user.name }}
      <span class="avatar">
        <img :src="user.img" />
      </span>
      <strong><a-icon type="down"/></strong>
    </span>
    <template v-slot:overlay>
      <a-menu>
        <a-menu-item>App Settings</a-menu-item>
        <a-menu-item>User Settings</a-menu-item>
        <a-menu-item>Logout</a-menu-item>
      </a-menu>
    </template>
  </a-dropdown>
</template>
<script>
import VueTypes from "vue-types";
export default {
  props: {
    user: VueTypes.objectOf({
      name: VueTypes.string,
      img: VueTypes.string,
    }).isRequired,
  },
};
</script>
<style lang="sass" scoped>
.user
  cursor: pointer
  font-weight: bold
  .avatar img
    margin: 0 0.4rem
    height: 32px
    width: 32px
    border: 1px solid rgba(orange, 0.8)
    padding: 2px
    border-radius: 100px
</style>
