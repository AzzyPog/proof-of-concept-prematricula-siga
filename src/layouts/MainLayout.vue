<template>
  <q-layout view="hHh lpR fFf" style="background-color: #e7ede9">
    <!---header--->
    <ProcessoHeader />
    <!--------->
    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>

  <ProcessoFooter />
</template>

<script setup>
import ProcessoFooter from 'src/components/processoFooter.vue'
import ProcessoHeader from 'src/components/processoHeader.vue'
</script>
