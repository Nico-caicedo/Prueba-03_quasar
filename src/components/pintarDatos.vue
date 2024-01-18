<template>
  
        <div class="q-pa-md">
    <q-table 
    title="Productos"
    class="q-mt-md"
    no-data-label="Sin productos para mostrar"
    :columns="columns"
    :rows= "productos"
    />
  </div>

</template>
<script>

const columns = [
  {
    name:'producto',
    label: 'Producto',
    align: 'Left',
    field: 'producto',
    sortable: true
  },
  {
    name:'prioridad',
    label: 'Prioridad',
    align: 'Left',
    field: 'prioridad',
    sortable: true
  }

]

const rows =  [
    {
        producto: 'producto 1',
        prioridad: 'Maxima'
    },

    {
        producto: 'producto 2',
        prioridad: 'Baja'
    }
]

export default{
    props:{
        productos: Array
    },
    setup(){
        return{
            columns,
            rows
        }
    }
}

</script>