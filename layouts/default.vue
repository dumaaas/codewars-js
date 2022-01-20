<template>
  <div>
    <div class="content">
      <Nuxt />
    </div>
  </div>
</template>

<script>
export default {
  components: {},
}
</script>

<style>
body::-webkit-scrollbar {
  width: 12px; /* width of the entire scrollbar */
}
body::-webkit-scrollbar-track {
  background: #1F1F1F; /* color of the tracking area */
}
body::-webkit-scrollbar-thumb {
  background-color: #bb86fc; /* color of the scroll thumb */
  border-radius: 20px; /* roundness of the scroll thumb */
  border: 1px solid #121212; /* creates padding around scroll thumb */
}
html {
  font-family: 'Mulish', -apple-system, BlinkMacSystemFont, 'Arial', Roboto,
    Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
}

h1,
h2,
h3,
h4 {
  font-family: 'Poppins', -apple-system, BlinkMacSystemFont, 'Arial', Roboto,
    Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  font-weight: 600;
}
</style>
