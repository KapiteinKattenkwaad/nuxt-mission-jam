<template>
  <div class="container">
    <div>
      <PlanetsList />

      <h1 class="title">
        {{ planet.title }}
      </h1>
      <img :src="planet.image" :alt="planet.title">
    </div>
  </div>
</template>

<script>
export default {
  head() {
    return {
      title: this.planet.title,
      htmlAttrs: {
        lang: 'en'
      },
      meta: [
        { charset: 'utf-8' },
        { name: 'viewport', content: 'width=device-width, initial-scale=1' },
        { hid: 'description', name: 'description', content: this.planet.description }
      ],
    }

  },
  async asyncData ( {params} ) {
    const planet = await fetch (
      `https://api.nuxtjs.dev/planets/${params.slug}`
    ).then((res) => res.json())
    return { planet }
  }
}
</script>

<style>
img {
  height: 80px;
  width: auto;
  object-fit: cover;
  margin: auto;
}
.container {
  margin: 0 auto;
  min-height: 100vh;
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
