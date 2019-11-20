<template>
  <div class="hero h-56 bg-gray-200 rounded">
    <div class="header">
      <h1 class="text-3xl font-bold text-gray-600">No Todos Found</h1>
      <p class="text-gray-600">Add more todos to fill to your list!</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Hero'
}
</script>

<style scoped>
.hero {
  display: flex;
  align-items: center;
  justify-content: center;
}
.hero > .header {
  padding: 20px;
  text-align: center;
}
.hero > .header > p {
  padding: 10px;
}
</style>