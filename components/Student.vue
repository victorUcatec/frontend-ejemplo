<template>
  <div>
    <p>Estudiente: {{ first_name }} {{ last_name}}</p>
  </div>
</template>

<script>
export default {
  name: 'Student',
  props: ['first_name', 'last_name'],
}
</script>
