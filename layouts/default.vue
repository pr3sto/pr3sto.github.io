<template>
  <div>
    <nuxt />
  </div>
</template>

<style>
@font-face {
  font-family: "ArcaMajora3-Bold";
  src: url("/fonts/ArcaMajora3-Bold.eot");
  src: url("/fonts/ArcaMajora3-Bold.woff") format("woff"),
  url("/fonts/ArcaMajora3-Bold.woff") format("woff2")
}

html {
  font-family: 'ArcaMajora3-Bold', 'Helvetica Neue', Arial, sans-serif;
  font-size: 16px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
  overflow: auto;
}

body {
  margin: 0;
  padding: 0;
}

*, *::before, *::after {
  box-sizing: inherit;
}
</style>
