<template>
  <div id="app">
    <div class="row">
      <div class="col" v-for="{number, themeKey} in displays" :key="themeKey">
        <div class="card">
          <div class="card-header">
            <h4 class="card-title">Display {{number}}</h4>
          </div>
          <div class="card-body">
            <ThemeDisplay :theme-key="themeKey" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import "./styles/styles.scss";
import "../node_modules/@fortawesome/fontawesome-free/css/all.css";
import ThemeDisplay from "./ThemeDisplay";
export default {
  components: {
    ThemeDisplay
  },
  data() {
    return {
      displays: [
        {
          number: 1,
          themeKey : "theme-first"
        },
        {
          number: 2,
          themeKey : "theme-second"
        }
      ]
    };
  }
};
</script>

<style lang="sass" scoped>
.card
    height: 100%
.row
    margin:10px
    height: calc(100vh - 20px)
</style>