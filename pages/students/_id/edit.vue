<template>
  <div>
    <h1>Editar estudiente</h1>
    <nuxt-link to="/students">Listado de estudientes</nuxt-link>

    <form @submit.prevent="update">
      <div>
        <label>Nombre</label>
        <input class="placeholder:italic placeholder:text-slate-400 block bg-white w-full border border-slate-300 rounded-md py-2 pl-9 pr-3 shadow-sm focus:outline-none focus:border-sky-500 focus:ring-sky-500 focus:ring-1 sm:text-sm" type="text" v-model="student.first_name"/>
      </div>
      <div>
        <label>Apellido</label>
        <input class="placeholder:italic placeholder:text-slate-400 block bg-white w-full border border-slate-300 rounded-md py-2 pl-9 pr-3 shadow-sm focus:outline-none focus:border-sky-500 focus:ring-sky-500 focus:ring-1 sm:text-sm" type="text" v-model="student.last_name"/>
      </div>
      <div>
        <label>Edad</label>
        <input class="placeholder:italic placeholder:text-slate-400 block bg-white w-full border border-slate-300 rounded-md py-2 pl-9 pr-3 shadow-sm focus:outline-none focus:border-sky-500 focus:ring-sky-500 focus:ring-1 sm:text-sm" type="text" v-model="student.age"/>
      </div>
      <div>
        <label>Celular</label>
        <input class="placeholder:italic placeholder:text-slate-400 block bg-white w-full border border-slate-300 rounded-md py-2 pl-9 pr-3 shadow-sm focus:outline-none focus:border-sky-500 focus:ring-sky-500 focus:ring-1 sm:text-sm" type="text" v-model="student.cell_phone"/>
      </div>
      <div>
        <label>Direccion</label>
        <input class="placeholder:italic placeholder:text-slate-400 block bg-white w-full border border-slate-300 rounded-md py-2 pl-9 pr-3 shadow-sm focus:outline-none focus:border-sky-500 focus:ring-sky-500 focus:ring-1 sm:text-sm" type="text" v-model="student.address"/>
      </div>
      <button type="submit">Guardar</button>

    </form>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data(){
    return {
      student: {
        first_name: '',
        last_name: '',
        age: 0,
        cell_phone: '',
        address: '',
      }
    }
  },
  async created() {
    const res = await axios.get('http://127.0.0.1:8000/api/students/' + this.$route.params.id);
    this.student = res.data;
  },
  methods:{
    async update(){
      const res = await axios.put('http://127.0.0.1:8000/api/students/' + this.$route.params.id, this.student);
      console.log(res.data);

    }
  }
}
</script>

<style scoped>

</style>
