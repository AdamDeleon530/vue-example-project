<template>
  <div id="app">
    <app-nav></app-nav>
    <div class="container app-content">
      <router-view></router-view>
    </div>
    <app-footer></app-footer>
  </div>
</template>

<script>
import AppNav from "./AppNav.vue";
import AppFooter from "./AppFooter.vue";
export default {
  name: "app",
  components: { AppNav, AppFooter },
  data() {
    return {
      message: "Hello, World!",
    };
  },
  created() {
    // Deprecated: Vue.extend usage
    const MyComponent = Vue.extend({
      template: "<div>{{ message }}</div>",
      data() {
        return {
          message: "This is a deprecated example",
        };
      },
    });
  },
  mounted() {
    // Deprecated: Filters (removed in Vue 3)
    this.$options.filters = {
      uppercase(value) {
        if (!value) return "";
        return value.toString().toUpperCase();
      },
    };
  },
  methods: {
    doSomething() {
      console.log(this.$options.filters.uppercase(this.message));
    },
  },
};
</script>

<style lang="scss">
html {
  position: relative;
  min-height: 100%;
}
body {
  /* Margin bottom by footer height */
  margin-bottom: 60px;
}
.app-content {
  padding: 60px 15px 0;
}
</style>
