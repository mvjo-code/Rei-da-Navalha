<script setup>
import { ref } from 'vue'

const links = [
  { texto: 'Início', href: '#inicio' },
  { texto: 'Serviços', href: '#servicos' },
  { texto: 'Ofertas', href: '#ofertas' },
  { texto: 'Horários', href: '#horarios' },
  { texto: 'Sobre', href: '#sobre' },
  { texto: 'Contato', href: '#contato' },
]

const linkAtivo = ref('#inicio')
</script>

<template>
  <header class="navbar">
    <a href="#inicio" class="logo">
      <img src="../assets/Logotipo.png" alt="Rei da Navalha" style="color: #d45b0e;">
    </a>

    <nav class="menu">
      <a
        v-for="link in links"
        :key="link.href"
        :href="link.href"
        :class="['menu-link', { ativo: linkAtivo === link.href }]"
        @click="linkAtivo = link.href"
      >
        {{ link.texto }}
      </a>
    </nav>

    <a href="#contato" class="botao-agendar">
       <img src="../assets/icones/icone_calendario.svg" alt="icone de calendário" />
      <span>Agendar</span>
    </a>
  </header>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&display=swap');

.navbar {
  padding-inline: var(--margem-lateral);

  position: fixed;
  top: 0;
  left: 0;
  z-index: 100;

  display: flex;
  /* antes: padding-left: 3em; padding-right: 3em; */
  width: 100%;
  align-items: center;
  justify-content: space-between;
  gap: 197px;
  box-sizing: border-box;
  background-color: rgba(0, 0, 0, 0.515);
}

.logo {
  display: flex;
  align-items: center;
}

.menu {
  display: flex;
  align-items: center;
  gap: 36.147px;
}

.menu-link {
  position: relative; /* necessário para posicionar a linha dentro do link */
  color: rgba(255, 255, 255, 0.85);
  font-family: 'Bebas Neue', sans-serif;
  font-size: 17.446px;
  font-style: normal;
  font-weight: 400;
  line-height: normal;
  letter-spacing: 2.11px;
  text-transform: uppercase;
  text-decoration: none;
  transition: all 0.2s ease-in-out;
}

/* linha fina embaixo do link (começa escondida) */
.menu-link::after {
  content: '';
  position: absolute;
  left: 0;
  bottom: -6px;
  width: calc(100% - 2.11px); /* desconta o letter-spacing sobrando no fim da última letra */
  height: 1px;
  background: currentColor; /* usa a mesma cor do texto */
  transform: scaleX(0);
  transform-origin: left;
  transition: transform 0.3s ease;
}

.menu-link:hover {
  color: #ffe4d4;
  transform: translateY(-2px);
}

.menu-link.ativo {
  color: #d45b0e;
}

.menu-link.ativo::after {
  transform: scaleX(1); /* mostra a linha só no link ativo */
}

.menu-link.ativo:hover {
  color: #e85f0a;
}

.botao-agendar {
  position: relative;  /* novo: serve de referência para o feixe */
  overflow: hidden;    /* novo: esconde o feixe fora do botão */
  display: flex;
  width: 210.048px;
  height: 10.431px;
  padding: 29.858px 35.83px 29.005px 35.83px;
  justify-content: center;
  align-items: center;
  gap: 8.531px;
  flex-shrink: 0;
  box-sizing: border-box;
  border-radius: 11.943px;
  border: 0.853px solid #d45b0e;
  background: rgba(217, 217, 217, 0);
  text-decoration: none;
  transition: all 0.3s cubic-bezier(0.22, 0.01, 0.36, 1);
}

/* o feixe de luz (começa fora do botão, à esquerda) */
.botao-agendar::before {
  content: '';
  position: absolute;
  top: 0;
  left: -75%;
  width: 50%;
  height: 100%;
  background: linear-gradient(
    120deg,
    transparent 0%,
    rgba(255, 255, 255, 0.25) 50%,
    transparent 100%
  );
  transform: skewX(-20deg);
  pointer-events: none;
}

.botao-agendar:hover {
  border-color: #f3640b;
  transform: translateX(-3px);
  box-shadow: 0 8px 20px rgba(212, 91, 14, 0.35);
}

/* no hover, o feixe atravessa o botão */
.botao-agendar:hover::before {
  animation: feixe 0.5s ease-out;
}

@keyframes feixe {
  from {
    left: -75%;
  }
  to {
    left: 125%;
  }
}

.botao-agendar:active {
  transform: translateY(0);
  box-shadow: 0 0 8px rgba(243, 100, 11, 0.25);
}

.botao-agendar span {
  color: #d45b0e;
  font-family: 'Bebas Neue', sans-serif;
  font-size: 16.299px;
  font-style: normal;
  font-weight: 400;
  line-height: normal;
  letter-spacing: 6.558px;
  text-transform: uppercase;
  transition:
    color 0.3s ease,
    text-shadow 0.3s ease;
}

.botao-agendar:hover span {
  color: #f3640b;
  text-shadow: 0 0 8px rgba(243, 100, 11, 0.6); /* brilho no texto */
}
</style>

/*
.botao-agendar {
  display: flex;
  width: 261.048px;
  height: 66.431px;
  padding: 29.858px 35.83px 29.005px 35.83px;
  justify-content: center;
  align-items: center;
  gap: 8.531px;
  flex-shrink: 0;
  box-sizing: border-box;
  border-radius: 11.943px;
  border: 0.853px solid #d45b0e;
  background: rgba(217, 217, 217, 0);
  text-decoration: none;
  transition:
    background-color 0.3s ease,
    border-color 0.3s ease,
    transform 0.3s ease,
    box-shadow 0.3s ease;
}

.botao-agendar:hover {
  border-color: #f3640b;
  background: rgba(243, 100, 11, 0.08); /* leve tom alaranjado no fundo */
  transform: translateY(-3px);
  box-shadow:
    0 8px 20px rgba(212, 91, 14, 0.25), /* sombra projetada embaixo */
    0 0 14px rgba(243, 100, 11, 0.35),  /* brilho em volta do botão */
    inset 0 0 14px rgba(243, 100, 11, 0.12); /* brilho por dentro da borda */
}

.botao-agendar:active {
  transform: translateY(0);
  box-shadow: 0 0 8px rgba(243, 100, 11, 0.25);
}

.botao-agendar span {
  color: #d45b0e;
  font-family: 'Bebas Neue', sans-serif;
  font-size: 27.299px;
  font-style: normal;
  font-weight: 400;
  line-height: normal;
  letter-spacing: 12.558px;
  text-transform: uppercase;
  transition:
    color 0.3s ease,
    text-shadow 0.3s ease;
}

.botao-agendar:hover span {
  color: #f3640b;
  text-shadow: 0 0 8px rgba(243, 100, 11, 0.6); /* brilho no texto */
}
*/