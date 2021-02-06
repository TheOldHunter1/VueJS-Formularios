<template>
  <div class="container">
      <form>
          <div class="row">
              <div class="col-xs12 col-sm-8 col-md-6">
                <h1>Formulario de contacto</h1>
                <hr>
                <div class="form-group">
                    <label for="nombre">Nombre:</label>
                    <input type="text" id="nombre" v-model='datosPersona.nombre'  class="form-control">
                </div>
                <div class="form-group">
                    <label for="email">E-Mail:</label>
                    <input type="text" id="email"  v-model='datosPersona.email' class="form-control">
                </div>
              </div>
            <div class="row">
                <div class="col-xs12 col-sm-8 col-md-6">
                    <label for="mensaje">Mensaje:</label>
                    <textarea id="email" cols="30" rows="5"  v-model='mensaje' class="form-control"></textarea>
              </div>
            </div>
          </div>
          <div class="row">
              <div class="col-xs12 col-sm-8 ol-md-6">
                  <div class="form-group">
                      <label for="enviarEmail">
                        <input type="checkbox" id="enviarMail" value="enviarmail" v-model="opcionMail">Enviar Email
                      </label>&nbsp;&nbsp;
                      <label for="enviarmecopia">
                          <input type="checkbox" id="enviarCopia" value="enviarcopia" v-model="opcionMail">Enviar Copia
                      </label>
                  </div>
              </div>
          </div>
          <div class="row">
              <div class="col-xs12 col-sm-8 ol-md-6">
                  <div class="form-group">
                      <label for="masculino">
                        <input type="radio" id="masculino" value="Masculino" v-model="genero">Masculino
                      </label>&nbsp;&nbsp;
                      <label for="femenino">
                          <input type="radio" id="femenino" value="Femenino" v-model="genero">Femenino
                      </label>
                  </div>
              </div>
          </div>
            <div class="row">
              <div class="col-xs12 col-sm-8 ol-md-6">
                  <div class="form-group">
                        <label for="horario">Horario</label>
                        <select id="horario" class="form-control"  v-model="horario">
                            <option :value="ophorario" v-for="ophorario in horarios" :key="ophorario" :selected="ophorario == 'Mañana'">{{ophorario}}</option>
                        </select>
                  </div>
              </div>
          </div>
            <div class="row">
                <div class="col-xs12 col-sm-8 ol-md-6">
                    <button class="btn btn-primary" @click.prevent="enviar()">Enviar datos</button>
                </div>
            </div>
      </form>
      <div class="row" v-if="enviado">
            <div class="col-xs12 col-sm-8 col-md-6">
                <div class="panel panel-default">
                    <div class="panel-heading">
                        <h3>Datos ingresados:</h3>
                    </div>
                    <div class="panel-body">
                        <p>Nombre: {{datosPersona.nombre}}</p>
                        <p>E-Mail: {{datosPersona.email}}</p>
                        <p style="white-space:pre">Mensaje: <br>{{mensaje}}</p>
                        <p> Opcion de envio:
                            <ul>
                                <li v-for="opcion in opcionMail" :key="opcion">
                                    {{opcion}}
                                </li>
                            </ul>
                        </p>
                        <p>Genero: {{genero}}</p>
                        <p>Horario: {{horario}}</p>
                    </div>
                </div>
            </div>
      </div>
  </div>
</template>

<script>


export default {
  name: 'formulario',
  data(){
      return{
            datosPersona:{
                nombre:'',
                email:''
          },
          mensaje:'',  
          opcionMail:[],
          genero:'',
          horario:'',
          horarios:['Mañana', 'Tarde', 'Noche'],
          enviado: false
      }
  },
  methods: {
      enviar(){
          this.enviado = true;
      }
  },
}
</script>

<style>

</style>
