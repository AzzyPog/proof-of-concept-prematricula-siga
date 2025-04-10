<template>
  <q-page class="flex flex-center">
    <div class="main-container q-pa-lg bg-white" style="max-width: 1000px; width: 100%">
      <div class="processo-titulo text-center q-mb-md">Selecione o curso que deseja…</div>

      <div class="row q-col-gutter-md q-mb-md justify-center">
        <q-card
          v-for="curso in cursos"
          :key="curso.nome"
          class="curso-card col-12 col-md-5 cursor-pointer"
          :class="{ 'border-selected': curso.nome === cursoSelecionado }"
          flat
          bordered
          @click="cursoSelecionado = curso.nome"
        >
          <q-card-section>
            <div class="curso-titulo">{{ curso.nome }}</div>
            <div class="curso-info">
              <span class="text-weight-bold">Semestre:</span> {{ curso.semestre }}
            </div>
            <div class="curso-info">
              <span class="text-weight-bold">Turno: </span>{{ curso.turno }}
            </div>
            <div class="curso-info">
              <span class="text-weight-bold">Método: </span>{{ curso.metodo }}
            </div>
            <div class="curso-info">
              <span class="text-weight-bold">Pólo: </span>{{ curso.polo }}
            </div>
            <div class="curso-info">
              <span class="text-weight-bold">Modalidade:</span> {{ curso.modalidade }}
            </div>
            <div class="status q-mt-sm text-positive">
              <span class="curso-info text-weight-bold">Status:</span> {{ curso.status }}
            </div>
          </q-card-section>
        </q-card>
      </div>

      <div class="q-mb-sm text-center">
        <q-btn color="confirm" size="1rem" label="Confirmar" />
      </div>

      <div class="text-caption text-center text-grey">
        [A cada etapa completa, seu progresso será salvo]
      </div>
    </div>

    <RoadMapFlutuante />
  </q-page>
</template>

<script setup>
import RoadMapFlutuante from 'src/components/roadMapFlutuante.vue'
import { ref } from 'vue'

const cursos = [
  {
    nome: 'Música',
    semestre: '1º',
    turno: 'Integral',
    metodo: 'THE/ENEM',
    polo: 'Escola de Música',
    modalidade: 'Ampla concorrência',
    status: 'Aguardando pré-matrícula',
    selecionado: false,
  },
  {
    nome: 'Paisagismo',
    semestre: '1º',
    turno: 'Integral',
    metodo: 'SISU/ENEM',
    polo: 'Escola de Belas Artes',
    modalidade: 'Ampla concorrência',
    status: 'Aguardando pré-matrícula',
    selecionado: true,
  },
]

const cursoSelecionado = ref(null)
</script>

<style scoped>
.border-selected {
  border: 2px solid #19856e;
}

.processo-titulo {
  color: #156c59;
  font-weight: bold;
  font-size: 1.7rem;
}

.text-confirm {
  color: #41ae75 !important;
}
.bg-confirm {
  background: #41ae75 !important;
}

.status {
  font-weight: bold;
}

.curso-info {
  color: #4a5a6a;
  font-size: 0.9rem;
  padding-bottom: 10px;
}

.curso-titulo {
  font-size: 1.6rem;
  padding-bottom: 15px;
  font-weight: bold;
  color: #4a5a6a;
}

.main-container {
  margin-top: 3rem;
  margin-bottom: 3rem;
  box-shadow: 2px 2px 10px 2px rgb(216, 216, 216);
  border-radius: 12px;
}

.curso-card {
  margin: 2rem;
}

.floating-btn {
  position: fixed;
  bottom: 20px;
  right: 20px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);
  z-index: 1000;
}
</style>
