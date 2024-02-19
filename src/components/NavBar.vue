<template>
  <nav>
    <div>
      <a href="/"> <img src="/logo.svg" alt="Logo Image" class="logo" /></a>
    </div>
  </nav>
</template>

<style scoped>
nav {
  height: 128px;
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: space-between;
}
.logo {
  max-width: 256px;
}

button {
  background-color: transparent;
  border: 2px solid var(--primary-color);
  padding: 8px 32px;
  font-weight: bold;
  cursor: pointer;
}

button:hover {
  background-color: var(--primary-color);
  transition: 0.3s;
}

@media (max-width: 1024px) {
  nav {
    justify-content: center;
  }

  .logo {
    max-width: 172px;
  }
}




</style>
