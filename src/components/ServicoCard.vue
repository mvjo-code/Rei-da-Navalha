<script setup>
defineProps({
  titulo: { type: String, required: true },
  descricao: { type: String, required: true },
  imagem: { type: String, default: '' },
  preco: { type: String, default: '' },
  duracao: { type: String, default: '' },
})
</script>

<template>
  <article class="servico-card">
    <div class="servico-imagem">
      <img v-if="imagem" :src="imagem" :alt="titulo" />
    </div>

    <div class="servico-info">
      <div class="servico-textos">
        <h3 class="servico-titulo">{{ titulo }}</h3>
        <p class="servico-descricao">{{ descricao }}</p>
      </div>

      <div v-if="preco || duracao" class="servico-meta">
        <span v-if="preco" class="servico-preco">{{ preco }}</span>
        <span v-if="preco && duracao" class="servico-separador">·</span>
        <span v-if="duracao" class="servico-duracao">{{ duracao }}</span>
      </div>
    </div>
  </article>
</template>

<style scoped>
.servico-card {
  display: flex;
  width: min(38rem, calc(100vw - 2 * var(--margem-lateral)));
  padding: 1rem;
  align-items: stretch;
  gap: 1.5rem;
  box-sizing: border-box;
  border-radius: 0.75rem;
  border: 1px solid rgba(255, 255, 255, 0.12);
  background: rgba(0, 0, 0, 0.7);
  box-shadow: 0 16px 32px -12px rgba(0, 0, 0, 0.6);
}

.servico-imagem {
  width: 15rem;
  height: 19rem;
  flex-shrink: 0;
  overflow: hidden;
  border-radius: 0.25rem;
  border: 1px solid #c6ae24;
  background: #2a2a2a;
}

.servico-imagem img {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.servico-info {
  display: flex;
  flex: 1;
  min-width: 0;
  padding: 0.5rem 0;
  flex-direction: column;
  justify-content: space-between;
}

.servico-textos {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

.servico-titulo {
  margin: 0;
  color: #f57d30;
  font-family: 'Bebas Neue', sans-serif;
  font-size: 3rem;
  font-weight: 400;
  line-height: 1;
  text-transform: uppercase;
}

.servico-descricao {
  margin: 0;
  color: rgba(255, 255, 255, 0.7);
  font-family: 'Bebas Neue', sans-serif;
  font-size: 1.375rem;
  font-weight: 400;
  line-height: 1.25;
  letter-spacing: 0.04rem;
  text-transform: uppercase;
}

.servico-meta {
  display: flex;
  padding-top: 1rem;
  align-items: baseline;
  gap: 0.75rem;
  border-top: 1px solid rgba(212, 91, 14, 0.4);
}

.servico-preco {
  color: #fff;
  font-family: 'Bebas Neue', sans-serif;
  font-size: 2.5rem;
  font-weight: 400;
  line-height: 1;
}

.servico-separador {
  color: #d55b0e;
  font-family: 'Bebas Neue', sans-serif;
  font-size: 1.75rem;
}

.servico-duracao {
  color: rgba(255, 255, 255, 0.67);
  font-family: 'Bebas Neue', sans-serif;
  font-size: 1.5rem;
  font-weight: 400;
  text-transform: uppercase;
}

@media (max-width: 1024px) {
  .servico-card {
    flex-direction: column;
    gap: 1rem;
  }

  .servico-imagem {
    width: 100%;
    height: 11rem;
  }

  .servico-titulo {
    font-size: 2.25rem;
  }

  .servico-descricao {
    font-size: 1.125rem;
  }

  .servico-preco {
    font-size: 2rem;
  }
}
</style>