<template>
  <nav id="nav">
    <p class="logo">The Vue Route Travel App</p>
    <nav class="nav-links">
      <li class="links">
        <router-link to="/"> Home </router-link>
      </li>
      <li
        v-for="destination in destinations"
        :key="destination.name"
        class="links"
      >
        <router-link
          :to="{
            name: 'DestinationDetails',
            params: { slug: destination.slug },
          }"
        >
          {{ destination.name }}
        </router-link>
      </li>
    </nav>
  </nav>
</template>

<script>
import store from "@/store.js";

export default {
  data() {
    return {
      destinations: store.destinations,
    };
  },
};
</script>

<style scoped>
#nav {
  display: flex;
  align-items: center;
  position: sticky;
  top: 0;
  background-color: white;
  border-bottom: 1px solid grey;
  z-index: 1;
}
#nav a {
  color: #2c3e50;
  text-decoration: none;
  font-weight: bold;
}
#nav a.link-active {
  color: #42b983;
}
.nav-links {
  display: flex;
}
.links {
  padding: 20px;
  list-style: none;
}
.links:hover {
  text-decoration: underline;
}
.logo {
  font-size: 20px;
  color: purple;
  font-weight: bold;
}
</style>
