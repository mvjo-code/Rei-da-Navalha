<script setup>
defineProps({
  precoAntigo: { type: String, default: 'De R$ 25,00' },
  prefixo: { type: String, default: 'Por' },
  preco: { type: String, default: 'R$ 15,00' },
  descricao: { type: String, default: 'No corte americano' },
  textoBotao: { type: String, default: 'Aproveitar oferta' },
  rodape: { type: String, default: 'Apenas este mês.' },
  href: { type: String, default: '#contato' },
})
</script>

<template>
  <aside class="oferta">
    <div class="oferta-topo">
      <span class="oferta-linha"></span>
      <!-- coloque aqui a logo -->
      <!-- <img class="oferta-logo" src="../assets/logo-mini.png" alt="" /> -->
       <img src="../assets/Logotipo.png" alt="logo" class="oferta-logo">
      <span class="oferta-linha"></span>
    </div>

    <div class="oferta-conteudo">
      <div class="oferta-valores">
        <p class="oferta-antigo">{{ precoAntigo }}</p>
        <p class="oferta-prefixo">{{ prefixo }}</p>
        <p class="oferta-preco">{{ preco }}</p>
        <p class="oferta-descricao">{{ descricao }}</p>
      </div>

      <span class="oferta-divisor"></span>

      <a class="oferta-botao" :href="href">{{ textoBotao }}</a>
    </div>

    <p class="oferta-rodape">{{ rodape }}</p>
  </aside>
</template>

<style scoped>
.oferta {
  position: relative;
  isolation: isolate; /* "andar" próprio para a camada de luz interna */
  display: flex;
  width: 100%;
  max-width: 22rem;
  padding: 1.25rem 1.0625rem;
  flex-direction: column;
  align-items: center;
  gap: 1.0625rem;
  box-sizing: border-box;
  border-radius: 0.625rem;
  border: 1px solid #fff;
  background: rgba(0, 0, 0, 0.5);
  box-shadow: 0 10px 30px -12px rgba(0, 0, 0, 0.5); /* sombra de repouso, discreta */
  will-change: transform;
  transition:
    transform 0.5s cubic-bezier(0.22, 1, 0.36, 1),
    box-shadow 0.5s ease,
    border-color 0.5s ease,
    background-color 0.5s ease;
}

/* camada de luz laranja que aparece no topo do card */
.oferta::before {
  content: '';
  position: absolute;
  inset: 0;
  z-index: -1;
  border-radius: inherit;
  background: radial-gradient(
    120% 70% at 50% 0%,
    rgba(213, 91, 14, 0.28) 0%,
    transparent 70%
  );
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.5s ease;
}

/* área invisível embaixo do card para evitar o flicker do hover */
.oferta::after {
  content: '';
  position: absolute;
  left: 0;
  right: 0;
  bottom: -10px;
  height: 10px;
}

.oferta:hover,
.oferta:focus-within {
  transform: translateY(-6px);
  border-color: #d55b0e;
  background: rgba(0, 0, 0, 0.6);
  box-shadow:
    0 24px 40px -12px rgba(0, 0, 0, 0.6),
    0 12px 40px -8px rgba(213, 91, 14, 0.35),
    0 0 0 1px rgba(213, 91, 14, 0.25);
}

.oferta:hover::before,
.oferta:focus-within::before {
  opacity: 1;
}

/* ---------- elementos internos reagem ao hover do card ---------- */

.oferta-linha,
.oferta-divisor {
  transition: transform 0.6s cubic-bezier(0.22, 1, 0.36, 1);
}

.oferta-divisor {
  transform-origin: center;
}

.oferta:hover .oferta-divisor {
  transform: scaleX(1.06);
}

.oferta:hover .oferta-prefixo,
.oferta:hover .oferta-preco {
  color: #fff;
  text-shadow: 0 0 24px rgba(213, 91, 14, 0.45);
}

.oferta:hover .oferta-botao {
  background: #b5520f; /* o botão "acende" junto com o card */
}

/* ---------- estrutura ---------- */

.oferta-topo {
  display: flex;
  align-items: center;
  gap: 1px;
}

.oferta-linha {
  width: 5.0625rem;
  height: 2px;
  background: #d55b0e;
}

.oferta-logo {
  width: 3.655rem;
  height: 3.438rem;
  object-fit: cover;
}

.oferta-conteudo {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1.0625rem;
  align-self: stretch;
}

.oferta-valores {
  display: flex;
  flex-direction: column;
  align-items: center;
  align-self: stretch;
}

.oferta-valores p {
  margin: 0;
  font-family: 'Bebas Neue', sans-serif;
  font-weight: 400;
  text-align: center;
  text-transform: uppercase;
}

.oferta-antigo {
  color: #d23b3b;
  font-size: 1.5rem;
  text-decoration: line-through;
}

.oferta-prefixo,
.oferta-preco {
  color: #dbdbdb;
  font-size: 4.5rem;
  line-height: 0.95;
  transition:
    text-shadow 0.5s ease,
    color 0.5s ease;
}

.oferta-descricao {
  color: rgba(255, 255, 255, 0.81);
  font-size: 1.5rem;
}

.oferta-divisor {
  width: 100%;
  height: 2px;
  background: #c7692f;
}

/* ---------- botão ---------- */

.oferta-botao {
  position: relative;
  overflow: hidden;
  display: flex;
  width: 90%;
  height: 3.1rem;
  justify-content: center;
  align-items: center;
  box-sizing: border-box;
  border-radius: 0.4727rem;
  border: 0.54px solid #fff;
  background: #9c450e;
  color: #fdf5f5;
  font-family: 'Bebas Neue', sans-serif;
  font-size: 1.0804rem;
  font-weight: 400;
  letter-spacing: 0.15rem;
  text-transform: uppercase;
  text-decoration: none;
  white-space: nowrap;
  transition: all 0.2s cubic-bezier(0.22, 0.01, 0.36, 1);
}

.oferta-botao:hover {
  transform: scale(1.05);
}

.oferta-botao:active {
  transform: scale(1.02);
}

/* feixe de luz (começa fora do botão, à esquerda) */
.oferta-botao::before {
  content: '';
  position: absolute;
  top: 0;
  left: -75%;
  width: 50%;
  height: 100%;
  background: linear-gradient(
    120deg,
    transparent 0%,
    rgba(255, 255, 255, 0.3) 50%,
    transparent 100%
  );
  transform: skewX(-20deg);
  pointer-events: none;
}

.oferta-botao:hover::before {
  animation: feixe 0.4s ease-in-out;
}

@keyframes feixe {
  from { left: -75%; }
  to { left: 125%; }
}

.oferta-rodape {
  margin: auto 0 0;
  color: rgba(255, 255, 255, 0.85);
  font-family: 'Bebas Neue', sans-serif;
  font-size: 1.375rem;
  font-weight: 400;
  text-align: center;
  text-transform: uppercase;
}

@media (max-width: 1024px) {
  .oferta {
    max-width: 26rem;
  }
}

/* respeita quem desativa animações no sistema */
@media (prefers-reduced-motion: reduce) {
  .oferta,
  .oferta::before,
  .oferta-linha,
  .oferta-divisor,
  .oferta-prefixo,
  .oferta-preco,
  .oferta-botao {
    transition: none;
  }
  .oferta:hover,
  .oferta:focus-within,
  .oferta-botao:hover,
  .oferta-botao:active {
    transform: none;
  }
  .oferta-botao:hover::before {
    animation: none;
  }
}
</style>