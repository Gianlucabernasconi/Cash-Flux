<template>
  <div class="splashscreen">
    <img src="@/assets/cashflux.svg" alt="logo" />
    <h1><span>Cash</span>Flux</h1>
  </div>
</template>

<style scoped>
.splashscreen {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  height: 100vh;
  font-size: x-large;
  font-weight: 900;
}
h1 {
  color: #8e43c8;
}

.splashscreen span {
  color: #341294;
}

.splashscreen img {
  width: 350px;
  height: 350px;
}
</style>
