<script setup>
defineProps({
  texto: { type: String, default: 'Agendar' },
  href: { type: String, default: '#contato' },
})
</script>

<template>
  <a :href="href" class="btn-agendar">
    <span class="btn-agendar-icone">
      <img src="../assets/icones/Ícone de agendamento.svg" alt="" />
    </span>
    <span class="btn-agendar-texto">{{ texto }}</span>
  </a>
</template>

<style scoped>
.btn-agendar {
  position: relative;
  overflow: hidden;
  display: flex;
  width: var(--btn-agendar-largura, 16.3125rem);
  height: 4.25rem;
  flex-shrink: 0;
  box-sizing: border-box;
  border-radius: 0.8125rem;
  border: 1.5px solid #c2c2c1;
  background: #c7550d;
  text-decoration: none;
  letter-spacing: var(--btn-agendar-espaco, 0.495rem);
  transition: transform 0.35s cubic-bezier(0.22, 1, 0.36, 1);
}

.btn-agendar:hover {
  transform: scale(1.03);
}

.btn-agendar:active {
  transform: scale(0.97);
}

.btn-agendar-icone {
  display: flex;
  width: 4rem;
  justify-content: center;
  align-items: center;
  flex-shrink: 0;
  align-self: stretch;
  border-right: 1.5px solid #d45b0e;
  background: #272522;
}

.btn-agendar-texto {
  display: flex;
  justify-content: center;
  align-items: center;
  flex: 1 0 0;
  align-self: stretch;
  color: #fff;
  font-family: 'Bebas Neue', sans-serif;
  font-size: 1.75rem;
  font-weight: 400;
  line-height: 100%;
  text-transform: uppercase;
  white-space: nowrap;
}

/* feixe de luz */
.btn-agendar::before {
  content: '';
  position: absolute;
  top: 0;
  left: -75%;
  width: 50%;
  height: 100%;
  background: linear-gradient(120deg, transparent 0%, rgba(255, 255, 255, 0.3) 50%, transparent 100%);
  transform: skewX(-20deg);
  pointer-events: none;
  z-index: 1;
}

.btn-agendar:hover::before {
  animation: feixe 0.4s ease-in-out;
}

@keyframes feixe {
  from { left: -75%; }
  to { left: 125%; }
}
</style>