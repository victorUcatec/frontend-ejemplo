<template>
  <div>
    <p>Estudiente: {{ first_name }} {{ last_name}}</p>
    <nuxt-link :to="`/students/${id}/show`"> Mostrar estudiante</nuxt-link>
    <nuxt-link :to="`/students/${id}/edit`"> Editar estudiante</nuxt-link>
  </div>
</template>

<script>
export default {
  name: 'Student',
  props: ['id', 'first_name', 'last_name'],
}
</script>
