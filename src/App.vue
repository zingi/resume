<template>
  <div id="app-container">
    <headline></headline>
    <locale-changer></locale-changer>
    <general-info></general-info>
    <work-experiance></work-experiance>
    <education></education>
    <technologies></technologies>
    <contact></contact>
  </div>
</template>

<script>
import Contact from './components/Contact.vue'
import Education from './components/Education.vue'
import GeneralInfo from './components/GeneralInfo.vue'
import Headline from './components/Headline.vue'
import LocaleChanger from './components/LocaleChanger.vue'
import Technologies from './components/Technologies.vue'
import WorkExperiance from './components/WorkExperiance.vue'

export default {
  name: 'App',
  components: {
    Headline,
    WorkExperiance,
    Education,
    LocaleChanger,
    GeneralInfo,
    Technologies,
    Contact
  },
  setup () {}
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Fira+Code:wght@400;600&display=swap');

html {
  * { padding: 0; margin: 0; }
  font-size: 16px;
}

button {
  all: unset;
  cursor: pointer;
  font-size: 1rem;
}

#app {
  font-family: 'Fira Code', monospace;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

#app-container {
  margin: 0 auto;
  padding: 0.5rem;
  max-width: 1000px;
}

#general-info-container {
  display: grid;
  grid-template-columns: 0.5fr 1fr;
  margin-top: 2rem;
}

#general-info-container .key {
  font-weight: 600;
}

h1 {
  font-size: 3rem;
  font-weight: 600;
  word-break: break-all;
}

h2 {
  margin-top: 4rem;
  font-weight: 600;
}

#hire-me-container {
  margin-top: 2rem;
  display: inline-block;
  border-radius: 3px;
  padding: 5px 20px 5px 20px;
}

.timelist-element {
  margin-top: 2rem;
  border-radius: 3px;
  padding: 5px;
}

.timelist-element .time-period,.locale-button {
  color: rgb(150, 150, 150);
}

#contact-container {
  margin-bottom: 10rem;
}

#m-button {
  margin-top: 2rem;
  text-decoration: underline;
}

#links {
  display: grid;
  width: max-content;
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-rows: 1fr;
  justify-items: center;
  margin: 2rem 0 0 0;
  column-gap: 1rem;
}

#links img {
  height: 2rem;
}

#logo-canvas {
  display: inline-block;
  margin-top: 2rem;
  background: blanchedalmond;
  border-radius: 3px;
}

.animated-gradient-background {
  color: rgba(255,255,255,0.9);
  background: linear-gradient(-45deg, #ffa63d, #ff3d77, #338aff, #3cf0c5);
  background-size: 600%;
  animation: background-animation 30s linear infinite;
}
@keyframes background-animation {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}

@media only screen and (max-width: 768px) {
  h1 {
    font-size: 2rem;
  }

  #general-info-container {
    grid-template-columns: 1fr;
    grid-template-rows: 1fr 1fr;
  }

  #general-info-container div:nth-child(2n+1):not(:first-child) {
    margin-top: 0.5rem;
  }
}

/* system dark mode */
@media (prefers-color-scheme: dark) {
  html {
    background: black;
    color: blanchedalmond;
  }

  .timelist-element .time-period,.locale-button {
    color: blanchedalmond;
    opacity: 0.6;
  }

  .logo {
    filter: invert(86%) sepia(5%) saturate(1826%) hue-rotate(332deg) brightness(111%) contrast(101%);
  }

  #linkedin-logo {
    background: blanchedalmond;
    border-radius: 5px;
  }
}

</style>
