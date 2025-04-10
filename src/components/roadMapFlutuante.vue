<template>
  <div>
    <q-btn
      round
      :icon="mostrar ? 'close' : 'timeline'"
      color="white"
      text-color="black"
      class="floating-btn"
      @click="mostrar = !mostrar"
    />

    <transition name="fade">
      <div v-if="mostrar" class="popup-container">
        <q-card class="popup-card">
          <q-card-section class="q-pa-md">
            <div v-for="(etapa, index) in etapas" :key="index" class="etapa-item">
              <div class="linha-conector" v-if="index !== 0"></div>

              <div
                class="etapa-icon"
                :class="{
                  'etapa-completa': etapa.status === 'Completo',
                  'etapa-disponivel': etapa.status === 'Disponível',
                  'etapa-bloqueada': etapa.status === 'Bloqueado',
                }"
              >
                <q-icon :name="etapa.icone" size="18px" />
              </div>

              <div class="etapa-text">
                <div class="text-subtitle2">Etapa {{ index + 1 }}</div>
                <div
                  :class="{
                    'text-grey-8': etapa.status === 'Disponível',
                    'text-weight-bold text-green': etapa.status !== 'Bloqueado',
                    'text-grey': etapa.status === 'Bloqueado',
                  }"
                >
                  {{ etapa.nome }}
                </div>
                <div class="text-caption text-grey-7">{{ etapa.status }}</div>
              </div>
            </div>
          </q-card-section>
        </q-card>
      </div>
    </transition>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const mostrar = ref(false)

const etapas = [
  { nome: 'Escolha de curso', status: 'Completo', icone: 'edit' },
  { nome: 'Dados pessoais', status: 'Completo', icone: 'badge' },
  { nome: 'Questionário', status: 'Disponível', icone: 'quiz' },
  { nome: 'Documentos', status: 'Bloqueado', icone: 'folder_off' },
]
</script>

<style scoped>
.floating-btn {
  position: fixed;
  bottom: 20px;
  right: 20px;
  z-index: 999;
}

.popup-container {
  position: fixed;
  bottom: 80px;
  right: 20px;
  z-index: 998;
}

.popup-card {
  width: 250px;
  box-shadow: 0px 4px 12px rgba(0, 0, 0, 0.2);
  border-radius: 12px;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.2s;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.etapa-item {
  display: flex;
  align-items: flex-start;
  position: relative;
  padding-left: 45px;
  margin-bottom: 16px;
}

.etapa-icon {
  position: absolute;
  left: 0;
  bottom: 15px;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background: #ccc;
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
}

.etapa-completa {
  background-color: #21ba45;
}

.etapa-disponivel {
  background-color: #ffffff;
  border: 1px solid #6b6b6b;
  color: #6b6b6b;
}

.etapa-bloqueada {
  background-color: #e0e0e0;
  color: #888;
}

.linha-conector {
  position: absolute;
  left: 18px;
  top: -31px;
  width: 2px;
  height: 40px;
  background: #ccc;
}

.etapa-text {
  margin-left: 8px;
}
</style>
