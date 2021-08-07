<template>
  <h1>{{ name }}</h1>
  <img class="persona" :alt="name + ' icon'" src="./assets/persona.svg" />
  <SocialLinks :title="name" :links="links" />
</template>

<script>
import SocialLinks from "./components/SocialLinks.vue";
import AppConfig from "../config.js";

export default {
  name: "App",
  data() {
    return {
      name: AppConfig.name,
      links: AppConfig.links,
    };
  },
  components: {
    SocialLinks,
  },
};
</script>

<style lang="scss">
@import "./scss/variables";

* {
  box-sizing: border-box;
}

h1 {
  position: absolute;
  z-index: 2;
  width: 100%;
  text-align: center;
}

html,
body {
  background: radial-gradient(circle, $bg-color-1, $bg-color-2);
  font-size: $default-size;
  height: 100%;
  padding: 0;
  margin: 0;
  overflow: hidden;
}

#app {
  font-family: $font-family;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: $accent-color;
  height: 100%;
  overflow: hidden;
}

.btn {
  display: flex;
  background: $accent-color;
  padding: 0.7em 1.5em;
  border-radius: 1.5em;
  border: 3px solid $accent-color;
  color: $accent-color;
  text-decoration: none;
  text-align: center;
  font-weight: bold;
  transition-duration: 0.5s;
  justify-content: center;
  align-items: center;
  color: darken($accent-color, 50%);
  position: relative;
  margin-top: 3px;
  margin-left: 3px;

  &:hover {
    margin-top: 0;
    margin-left: 0;

    &::before {
      top: -3px;
      left: -3px;
    }
  }

  & > img {
    height: $icon-size;
    width: $icon-size;
    margin-right: 1em;
    margin-left: -0.7em;
  }

  &::before {
    content: "";
    position: absolute;
    z-index: -1;
    top: -6px;
    left: -6px;
    background: darken($accent-color, 30%);
    border: 3px solid darken($accent-color, 30%);
    border-radius: 1.5em;
    width: 100%;
    height: 100%;
    transition-duration: 0.5s;
  }
}

.f-w {
  width: 100%;
}

.social-links {
  position: absolute;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 3;
  text-align: center;
  overflow: auto;

  ul {
    list-style: none;
    max-width: 300px;
    margin: 0 auto;
    padding: 0;

    li {
      margin: 1em;
    }
  }
}

.persona {
  position: absolute;
  z-index: 1;
  max-width: $persona-width;
  width: 100%;
  top: 8px;
  left: 50%;
  margin-left: -1 * $persona-width * 0.5;
}

@media (orientation: landscape) {
  h1 {
    position: relative;
  }

  .social-links {
    display: flex;
    flex-direction: column;
    justify-content: center;
    top: 0;
    left: $persona-width * 0.625;
  }

  .persona {
    top: auto;
    bottom: -20%;
    left: -1 * $persona-width * 0.3;
    margin-left: 0;
  }
}

@media (min-height: $persona-width * 1.2) {
  .persona {
    bottom: -10px;
  }
}

@media (min-width: $persona-width * 3) {
  .social-links {
    left: 0;
  }
}
</style>
