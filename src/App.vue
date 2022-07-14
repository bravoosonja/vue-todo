<template>
  <div class="wrapper">
    <div class="background-image" />
    <div class="overlay">
      <header>
        <div class="header">
          <h1>TODO</h1>
          <div class="icons">
            <button @click="toggleDark()">
              <img
                v-if="isDark"
                src="./assets/images/icon-sun.svg"
                alt="switch to light mode"
              />
              <img
                v-if="!isDark"
                src="./assets/images/icon-moon.svg"
                alt="switch to dark mode"
              />
            </button>
          </div>
        </div>
      </header>
      <Navbar />
    </div>
  </div>
  <router-view />
</template>

<script>
import Navbar from "./components/Navbar.vue";
export default {
  components: { Navbar },
};
</script>

<script setup>
import { useDark, useToggle } from "@vueuse/core";
const isDark = useDark();
const toggleDark = useToggle(isDark);
</script>

<style>
:root {
  --text: hsl(236, 9%, 61%);
  --hover-text: hsl(235, 19%, 35%);
  --sub-text: hsl(233, 11%, 84%);
  --background: hsl(236, 33%, 92%);
  --form-background: hsl(0, 0%, 98%);

  --accent: hsl(220, 98%, 61%);
  --gradient: linear-gradient hsl(192, 100%, 67%) to hsl(280, 87%, 65%);
  --box-shadow: rgba(0, 0, 0, 0.56) 0px 22px 70px 4px;
  --desktop-image: url("./assets/images/bg-desktop-light.jpg");
  --mobile-image: url("./assets/images/bg-mobile-light.jpg");
}

:root.dark {
  --text: hsl(236, 33%, 92%);
  --hover-text: hsl(234, 39%, 85%);
  --sub-text: hsl(234, 11%, 52%);
  --background: hsl(235, 21%, 11%);
  --form-background: hsl(237, 14%, 26%);
  --desktop-image: url("./assets/images/bg-desktop-dark.jpg");
  --mobile-image: url("./assets/images/bg-mobile-dark.jpg");
}

*,
*::before,
*::after {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "Albert Sans", sans-serif;
  -webkit-font-smoothing: antialiased;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  width: 100%;
  height: 100vh;
  background-color: var(--background);
}

h1 {
  font-weight: 600;
  color: var(--text);
}

h2 {
  font-weight: 500;
  color: var(--text);
}

p {
  font-weight: 400;
  color: var(--text);
  font-size: 18px;
}

span {
  color: var(--sub-text);
  font-size: 16px;
}

ul,
li {
  color: var(--text);
  background-color: var(--form-background);
  font-size: 18px;
  padding: 1rem 1.3rem;
  width: 100%;
  border-radius: 5px;
  outline: none;
  border: none;
  list-style: none;
}

ul,
li:focus {
  outline: 1px solid var(--text);
}

input[type="text"] {
  color: var(--text);
  background-color: var(--form-background);
  font-size: 18px;
  padding: 1rem 1.3rem;
  width: 100%;
  border-radius: 5px;
  outline: none;
  border: none;
}

input [type="text"]::placeholder {
  color: var(--sub-text);
}

input [type="text"]::focus {
  outline: 1px solid var(--text);
}

input [type="text"]::active {
  background-color: var(--form-background);
  color: var(--text);
  outline: 1px solid var(--text);
}

form {
  width: 40vw;
  box-shadow: var(--box-shadow);
}
</style>

<style scoped>
.wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  width: 100%;
  height: 100%;
  position: relative;
}
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 40vw;
}

.background-image {
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
}

@media (min-width: 375px) {
  .background-image {
    background-image: var(--mobile-image);
    width: 100vw;
    height: 200px;
  }
}
@media (min-width: 1440px) {
  .background-image {
    background-image: var(--desktop-image);
    width: 100vw;
    height: 300px;
  }
}

.overlay {
  position: absolute;
  top: 3vh;
  width: 100%;
  height: 100%;
  position: absolute;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

h1 {
  font-size: 2.5rem;
  letter-spacing: 1.3rem;
}
button {
  background-color: transparent;
  border: none;
  cursor: pointer;
}
</style>