<template>

  <div>
    <h1> Ver Estudiente</h1>
    <div>
      <h2>{{ student.first_name }} {{ student.last_name}}</h2>
      <p>Edad: {{ student.age}}</p>
      <p>Celular: {{ student.cell_phone}}</p>
      <p>Direccion: {{ student.address}}</p>
    </div>
    <button type="button" v-on:click="destroy">Eliminar</button>
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
  },
  methods:{
    async destroy(){
      if(confirm("Desea eliminar al estudiente " + this.student.first_name + " " + this.student.last_name )){
        const res = await axios.delete('http://127.0.0.1:8000/api/students/' + this.$route.params.id);
        console.log(res.data);
        this.$router.push("/students");

      }
    }
  }
}
</script>

