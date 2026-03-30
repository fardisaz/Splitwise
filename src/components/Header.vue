<template>
  <div>
    <input />
    <v-for ="(item, index) in items" :key="index" />
  </div>
</template>
<style scoped>
input {
  margin: 20px;
}
</style>
