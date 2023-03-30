<template>
  <div class="nav">
    <span><NuxtLink to="/">Home</NuxtLink></span>
    <span><NuxtLink to="/details">Details</NuxtLink></span>
  </div>
</template>

<script>
export default {};
</script>

<style>
.nav {
  display: flex;
  align-items: center;
  gap: 16px;
  padding: 16px;
  height: 100px;
  box-shadow: 0px 0px 24px -5px rgba(66, 68, 90, 1);
  border-radius: 4px;
}

.nav > span {
  font-size: 24px;
}
</style>