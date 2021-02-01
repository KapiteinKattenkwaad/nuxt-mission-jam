<template>
  <div class="container">
    <div>
      <p v-if="$fetchState.pending">
        Loading planets...
      </p>
      <p v-else-if="$fetchState.error">
        Error while loading planets
      </p>
      <div v-else v-for="planet in planets" :key="planet.slug">
        <NuxtLink :to="planet.slug">
          {{ planet.title }}
        </NuxtLink>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      planets: []
    }
  },
  async fetch() {
    this.planets = await fetch('https://api.nuxtjs.dev/planets')
      .then((res) => res.json())
  }
}
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
@apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
.container {
  margin: 0 auto;

  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
