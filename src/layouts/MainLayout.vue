<template>
  <q-layout view="hHh lpR fFf">

    <q-header elevated class="bg-cyan-8">
      <q-toolbar>
        <q-toolbar-title>
          <q-avatar>
            <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg">
          </q-avatar>
          prueba
        </q-toolbar-title>

        <q-btn dense flat round icon="menu" @click="drawer = !drawer" />
      </q-toolbar>
    </q-header>

    <q-drawer 
    v-model="drawer"
    show-if-above
    :width="200"
    :breakpoint="400"
    >
    <q-scroll-area style="height: calc(100% - 150px); margin-top: 150px; border-right: 1px solid #ddd">
          <q-list padding>
            <q-item clickable v-ripple to="/" active-class="my-menu-link" exact>
              <q-item-section avatar>
                <q-icon name="inbox" />
              </q-item-section>

              <q-item-section>
                Inicio
              </q-item-section>
            </q-item>

            <q-item  clickable v-ripple to="/about" active-class="my-menu-link">
              <q-item-section avatar>
                <q-icon name="star" />
              </q-item-section>

              <q-item-section>
               About
              </q-item-section>
            </q-item>

            <q-item  clickable v-ripple to="/form" active-class="my-menu-link">
              <q-item-section avatar>
                <q-icon name="form" />
              </q-item-section>

              <q-item-section>
               Formulario
              </q-item-section>
            </q-item>
        

       
          </q-list>
        </q-scroll-area>

        <q-img class="absolute-top" src="https://cdn.quasar.dev/img/material.png" style="height: 150px">
          <div class="absolute-bottom bg-transparent">
            <q-avatar size="56px" class="q-mb-sm">
              <img src="https://cdn.quasar.dev/img/boy-avatar.png">
            </q-avatar>
            <div class="text-weight-bold">Razvan Stoenescu</div>
            <div>@rstoenescu</div>
          </div>
        </q-img>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>

    <q-footer elevated class="bg-grey-8 text-white">
      <q-toolbar>
        <q-toolbar-title>
          <q-avatar>
            <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg">
          </q-avatar>
          <div>Title</div>
        </q-toolbar-title>
      </q-toolbar>
    </q-footer>

  </q-layout>
</template>

<script>
import { ref } from 'vue'
  const drawer = ref(false)
export default {
  setup () {
    return {
      drawer
    }
  }
}
</script>

<style lang="scss">
.my-menu-link{
  color: white;
  background-color: rgb(190, 73, 31);
}

</style>