<template>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Bitter:wght@700&display=swap" rel="stylesheet">
  <div class="container">
    <Header />
    <DataTable />
  </div>
</template>

<script>
import Header from './components/Header';
import DataTable from './components/DataTable';

export default {
  name: 'App',
  components: {
    Header,
    DataTable
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

html, body {
  overflow-x: hidden;
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: 'Bitter', serif;
  color: white;
}

.container {
  padding: 2% 4%;
  background-image:
    linear-gradient(
      to bottom left,
      #6b7b85,
      #1f262c 65%
    );
}


</style>
