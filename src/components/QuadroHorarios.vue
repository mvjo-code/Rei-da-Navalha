<script setup>
defineProps({
  titulo: { type: String, default: 'Horário de funcionamento' },
  horarios: { type: Array, required: true },
})
</script>

<template>
  <div class="quadro">
    <header class="quadro-topo">
      <h3 class="quadro-titulo">{{ titulo }}</h3>

      <div class="quadro-logo">
        <!-- coloque aqui a logo -->
        <!-- <img src="../assets/logo-mini.png" alt="" /> -->
      </div>
    </header>

    <ul class="quadro-grade">
      <li v-for="item in horarios" :key="item.dia" class="quadro-linha">
        <span class="quadro-dia">{{ item.dia }}</span>
        <span class="quadro-horas">{{ item.horas }}</span>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.quadro {
  display: flex;
  width: 46.25rem;
  max-width: 100%;
  min-height: 30.125rem;
  padding: 1.5rem;
  flex-direction: column;
  align-items: flex-start;
  gap: 0.8125rem;
  box-sizing: border-box;
  border-radius: 1.5rem;
  border: 2px solid rgba(249, 249, 249, 0.43);
  background: rgba(0, 0, 0, 0.6);
}

.quadro-topo {
  display: flex;
  padding: 0 1rem;
  justify-content: space-between;
  align-items: center;
  align-self: stretch;
}

.quadro-titulo {
  margin: 0;
  padding: 0.5rem 0.875rem;
  border-radius: 999px;
  background: rgba(212, 91, 14, 0.85);
  color: #fff;
  font-family: 'Bebas Neue', sans-serif;
  font-size: 2rem;
  font-weight: 400;
  line-height: normal;
  text-transform: uppercase;
}

.quadro-logo {
  width: 3.6556rem;
  height: 3.6319rem;
  flex-shrink: 0;
}

.quadro-logo img {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.quadro-grade {
  display: flex;
  flex: 1;                         /* ocupa a altura que sobra */
  margin: 0;
  padding: 0;
  list-style: none;
  flex-direction: column;
  justify-content: space-between;  /* distribui as linhas igualmente */
  gap: 1.125rem;
  align-self: stretch;
}

.quadro-linha {
  display: flex;
  padding: 0.3rem 0.5rem 0.3rem 1rem;
  justify-content: space-between;
  align-items: center;
  box-sizing: border-box;
  border-radius: 1rem;
  border: 1px solid #d45b0e;
  background: #1a1a1a;
  transition:
    border-color 0.3s ease,
    background-color 0.3s ease;
}

.quadro-linha:hover {
  border-color: #f3640b;
  background: #232323;
}

.quadro-dia {
  color: #fff;
  font-family: 'Bebas Neue', sans-serif;
  font-size: 1.375rem;
  font-weight: 400;
  line-height: normal;
  text-transform: uppercase;
}

.quadro-horas {
  padding: 0.1875rem 0.75rem;
  border-radius: 999px;
  background: rgba(212, 91, 14, 0.79);
  color: #fff;
  font-family: 'Bebas Neue', sans-serif;
  font-size: 1.125rem;
  font-weight: 400;
  line-height: normal;
  text-transform: uppercase;
}

@media (max-width: 1024px) {
  .quadro {
    width: 100%;
    min-height: 0;
  }

  .quadro-topo {
    flex-wrap: wrap;
    gap: 0.75rem;
  }

  .quadro-titulo {
    font-size: clamp(1.25rem, 5vw, 2rem);
  }
}
</style>