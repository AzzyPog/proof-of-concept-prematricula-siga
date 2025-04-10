<template>
  <q-header class="bg-gradient q-pa-sm flex items-center justify-evenly">
    <div class="flex items-center">
      <q-img
        src="../assets/ufrj-horizontal-negativa-telas 2.png"
        alt="Logo UFRJ"
        width="10em"
        class="minerva-img q-mr-sm"
      />
    </div>
    <div class="main-title text-white text-weight-bold">PORTAL DE ACESSO</div>

    <div class="flex items-center">
      <div class="text-white text-right q-mr-sm">
        <div class="text-subtitle1 text-weight-bold">Carlos Martins</div>
        <div class="text-caption cursor-pointer">Sair do sistema</div>
      </div>
      <q-avatar size="40px" color="grey" text-color="primary" class="user-icon">
        <q-icon name="person" color="white" size="30px" class="icon-img cursor-pointer" />
      </q-avatar>
    </div>
  </q-header>
</template>

<script setup></script>

<style scoped>
.bg-gradient {
  background: linear-gradient(to right, #026364, #0bab8b);
}

.icon-img {
  padding-right: 2px;
}

.user-icon {
  border: 1px solid #24ff24;
}

.main-title {
  font-size: 2rem;
}

.minerva-img {
  border-right: 1px solid #ffff;
}
</style>
