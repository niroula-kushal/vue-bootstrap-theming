<template>
  <div id="app">
    <button class="btn btn-info" @click="toggleTheme">
        Day/Night
    </button>
    <div id="nav" class="cst">
      <router-link to="/" class="btn btn-primary">Home</router-link> |
      <router-link to="/about" class="btn btn-warning">About</router-link>
    </div>
    <transition name="slide-fade" mode="out-in">       
      <router-view />
    </transition>
  </div>
</template>

<script>
import "./styles.scss";
const bodyElm = document.querySelector("body");
const tempTransitionalClass = "temp-transitional";

export default {
  data () {
    return {
      theme : "light"
    }
  },
  methods: {
    toggleTheme() {
      bodyElm.classList.add(tempTransitionalClass);
      if(this.theme === "light") {
        this.theme = "dark";
        bodyElm.classList.remove("theme-light");
        bodyElm.classList.add("theme-dark");
      }
      else {
        this.theme = "light";
        bodyElm.classList.remove("theme-dark");
        bodyElm.classList.add("theme-light");
      }
      setTimeout(() => bodyElm.classList.remove(tempTransitionalClass), 1000);
    }
  }
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');
/* Enter and leave animations can use different */
/* durations and timing functions.              */
.slide-fade-enter-active {
  transition: all .3s ease;
}
.slide-fade-leave-active {
  transition: all .3s cubic-bezier(1.0, 0.5, 0.8, 1.0);
} 
.slide-fade-enter {
  transform : translate(-10%);
}
.slide-fade-leave-to
/* .slide-fade-leave-active below version 2.1.8 */ {
  transform: translateX(10%);
  opacity: 0;
}
#app {
  font-family: 'Roboto', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
  }
}

.temp-transitional {
  &, & *, & *:before, & *:after {
    transition: all .3s;
  }
}
</style>

