<template>
  <div>
    <Nuxt />
  </div>
</template>

<script>
export default {
  head() {
    return {
      meta: [
        {
          hid: 'Content-Security-Policy',
          'http-equiv': 'Content-Security-Policy',
          content: 'upgrade-insecure-requests'
        }
      ]
    }
  },
}
</script>

<style>
html {
  font-family:
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
}
html, body {
  background: #000;
  min-height: 100vh;
}
</style>
