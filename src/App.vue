<script>
  export default {
    // Definimos los datos a usar 
    data() {
      return {
        errors: [],
        nya: null,
        email: null,
        asunto: null,
        area: "",
        archivo: null,
        mensaje: null,
      }
    },
    methods: {
      // Función para validar los campos del formulario 
      validarFormulario: function (e) {
        if (this.nya && this.email && this.asunto && this.area && this.archivo !== null && this.mensaje) {
          return true;
        }
        
        this.errors = [];

        if (!this.nya) {
          this.errors.push('Por favor, ingresa tus Nombres y Apellidos.');
        }
        if (!this.email) {
          this.errors.push('Por favor, ingresa tu Email.');
        }
        if (!this.asunto) {
          this.errors.push('Por favor, ingresa un Asunto.');
        }
        if (!this.area) {
          this.errors.push('Por favor, Selecciona un Área.');
        } 
        if (!this.archivo) {
          this.errors.push('Por favor, Selecciona un Archivo.');
        }
        if (!this.mensaje) {
          this.errors.push('Por favor, ingresa tu Mensaje.');
        }
        
        e.preventDefault();
      },
      // Función para validar un archivo seleccionado 
      archivoSeleccionado(event) {
        this.archivo = event.target.files[0];
      }
    }
  }
</script>

<template>
  <main role="main">
    <div class="container">
      <div class="row">
        <div class="col-md-12 mt-5">
          <h1>Como Validar un Formulario con Vue JS 3</h1>
          <form @submit="validarFormulario">

            <p v-if="errors.length">
              <b>Por favor verificar:</b>
              <ul>
                <li v-for="error in errors" class="text-danger">{{ error }}</li>
              </ul>
            </p>

            <div class="mb-3">
              <label for="nya" class="form-label">Nombres y Apellidos</label>
              <input type="text" class="form-control" id="nya" v-model="nya" aria-describedby="nyaHelp">
              <div id="nyaHelp" class="form-text">Ejemplo: Carlos Rojas Torres</div>
            </div>
            <div class="mb-3">
              <label for="email" class="form-label">Email</label>
              <input type="email" class="form-control" id="email" v-model="email" aria-describedby="emailHelp"> 
              <div id="emailHelp" class="form-text">Ejemplo: crojas@mail.com</div>             
            </div>
            <div class="mb-3">
              <label for="asunto" class="form-label">Asunto</label>
              <input type="text" class="form-control" id="asunto" v-model="asunto" aria-describedby="asuntoHelp">
              <div id="asuntoHelp" class="form-text">Ejemplo: Compra de Productos</div>
            </div>
            <div class="mb-3">
              <label for="area" class="form-label">Área o Departamento</label>             
              <select class="form-select" id="area" v-model="area" aria-label="Default select example" aria-describedby="areaHelp">
                <option value="" disabled selected>Seleccionar:</option>
                <option value="1">Ventas</option>
                <option value="2">Marketing</option>
                <option value="3">Soporte</option>
              </select>
              <div id="areaHelp" class="form-text">Ejemplo: Ventas</div>
            </div>
            <div class="mb-3">
              <label for="archivo" class="form-label">Adjuntar Archivo</label>
              <input class="form-control" type="file" id="archivo" v-on:change="archivoSeleccionado">
            </div>
            <div class="mb-3">
              <label for="mensaje" class="form-label">Mensaje</label>
              <textarea class="form-control" id="mensaje" v-model="mensaje" rows="3"></textarea>
            </div>
            <button type="submit" class="btn btn-primary">Enviar</button>
          </form>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
  /* */
</style>
