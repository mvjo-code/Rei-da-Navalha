<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'

// "secao" = id da seção da página onde o link está.
// Horários fica dentro da seção Ofertas, e Contato dentro da seção Sobre.
const links = [
  { texto: 'Início', href: '#inicio', secao: 'inicio' },
  { texto: 'Serviços', href: '#servicos', secao: 'servicos' },
  { texto: 'Ofertas', href: '#ofertas', secao: 'ofertas' },
  { texto: 'Horários', href: '#horarios', secao: 'ofertas' },
  { texto: 'Sobre', href: '#sobre', secao: 'sobre' },
  { texto: 'Contato', href: '#contato', secao: 'sobre' },
]

const linkAtivo = ref('#inicio')

let secaoAtual = 'inicio'   // seção que está no meio da tela agora
let destino = null          // seção para onde um clique está rolando (null = nenhuma)
let observador = null

// clique em um link
function aoClicar(link) {
  linkAtivo.value = link.href
  // só "espera chegar" se o link levar a outra seção
  destino = link.secao !== secaoAtual ? link.secao : null
}

// se a pessoa rolar por conta própria, para de esperar o destino do clique
function cancelarDestino() {
  destino = null
}

// o observador chama esta função quando alguma seção entra ou sai da faixa do meio da tela
function aoMudarSecao(entradas) {
  for (const entrada of entradas) {
    if (!entrada.isIntersecting) continue   // ignora as seções que saíram

    secaoAtual = entrada.target.id

    if (destino !== null) {
      if (secaoAtual === destino) destino = null   // chegou: o link clicado continua ativo
      continue                                     // passando por outra seção: não muda nada
    }

    // rolagem normal: ativa o primeiro link daquela seção
    const link = links.find((l) => l.secao === secaoAtual)
    linkAtivo.value = link.href
  }
}

const eventos = ['wheel', 'touchstart', 'keydown']

onMounted(() => {
  const ids = [...new Set(links.map((l) => l.secao))]
  const elementos = ids.map((id) => document.getElementById(id)).filter(Boolean)

  observador = new IntersectionObserver(aoMudarSecao, {
    rootMargin: '-45% 0px -45% 0px',   // olha só para uma faixa fina no meio da tela
  })
  elementos.forEach((el) => observador.observe(el))

  eventos.forEach((e) => window.addEventListener(e, cancelarDestino, { passive: true }))
})

onBeforeUnmount(() => {
  observador?.disconnect()
  eventos.forEach((e) => window.removeEventListener(e, cancelarDestino))
})
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
        @click="aoClicar(link)"
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

.logo img {
  width: 80px;
  height: auto;
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
  height: 58.431px;
  padding: 20px 35.83px 20px 35.83px;
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

/* ========== TABLET E CELULAR: navbar em duas linhas ========== */
/* ========== TABLET E CELULAR: navbar em duas linhas ========== */
@media (max-width: 1024px) {
  .navbar {
    flex-wrap: wrap;
    row-gap: 0.75rem;
    column-gap: 1rem;
    padding-top: 0.75rem;
    padding-bottom: 0.75rem;
    background: rgba(12, 12, 12, 0.88);
  }

  .logo {
    order: 1;
  }

  .logo img {
    display: block;
    height: 3.4rem;
    width: auto;
  }

  .botao-agendar {
    order: 2;
    width: 11.5rem;
    height: 3.4rem;
    padding: 0;
    gap: 0.75rem;
    border-radius: 0.625rem;
    border-width: 1px;
  }

  .botao-agendar img {
    width: 1.375rem;
    height: 1.375rem;
  }

  .botao-agendar span {
    color: #fff;
    font-size: 1.375rem;
    letter-spacing: 0.04rem;
  }

  .menu {
    order: 3;
    flex-basis: 100%;
    width: 100%;
    justify-content: space-between;
    gap: 0;
  }

  .menu-link {
    font-size: 1.125rem;
    letter-spacing: 0.05rem;
  }

  .menu-link::after {
    display: none;
  }
}

@media (max-width: 640px) {
  .botao-agendar {
    width: 9.5rem;
    height: 3rem;
  }

  .botao-agendar img {
    width: 1.25rem;
    height: 1.25rem;
  }

  .botao-agendar span {
    font-size: 1.25rem;
  }

  .menu-link {
    font-size: 1rem;
  }
}

</style>
