<script setup>
defineProps({
  titulo: { type: String, required: true },
  descricao: { type: String, required: true },
  imagem: { type: String, default: '' },
})
</script>

<template>
  <article class="servico-card">
    <div class="servico-imagem">
      <img v-if="imagem" :src="imagem" :alt="titulo" />
    </div>

    <div class="servico-direita">
      <div class="servico-textos">
        <h3 class="servico-titulo">{{ titulo }}</h3>
        <p class="servico-descricao">{{ descricao }}</p>
      </div>

      <div class="servico-logo">
        <!-- coloque aqui a logo -->
        <!-- <img src="../assets/logo-mini.png" alt="" /> -->
         <img src=  "../assets/Logotipo.png" alt="Logo">
      </div>
    </div>
  </article>
</template>

<style scoped>
.servico-card {
  display: flex;
  width: 21.375rem;
  padding: 0.75rem;
  align-items: flex-start;
  gap: 0.96rem;
  box-sizing: border-box;
  border: 1px solid rgba(255, 255, 255, 0.1);
  background: rgba(0, 0, 0, 0.7);
  box-shadow: 0 10px 24px -8px rgba(0, 0, 0, 0.4);
}

.servico-imagem {
  width: 8.548rem;
  height: 10.376rem;
  flex-shrink: 0;
  overflow: hidden;
  border-radius: 0.163rem;
  border: 1px solid #c6ae24;
  background: lightgray;
}

.servico-imagem img {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.servico-direita {
  display: flex;
  flex: 1;
  min-width: 0;
  height: 10.376rem;
  align-items: flex-end;
  gap: 0.96rem;
}

.servico-textos {
  display: flex;
  flex: 1;
  min-width: 0;
  height: 100%;
  padding: 0.65rem 0;
  box-sizing: border-box;
  flex-direction: column;
  justify-content: space-between;
  align-items: flex-start;
}

.servico-titulo {
  margin: 0;
  color: #f57d30;
  font-family: 'Bebas Neue', sans-serif;
  font-size: 1.982rem;
  font-weight: 400;
  line-height: normal;
  text-transform: uppercase;
}

.servico-descricao {
  margin: 0;
  color: rgba(255, 255, 255, 0.67);
  font-family: 'Bebas Neue', sans-serif;
  font-size: 1.115rem;
  font-weight: 400;
  line-height: normal;
  letter-spacing: 0.033rem;
  text-transform: uppercase;
}

.servico-logo {
  width: 3.655rem;
  height: 3.438rem;
  flex-shrink: 0;
}

.servico-logo img {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
}
</style>