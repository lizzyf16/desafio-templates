<template>
  <div id="app">
    <section class="container  mt-5">
      <div class="text-center my-5">
        <h1>Templates de Cuadro con Texto</h1>
      </div>
      <div class="row">
        <div class="col-4 inputs p-3 text-start">
          <div class="d-flex flex-column py-3">
            <label class="text-light py-1" for="cFondo">Color de Fondo</label>
            <input type="color" id="cFondo" name="cFondo" v-model="cFondo">
          </div>
          <div class="d-flex flex-column py-3">
            <label class="text-light py-1" for="cTexto">Color de Texto</label>
            <input type="color" id="cTexto" name="cTexto" v-model="cTexto">
          </div>
          <div class="d-flex gap-2 flex-row align-items-center py-3">
            <label class="text-light " for="mostrarTexto">Mostrar Texto</label>
            <input class="px-3" type="checkbox" id="mostrarTexto" name="mostrarTexto" v-model="mostrarTexto">
          </div>
          <div class="d-flex flex-column py-3">
            <label class="text-light py-1" for="rangeBorde">Borde</label>
            <input type="range" id="rangeBorde" name="rangeBorde" min="0" max="50" step="1" v-model="rangeBorde">
          </div>
          <div class="d-flex flex-column py-3">
            <label class="text-light py-1" for="contenidoTexto">Contenido Textual</label>
            <textarea id="contenidoTexto" name="contenidoTexto" placeholder="Escribe el texto"
              v-model="contenidoTexto">Awe</textarea>
          </div>
          <div class="d-flex flex-column py-3">
            <label class="text-light py-1" for="tipoTipografia">Tipografía</label>
            <select name="tipoTipografia" id="tipoTipografia" v-model="tipoTipografia">
              <option v-for="(tipografia, index) in tipografias" :key="index" :value="tipografia.font">{{
                tipografia.name
              }}</option>
            </select>
          </div>
          <div class="d-flex gap-2 flex-row align-items-center py-3">
            <label class="text-light " for="opacity">Opaco</label>
            <input class="px-3" type="checkbox" id="opacity" name="opacity" v-model="opacity">
          </div>
          <div class="py-3">
            <label class="text-light py-1" for="">Tamaño de Letra</label>
            <br>            
            <div class="text-light d-flex gap-2">
              <input type="radio" value="Pequeño" v-model="tamañoLetra">Pequeño
            <input type="radio" value="Mediano" v-model="tamañoLetra">Mediano
            <input type="radio" value="Grande" v-model="tamañoLetra">Grande
            </div>            
          </div>
        </div>
        <div class="col-8 d-flex justify-content-center align-items-center">
          <div :class="{ cuadro: true }" :style="{
            backgroundColor: colorBox(),
            borderRadius: rangeBorde + '%',
          }">
            <div class="text-center" v-show="mostrarTexto">
              <p v-if="tamañoLetra == 'Pequeño'"
          :style="{fontFamily: tipoTipografia, fontSize:'1.5em', color: cTexto, opacity:1 }">{{ contenidoTexto }}</p>
          <p v-else-if="tamañoLetra == 'Mediano'"
          :style="{fontFamily: tipoTipografia, fontSize:'2.5em', color: cTexto }">{{ contenidoTexto }}</p>
          <p v-else
          :style="{fontFamily: tipoTipografia, fontSize:'3.5em', color: cTexto }">{{ contenidoTexto }}</p>
            </div>
          </div>

        </div>
      </div>
    </section>
  </div>
</template>

<script>


export default {
   name: 'App',
   data() {
     return {
       cFondo: '',
       cTexto: '',
       mostrarTexto: false,
       rangeBorde: '',
       contenidoTexto: '',
       opacity: false,
       tipoTipografia: '',
       tamañoLetra: false,
       tipografias: [
         { name: 'Open Sans', font: '"Open Sans", sans-serif' },
         { name: 'Yellowtail', font: '"Yellowtail", cursive' },
         { name: 'Young Serif', font: '"Young Serif", serif' },
         { name: 'Over the Rainbow', font: '"Over the Rainbow", cursive' }
       ]
     };
   },
   methods: {
     colorBox: function () {
       let red = parseInt(this.cFondo.slice(1, 3), 16)
       let green = parseInt(this.cFondo.slice(3, 5), 16)
       let blue = parseInt(this.cFondo.slice(5, 7), 16)
       let transparencia = 0.7
       if (this.opacity) {
         transparencia = 1
       }
       return `rgba(${red},${green},${blue},${transparencia})`
     }
   }
 }
 </script>
  
  <style>
  .inputs {
    background-color: rgb(57, 112, 112);
  }
  
  .cuadro {
    width: 450px;
    height: 450px;
  }
  h1{
    font-size: 50px;
    font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
    font-weight: 800;
    color: rgb(57, 112, 112);
  }
  </style>
  