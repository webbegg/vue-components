<template>
  <div id="app">
    <div class="row">
      <form class="col-sm-8 col-sm-offset-2">
        <input-text label="Nombre" name="txtNombre" v-model="formData.nombre" class="col-sm-6" required></input-text>
        <input-text label="Apellidos" name="txtApellidos" v-model="formData.apellidos" class="col-sm-6"></input-text>
        <input-text type="number" label="Edad" name="txtEdad" v-model="formData.edad" class="col-sm-3"></input-text>
        <input-text type="email" label="Email" name="txtEmail" v-model="formData.email" required class="col-sm-9"></input-text>
        <button type="button" class="btn btn-primary btn-block">
          <i class="glyphicon glyphicon-save"></i>
          GUARDAR
        </button>
      </form>
    </div>
    <hr>
    <pre>{{ $data }}</pre>
  </div>

</template>

<script>
import InputText from './components/InputText.vue'

export default {
  components: { InputText },
  data () {
    return {
      formData: {
        nombre: 'Marcos',
        apellidos: 'Juan Juan',
        edad: 21,
        email: 'marcos@immsoluciones.com'
      }
    }
  }
}
</script>

<style>
body {
  background-color: #f2f2f2;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
