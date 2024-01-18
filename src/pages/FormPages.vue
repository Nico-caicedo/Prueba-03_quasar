<template>
  <q-page padding>
    <h4>Agregar Producto</h4>
    <!-- <pre>{{producto}}</pre> -->
        
    <q-form class="row q-col-gutter-md"
    @submit.prevent="procesarFormulario"
    @reset="reset"
    ref="myform"
    >
      <div class="col-12 col-sm-6">
        <q-input label="Producto"  v-model="producto"
        lazy-rules
        :rules="[ val => val && val.length > 0 || 'Escriba un producto']"/>
      </div>
   

      <div class="col-12 col-sm-6">
        <q-select label="Prioridad" :options="opciones"  v-model="seleccion" 
        lazy-rules
        :rules="[ val => val && val.length > 0 || 'seleccione algo']"/>
      </div>
      <div class="col-12">
        <q-toggle
        v-model="aceptar"
        label="Aceptar los terminos"
        />
      </div>
      <div class="col-12">
        <q-btn 
        color="black"
        text-color="white" 
        label="Submit" 
        type="submit"
         />

        <q-btn
          text-color="blue"
          label="reset"
          outline
          rounded
          class="q-ma-lg"
          :ripple="false"
          type="reset"
        />
      </div>

    </q-form>
    <PintarDatos :productos="productos"/>
  </q-page>
</template>
<script>
import{ref} from 'vue'
import { useQuasar } from 'quasar'
import PintarDatos from 'src/components/pintarDatos.vue'
export default{
    setup() {
        const $q = useQuasar();
        const producto = ref(null);
        const myform = ref(null);
        const seleccion = ref(null);
        const aceptar = ref(false);
        const productos = ref([]);
        const opciones = [
            'Maxima',
            'Minima',
            'Ninguna'
        ];
        const procesarFormulario = () => {
            console.log('me diste click');
            if (aceptar.value === false) {
                $q.notify({
                    color: 'red-5',
                    textColor: 'white',
                    icon: 'warning',
                    message: 'Acepta los terminos primero'
                });
            }
            else {
                $q.notify({
                    color: 'green-4',
                    textColor: 'white',
                    icon: 'cloud_done',
                    message: 'Submitted'
                });
             
                productos.value = [...productos.value,{
                    producto: producto.value,
                    prioridad: seleccion.value
                }]
                myform.value.reset();
            }
        };
        const reset = () => {
            producto.value = null;
            seleccion.value = null;
            aceptar.value = false;
        };
        return {
            producto,
            seleccion,
            opciones,
            procesarFormulario,
            aceptar,
            reset,
            myform,
            productos
        };
    },
    components: { PintarDatos }
}

</script>