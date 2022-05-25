<template>
  <header>
    <router-link to="/">
      <h1><span>Vue</span>Movies</h1>
    </router-link>
  </header>
  <main>
    <router-view />
  </main>
</template>

<style lang="scss">
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  font-family: 'Fira Sans', sans-serif;

  &::selection {
    background: transparentize(#42b883, 0.5);
  }
}

body {
  background-color: #35495e;
}

a {
  text-decoration: none;
}

main {
  max-width: 400px;
  margin: 0 auto;
}

header {
  display: flex;
  align-content: center;
  justify-content: center;
  padding: 10px 16px;
  background-color: #2c3d43;
  box-shadow: 0px 0px 6px rgba(0, 0, 0, 0.1);

  h1 {
    color: #fff;
    font-size: 28px;

    span {
      color: #42b883;
    }
  }
}
</style>
