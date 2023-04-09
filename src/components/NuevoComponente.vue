<script>
export default {
  name: 'NuevoComponente',
}
</script>
<template>
  <h1>Este es una prueba de los Slots y la propiedad :is</h1>
  <slot>
    <h2>En caso de que no se muestre la info que quiero, quiero que se muestre este mensaje por medio de un H2 🤓</h2>
  </slot>
</template>