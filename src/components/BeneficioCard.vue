<script setup>
defineProps({
  titulo: { type: String, required: true },
  texto: { type: String, required: true },
})
</script>

<template>
  <article class="beneficio-card">
    <div class="beneficio-topo">
      <span class="beneficio-linha"></span>
      <!-- coloque aqui a logo -->
      <!-- <img class="beneficio-logo" src="@/assets/logo-mini.png" alt="" /> -->
       <img class="beneficio-logo" src="../assets/Logotipo.png" alt="">
      <span class="beneficio-linha"></span>
    </div>

    <div class="beneficio-textos">
      <h3 class="beneficio-titulo">{{ titulo }}</h3>
      <p class="beneficio-texto">{{ texto }}</p>
    </div>
  </article>
</template>

<style scoped>
.beneficio-card {
  position: relative;   /* referência para o feixe */
  overflow: hidden;     /* corta o feixe nas bordas arredondadas */
  display: flex;
  width: 26.5rem;
  height: 11rem;
  padding: 1.25rem;
  flex-direction: column;
  align-items: flex-start;
  gap: 1rem;
  box-sizing: border-box;
  border-radius: 1rem;
  border: 1px solid rgba(255, 255, 255, 0.1);
  background: rgba(0, 0, 0, 0.3);
  -webkit-backdrop-filter: blur(0px);
  backdrop-filter: blur(0px); /* começa em 0 para o hover poder animar até 10px */
  transition:
    backdrop-filter 0.5s ease,
    -webkit-backdrop-filter 0.5s ease,
    background-color 0.5s ease,
    border-color 0.5s ease,
    transform 0.5s cubic-bezier(0.22, 1, 0.36, 1),
    box-shadow 0.5s ease;
}

/* ---------- hover: fundo ofuscado ---------- */
.beneficio-card:hover {
  -webkit-backdrop-filter: blur(10px);
  backdrop-filter: blur(10px);
  background: rgba(0, 0, 0, 0.45);
  border-color: rgba(213, 91, 14, 0.45);
  transform: translateY(-4px);
  box-shadow: 0 16px 32px -12px rgba(0, 0, 0, 0.6);
  cursor: pointer;
}

.beneficio-card:active {
  transform: translateY(0);
  box-shadow: 0 10px 30px -12px rgba(0, 0, 0, 0.5);
}

/* ---------- feixe de luz periódico ---------- */
.beneficio-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 40%;
  height: 100%;
  background: linear-gradient(
    120deg,
    transparent 0%,
    rgba(255, 255, 255, 0.12) 50%,
    transparent 100%
  );
  transform: translateX(-150%) skewX(-20deg);
  pointer-events: none;
  animation: feixe-periodico 8s ease-in-out infinite;
}

/* cada card começa um pouco depois do anterior: o feixe "viaja" entre eles */
.beneficio-card:nth-child(2)::before {
  animation-delay: 0.5s;
}
.beneficio-card:nth-child(3)::before {
  animation-delay: 1s;
}

@keyframes feixe-periodico {
  0% {
    transform: translateX(-150%) skewX(-20deg);
  }
  25% {
    transform: translateX(300%) skewX(-20deg); /* atravessa o card */
  }
  100% {
    transform: translateX(300%) skewX(-20deg); /* fica parado fora do card até repetir */
  }
}

.beneficio-topo {
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.beneficio-linha {
  width: 3rem;
  height: 2px;
  background: #d55b0e;
}

.beneficio-logo {
  width: 3rem;
  height: 2.8125rem;
  object-fit: cover;
}

.beneficio-textos {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 0.5rem;
  align-self: stretch;
}

.beneficio-titulo {
  margin: 0;
  align-self: stretch;
  color: rgba(255, 255, 255, 0.85);
  font-family: 'Bebas Neue', sans-serif;
  font-size: 1.75rem;
  font-style: normal;
  font-weight: 400;
  line-height: normal;
  letter-spacing: 0.1575rem;
  text-transform: uppercase;
}

.beneficio-texto {
  margin: 0;
  color: rgba(255, 255, 255, 0.67);
  font-family: 'Bebas Neue', sans-serif;
  font-size: 1rem;
  font-style: normal;
  font-weight: 400;
  line-height: 140%;
  letter-spacing: 0.03rem;
  text-transform: uppercase;
}

@media (prefers-reduced-motion: reduce) {
  .beneficio-card::before {
    animation: none;
  }
  .beneficio-card:hover {
    transform: none;
  }
}

@media (max-width: 1024px) {
  .beneficio-card {
    width: 100%;
    height: auto;         /* a altura fixa de 11rem não comporta o texto em 2 linhas */
  }
}

@media (max-width: 640px) {
  .beneficio-topo {
    align-self: center;   /* linhas e logo centralizadas, como no design */
  }

  .beneficio-linha {
    width: 3.4rem;
  }

  .beneficio-titulo {
    font-size: 1.5rem;
    letter-spacing: 0.075rem;
  }
}

</style>