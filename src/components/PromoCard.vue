<script setup>
defineProps({
  titulo: { type: String, default: 'Damos' },
  valor: { type: String, default: '20' },
  simbolo: { type: String, default: '%' },
  sufixo: { type: String, default: 'OFF' },
  descricao: { type: String, default: 'No primeiro corte' },
  textoBotao: { type: String, default: 'Aproveitar oferta' },
  href: { type: String, default: '#contato' },
})
</script>

<template>
  <aside class="promo">
    <div class="promo-topo">
      <span class="promo-linha"></span>
      <!-- coloque aqui a logo -->
      <!-- <img class="promo-logo" src="@/assets/logo-mini.png" alt="" /> -->
       <img src="../assets/Logotipo.png" alt="logo" class="promo-logo">
      <span class="promo-linha"></span>
    </div>

    <div class="promo-conteudo">
      <div class="promo-oferta">
        <p class="promo-texto">{{ titulo }}</p>

        <div class="promo-desconto">
          <span class="promo-valor">{{ valor }}</span>
          <div class="promo-lateral">
            <span class="promo-simbolo">{{ simbolo }}</span>
            <span class="promo-sufixo">{{ sufixo }}</span>
          </div>
        </div>

        <p class="promo-texto">{{ descricao }}</p>
      </div>

      <span class="promo-divisor"></span>

      <a class="promo-botao" :href="href">{{ textoBotao }}</a>
    </div>
  </aside>
</template>

<style scoped>
.promo {
  position: relative;
  isolation: isolate; /* cria um "andar" próprio para as camadas internas do card */
  display: flex;
  width: 18.1875rem;
  height: 24.875rem;
  padding: 1.25rem 1.0625rem;
  flex-direction: column;
  align-items: center;
  gap: 1.0625rem;
  flex-shrink: 0;
  box-sizing: border-box;
  border-radius: 0.625rem;
  border: 1px solid rgba(255, 255, 255, 0.85);
  background: rgba(0, 0, 0, 0.4);
  box-shadow: 0 10px 30px -12px rgba(0, 0, 0, 0.5); /* sombra de repouso, discreta */
  will-change: transform;
  transition:
    transform 0.5s cubic-bezier(0.22, 1, 0.36, 1),
    box-shadow 0.5s ease,
    border-color 0.5s ease,
    background-color 0.5s ease;
}

/* camada de luz laranja que aparece no topo do card */
.promo::before {
  content: '';
  position: absolute;
  inset: 0;
  z-index: -1; /* fica atrás do conteúdo, mas na frente do fundo */
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
.promo::after {
  content: '';
  position: absolute;
  left: 0;
  right: 0;
  bottom: -10px;
  height: 10px;
}

.promo:hover,
.promo:focus-within {
  transform: translateY(-6px);
  border-color: #d55b0e;
  background: rgba(0, 0, 0, 0.5);
  box-shadow:
    0 24px 40px -12px rgba(0, 0, 0, 0.6),      /* profundidade: sombra escura e longa */
    0 12px 40px -8px rgba(213, 91, 14, 0.35),  /* brilho laranja embaixo */
    0 0 0 1px rgba(213, 91, 14, 0.25);         /* "halo" fino em volta da borda */
}

.promo:hover::before,
.promo:focus-within::before {
  opacity: 1;
}

/* ---------- elementos internos reagem ao hover do card ---------- */

.promo-linha,
.promo-divisor {
  transition: transform 0.6s cubic-bezier(0.22, 1, 0.36, 1);
}

.promo-divisor {
  transform-origin: center;
}

.promo:hover .promo-divisor {
  transform: scaleX(1.06);
}

.promo-valor {
  transition: text-shadow 0.5s ease, color 0.5s ease;
}

.promo:hover .promo-valor {
  color: #fff;
  text-shadow: 0 0 24px rgba(213, 91, 14, 0.45);
}

.promo-botao {
  transition:
    background-color 0.4s ease,
    transform 0.4s cubic-bezier(0.22, 1, 0.36, 1);
}

.promo:hover .promo-botao {
  background: #b5520f; /* o botão "acende" junto com o card */
}

/* respeita quem desativa animações no sistema */
@media (prefers-reduced-motion: reduce) {
  .promo,
  .promo::before,
  .promo-linha,
  .promo-divisor,
  .promo-valor,
  .promo-botao {
    transition: none;
  }
  .promo:hover,
  .promo:focus-within {
    transform: none;
  }
}

.promo-topo {
  display: flex;
  align-items: center;
  gap: 1px;
}

.promo-linha {
  width: 5.0625rem;
  height: 2px;
  background: #d55b0e;
}

.promo-logo {
  width: 3.655rem;
  height: 3.438rem;
  object-fit: cover;
}

.promo-conteudo {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1.0625rem;
  align-self: stretch;
}

.promo-oferta {
  display: flex;
  flex-direction: column;
  align-items: center;
  align-self: stretch;
}

.promo-texto {
  margin: 0;
  align-self: stretch;
  color: rgba(255, 255, 255, 0.81);
  text-align: center;
  font-family: 'Bebas Neue', sans-serif;
  font-size: 1.5rem;
  font-style: normal;
  font-weight: 400;
  line-height: normal;
  text-transform: uppercase;
}

.promo-desconto {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.promo-valor {
  color: #dbdbdb;
  font-family: 'Bebas Neue', sans-serif;
  font-size: 11.875rem;
  font-weight: 400;
  line-height: 0.8;
}

.promo-lateral {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  color: #fff;
  font-family: 'Bebas Neue', sans-serif;
  font-weight: 400;
}

.promo-simbolo {
  font-size: 6.25rem;
  line-height: 0.85;
}

.promo-sufixo {
  font-size: 2.125rem;
  line-height: 1;
}

.promo-divisor {
  width: 14.6875rem;
  max-width: 100%;
  height: 2px;
  background: #c7692f;
}

.promo-botao {
    position: relative;
    overflow: hidden;
  display: flex;
  width: 13.1875rem;
  height: 2.625rem;
  padding: 1.182rem 1.418rem 1.148rem 1.418rem;
  justify-content: center;
  align-items: center;
  gap: 1.625rem;
  box-sizing: border-box;
  border-radius: 0.4727rem;
  border: 0.54px solid #fff;
  background: #9c450e;
  color: #fdf5f5;
  font-family: 'Bebas Neue', sans-serif;
  font-size: 1.0804rem;
  font-style: normal;
  font-weight: 400;
  line-height: normal;
  letter-spacing: 0.19rem;
  text-transform: uppercase;
  text-decoration: none;
  white-space: nowrap;
  transition: all 0.2s cubic-bezier(0.22, 0.01, 0.36, 1); /* Adiciona uma transição suave para a transformação */
}

.promo-botao:hover {
  transform: scale(1.05);
}

.promo-botao:active {
  transform: scale(1.02);
}

/* o feixe de luz (começa fora do botão, à esquerda) */
.promo-botao::before {
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

/* no hover, o feixe atravessa o botão */
.promo-botao:hover::before {
  animation: feixe 0.4s ease-in-out;
}

@keyframes feixe {
  from {
    left: -75%;
  }
  to {
    left: 125%;
  }
}

@media (max-width: 640px) {
  .promo {
    width: 100%;
    height: auto;
    padding: 1.5rem 1.125rem 1.25rem;
    gap: 1rem;
    border-radius: 1rem;
  }

  .promo-topo {
    gap: 0.75rem;
  }

  .promo-linha {
    width: 3.4rem;
  }

  .promo-conteudo {
    gap: 0.875rem;
  }

  /* o bloco da oferta vira uma grade de 3 colunas */
  .promo-oferta {
    display: grid;
    grid-template-columns: auto auto auto;
    grid-template-rows: auto 1fr 1fr;
    justify-content: center;
    align-items: center;
    padding-bottom: 0.375rem;
  }

  /* "Damos": linha de cima, ocupando as 3 colunas */
  .promo-oferta > .promo-texto:first-child {
    grid-column: 1 / -1;
    grid-row: 1;
    font-size: 1.5rem;
  }

  /* "display: contents" tira essas caixas do caminho: o 20, o % e o OFF viram itens da grade */
  .promo-desconto,
  .promo-lateral {
    display: contents;
  }

  .promo-valor,
  .promo-simbolo {
    grid-row: 2 / 4;
    font-size: 5.5rem;
    line-height: 0.85;
  }

  .promo-valor {
    grid-column: 1;
  }

  .promo-simbolo {
    grid-column: 2;
  }

  .promo-sufixo {
    grid-column: 3;
    grid-row: 2;
    align-self: end;
    margin-left: 1rem;
    font-size: 1.5rem;
    color: rgba(255, 255, 255, 0.55);
  }

  .promo-oferta > .promo-texto:last-child {
    grid-column: 3;
    grid-row: 3;
    align-self: start;
    margin-left: 1rem;
    text-align: left;
    font-size: 1.375rem;
    white-space: nowrap;
  }

  .promo-divisor {
    width: 100%;
  }

  .promo-botao {
    width: 100%;
    height: 3rem;
    padding: 0;
    background: #c7550d;
    font-size: 1.125rem;
    letter-spacing: 0.05rem;
  }
}

/* ---------- ajustes para tablets ---------- */
@media (min-width: 641px) and (max-width: 1024px) {
  .promo {
    width: 15.75rem;
    height: auto;
    padding: 1.125rem 1rem 1.25rem;
    gap: 0.875rem;
  }

  .promo-linha {
    width: 3.5rem;
  }

  .promo-texto {
    font-size: 1.25rem;
  }

  .promo-valor {
    font-size: 8.5rem;
  }

  .promo-simbolo {
    font-size: 4.5rem;
  }

  .promo-sufixo {
    font-size: 1.75rem;
  }

  .promo-divisor {
    width: 100%;
  }

  .promo-botao {
    width: 100%;
    height: 2.75rem;
    padding: 0;
    background: #c7550d;
    font-size: 1rem;
    letter-spacing: 0.08rem;
  }
}

</style>