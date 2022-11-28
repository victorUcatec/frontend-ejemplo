<template>

  <div>
    <h1> Ver Estudiente</h1>
    <div>
      <h2>{{ student.first_name }} {{ student.last_name}}</h2>
      <p>Edad: {{ student.age}}</p>
      <p>Celular: {{ student.cell_phone}}</p>
      <p>Direccion: {{ student.address}}</p>

    </div>
  </div>

</template>

<script>
import axios from "axios";
export default {
  data(){
    return{
      student: {}
    }
  },
  async created() {
    const res = await axios.get('http://127.0.0.1:8000/api/students/' + this.$route.params.id);
    this.student = res.data;
  }
}
</script>

