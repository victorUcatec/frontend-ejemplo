<template>
  <div >
    <h1 class="uppercase font-bold">Vista de estudiantes</h1>
    <nuxt-link class="text-pink-600 font-bold" to="/students/create">Crear nuevo estudiente</nuxt-link>
    <Student
      v-for="student of students"
      :key="student.id"
      :first_name="student.first_name"
      :last_name="student.last_name"
    />
  </div>

</template>
<script>
import axios from 'axios';
import Student from "@/components/Student";
export default {
  components:{
    Student,
  },
  data(){
    return{
      students: []
    }
  },
  async created(){
    const res = await axios.get('http://127.0.0.1:8000/api/students');
    this.students = res.data;
    console.log(this.students);
  }

}

</script>
