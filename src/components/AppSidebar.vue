<template>
  <div id="app-sidebar" :class="{ collapsed: $props.collapsed }">
    <div
      class="logo"
      @click="$emit('toggleSidebar', !$props.collapsed)"
    >
      S
    </div>
    <div class="main-navigation">
      <ul class="parent">
        <li
          v-for="(link, linkIndex) in links"
          :key="linkIndex"
          :class="{ active: checkCurrentRoute(link.link) }"
        >
          <span class="title" @click="doLinkClick(link.link)">
            <a-icon :type="link.icon" />
            <span>{{ link.label }}</span>
          </span>
          <ul
            class="children"
            v-if="
              checkCurrentRoute(link.link) &&
                link.children &&
                link.children.length
            "
          >
            <li
              v-for="(c, cIndex) in link.children"
              :key="cIndex"
              :class="{
                active: checkChildRoute(c.link),
              }"
            >
              <span class="title" @click="doLinkClick(c.link, true)">
                <span>{{ c.label }}</span>
              </span>
            </li>
          </ul>
        </li>
      </ul>
    </div>
  </div>
</template>
<script>
import VueTypes from "vue-types";
export default {
  props: {
    collapsed: VueTypes.bool.def(false),
  },
  model: {
    prop: "collapsed",
    event: "toggleSidebar",
  },
  data: () => ({
    links: [
      {
        id: "home",
        label: "Home",
        icon: "home",
        link: "/",
      },
      {
        id: "reports",
        label: "Reports",
        icon: "file-text",
        link: "/reports",
        children: [
          {
            id: "reports-overview",
            label: "Overview",
            link: "/reports/overview",
          },
          {
            id: "reports-engagement",
            label: "Engagement",
            link: "/reports/engagement",
          },
          {
            id: "reports-wellbeing",
            label: "Wellbeing",
            link: "/reports/wellbeing",
          },
          {
            id: "reports-customs",
            label: "Customs",
            link: "/reports/customs",
          },
        ],
      },
      {
        id: "insights",
        label: "Insights",
        icon: "line-chart",
        link: "/insights",
      },
      {
        id: "surveys",
        label: "Surveys",
        icon: "bar-chart",
        link: "/surveys",
        children: [
          {
            label: "Dummy 1",
            link: "/surveys/overview",
          },
          { label: "Dummy 2", link: "/surveys/engagement" },
          { label: "Dummy 3", link: "/surveys/wellbeing" },
          { label: "Dummy 4", link: "/surveys/customs" },
        ],
      },
    ],
    currentRoute: "/home",
  }),
  mounted() {
    this.currentRoute = window.location.pathname;
  },
  methods: {
    /* eslint-disable no-unused-vars */
    doLinkClick(link) {
      this.currentRoute = link;
      window.history.replaceState(null, "", link);
    },
    checkCurrentRoute(link) {
      return (
        link.replace("/", "") === this.currentRoute.split("/")[1]
      );
    },
    checkChildRoute(link) {
      return link === this.currentRoute;
    },
  },
};
</script>

<style lang="sass" scoped>
@import '@/assets/style-constants.sass'
#app-sidebar
  position: fixed
  height: 100vh
  left: 0
  top: 0
  bottom: 0
  padding: 2rem
  text-align: right
  background: white
  z-index: 10000
  width: $sidebarWidth
  transition: all 0.1s ease-in-out
  &.collapsed
    width: $sidebarCollapsedWidth
    padding: 0
    .logo
      text-indent: 0
      text-align: center
      padding: 1rem 0
      background-image: none
    .main-navigation
      ul.parent > li > span.title > span
        display: none
      ul.children
        display: none
      ul.parent > li.active > span.title
        box-shadow: none
  @media (max-width: 767px)
    display: none
  .logo
    text-indent: 999999px
    cursor: pointer
    // overflow: auto
    // width: 300px
    height: 53px
    background-repeat: no-repeat
    background-image: url('https://uploads-ssl.webflow.com/5e2ea44912d9356838f9bb77/5e3975afd760944067dce1b6_Artboard%202%20copySUPERH.svg')
    background-position: 0px 0px
    background-size: contain
    -o-object-fit: none
    object-fit: none
  .main-navigation
    margin-top: 2rem
    ul.parent
      text-align: left
      margin: 0
      padding: 0
      list-style-type: none
      font-size: 1rem
      > li
        margin-bottom: 1rem
        span.title
          width: 100%
          display: inline-block
          cursor: pointer
          padding: 0.75rem 1rem
          border-radius: 50px
          .anticon
            margin-right: 5px
        &.active
          > span.title
            background: white
            box-shadow: $cardShadow
            color: $primaryColor
        ul.children
          font-size: $baseFontSize * 0.85
          text-align: left
          margin: 0.5rem 0 0 1rem
          padding: 0
          list-style-type: none
          li
            &.active
              span.title
                color: $primaryColor
</style>
