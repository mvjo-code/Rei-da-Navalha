<script setup>
import PromoCard from './PromoCard.vue'
import BeneficioCard from './BeneficioCard.vue'

const beneficios = [
  {
    titulo: 'Corte com precisão',
    texto: 'Técnicas certas para cada perfil e estilo, com atenção total na medida certa.',
  },
  {
    titulo: 'Barba definida',
    texto: 'Acabamento limpo, linhas nítidas e cuidado com cada detalhe da aparência.',
  },
  {
    titulo: 'Atendimento com respeito',
    texto: 'Ambiente tranquilo, escuta atenta e foco na sua experiência desde o início.',
  },
]
</script>

<template>
  <section id="inicio" class="hero">

    <div class="hero-overlay"></div>

    <div class="hero-conteudo">
      <div class="hero-topo">
        <div class="hero-esquerda">
          <div class="hero-textos">
            <p class="hero-subtitulo">Sua aparência é nosso foco!</p>
            <h1 class="hero-titulo">
              <span class="titulo-linha-1">Rei da</span>
              <span class="titulo-linha-2">Navalha</span>
            </h1>
          </div>

          <div class="hero-botoes">
            <a href="#contato" class="btn-agendar">
              <span class="btn-agendar-icone">
                 <img src="../assets/icones/Ícone de agendamento.svg" alt="icone de calendário" />
              </span>
              <span class="btn-agendar-texto">Agendar</span>
            </a>

            <a href="#servicos" class="btn-servicos">Serviços →</a>
          </div>
        </div>

        <PromoCard />
      </div>

      <div class="beneficios">
        <BeneficioCard
          v-for="item in beneficios"
          :key="item.titulo"
          :titulo="item.titulo"
          :texto="item.texto"
          class="beneficio"
        />
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero {
    padding: 6.875rem var(--margem-lateral) 2.5rem;

  position: relative; /* necessário para o vídeo se posicionar em relação ao hero */
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100dvh;
  overflow: hidden;
  box-sizing: border-box;
  background-image: url('../assets/imagens/teste2.jpg');
    background-size: cover;
    background-position: center;
  background-color: #1c1c1c; /* aparece um instante antes do vídeo carregar */
}

.hero-video {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover; /* preenche o espaço sem distorcer, cortando o excesso */
  z-index: 0;
}

.hero-overlay {
  position: absolute;
  inset: 0;
  z-index: 1;
  background-color: rgba(0, 0, 0, 0.673);

}
.hero-conteudo {
  position: relative; /* fica acima do vídeo e do overlay */
  z-index: 2;
  display: flex;
  min-width: 0;
  width: 100%;
  flex-direction: column;
  align-items: flex-start;
  gap: 2.5rem;
}

.hero-topo {
  display: flex;
  width: 100%;
  align-items: center;
  justify-content: space-between; /* no lugar do gap: 302px */
  gap: 2rem;
}

.hero-esquerda {
  display: flex;
  width: 36.6875rem;
  flex-direction: column;
  align-items: flex-start;
  gap: 3.75rem;
}

.hero-textos {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  align-self: stretch;
}

.hero-subtitulo {
  height: 1.5rem;
  margin: 0;
  align-self: stretch;
  color: rgba(255, 255, 255, 0.78);
  font-family: 'Bebas Neue', sans-serif;
  font-size: 1.25rem;
  font-style: normal;
  font-weight: 400;
  line-height: normal;
  text-transform: uppercase;
}

.hero-titulo {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  align-self: stretch;
  margin: -0.875rem 0 0;
  font-family: 'Bebas Neue', sans-serif;
  font-size: 10.855rem;
  font-style: normal;
  font-weight: 400;
  line-height: normal;
  text-transform: uppercase;
  white-space: nowrap;
}

.titulo-linha-1 {
  height: 10.125rem;
  align-self: stretch;
  color: #dbdbdb;
}

.titulo-linha-2 {
  height: 9.8125rem;
  align-self: stretch;
  color: #f8f8f8;
  -webkit-text-stroke-width: 1px;
  -webkit-text-stroke-color: rgba(212, 91, 14, 0.12);
}

.hero-botoes {
  display: flex;
  width: 35.25rem;
  height: 6rem;
  justify-content: center;
  align-items: center;
  gap: 2.625rem;
  box-sizing: border-box;
  border-radius: 1.5rem;
  background: rgba(0, 0, 0, 0.15);
}

/* botão agendar (ícone + texto) */
.btn-agendar {
    position: relative;
    overflow: hidden;
  display: flex;
  width: 16.3125rem;
  height: 4.25rem;
  flex-shrink: 0;
  box-sizing: border-box;
  overflow: hidden;
  border-radius: 0.8125rem;
  border: 1.5px solid #c2c2c1;
  background: #c7550d;
  text-decoration: none;
  transition: transform 0.3s cubic-bezier(0.22, 0.01, 0.36, 1);
  letter-spacing: 0.495rem;
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
  font-style: normal;
  font-weight: 400;
  line-height: 100%;
  text-transform: uppercase;
}

/* botão serviços */
.btn-servicos {
    position: relative;
    overflow: hidden;
  display: flex;
  width: 16.3155rem;
  height: 4.152rem;
  padding: 1.866rem 2.239rem 1.813rem 2.239rem;
  justify-content: center;
  align-items: center;
  gap: 0.533rem;
  flex-shrink: 0;
  box-sizing: border-box;
  border-radius: 0.746rem;
  border: 0.853px solid #d45b0e;
  background: linear-gradient(90deg, rgba(212, 91, 14, 0.11) 56.25%, rgba(0, 0, 0, 0.16) 100%);
  color: #fff;
  font-family: 'Bebas Neue', sans-serif;
  font-size: 1.706rem;
  font-style: normal;
  font-weight: 400;
  line-height: normal;
  letter-spacing: 0.495rem;
  text-transform: uppercase;
  text-decoration: none;
  white-space: nowrap;
  transition: transform 0.3s cubic-bezier(0.22, 0.01, 0.36, 1);
}

/* benefícios */
.beneficios {
  display: flex;
  align-items: flex-start;
  gap: 1rem;
  align-self: stretch;
}

.beneficio {
  flex: 1 1 0;
  width: auto;
}

.btn-agendar:hover,
.btn-servicos:hover {
  transform: scale(1.03);
}

/* animmação de feixe de luz */
/* feixe de luz (começa fora do botão, à esquerda) */
.btn-agendar::before,
.btn-servicos::before {
  content: '';
  position: absolute;
  top: 0;
  left: -55%;
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
  z-index: 1;
}

/* no hover, o feixe atravessa o botão */
.btn-agendar:hover::before,
.btn-servicos:hover::before {
  animation: feixe 0.5s ease-in-out;
}

@keyframes feixe {
  from {
    left: -75%;
  }
  to {
    left: 125%;
  }
}


/* ========== TABLET E CELULAR ========== */
/* ========== TABLET E CELULAR (parte comum) ========== */
@media (max-width: 1024px) {
  .hero {
    --altura-video: max(100dvh, 55rem);
    height: auto;
    min-height: 100dvh;
    overflow: visible;
    align-items: flex-start;
    padding: 10.5rem var(--margem-lateral) 3rem;   /* espaço da navbar de duas linhas */
  }

  /* o vídeo cobre só a primeira tela e some num degradê */
  .hero-video {
    height: var(--altura-video);
  }

  .hero-overlay {
    bottom: auto;
    height: var(--altura-video);
  }

  .hero::after {
    content: '';
    position: absolute;
    left: 0;
    right: 0;
    top: calc(var(--altura-video) - 10rem);
    height: 10rem;
    background: linear-gradient(180deg, transparent 0%, #1c1c1c 100%);
    pointer-events: none;
    z-index: 1;
  }

  .hero-conteudo {
    align-items: stretch;
    gap: 1.75rem;
  }

  .hero-topo {
    gap: 1.5rem;
  }

  .hero-esquerda {
    gap: 1.5rem;
  }

  .hero-textos {
    align-items: flex-start;
    text-align: left;
  }

  .hero-subtitulo {
    height: auto;
    font-size: 1.125rem;
  }

  .hero-titulo {
    align-items: flex-start;
    margin: 0.25rem 0 0;
  }

  .titulo-linha-1,
  .titulo-linha-2 {
    height: auto;
    line-height: 0.95;
  }

  /* os botões saem da "caixa" escura */
  .hero-botoes {
    width: 100%;
    height: auto;
    padding: 0;
    background: none;
    border-radius: 0;
  }

  /* Agendar: o ícone vai para dentro do botão laranja */
  .btn-agendar {
    justify-content: center;
    align-items: center;
    gap: 0.75rem;
    border-width: 1px;
    border-radius: 0.625rem;
    letter-spacing: 0.05rem;
  }

  .btn-agendar-icone {
    width: auto;
    border-right: 0;
    background: none;
    align-self: center;
  }

  .btn-agendar-icone img {
    width: 1.25rem;
    height: 1.25rem;
  }

  .btn-agendar-texto {
    flex: 0 0 auto;
    font-size: 1.5rem;
  }

  .btn-servicos {
    padding: 0;
    border-width: 1px;
    border-radius: 0.625rem;
    font-size: 1.5rem;
    letter-spacing: 0.06rem;
  }

  .beneficios {
    gap: 1rem;
  }
}

/* ========== TABLET (design próprio) ========== */
@media (min-width: 641px) and (max-width: 1024px) {
  /* texto e botões à esquerda, promoção à direita, centralizados na vertical */
  .hero-topo {
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
  }

  .hero-esquerda {
    flex: 1 1 0;
    width: auto;
    min-width: 0;
  }

  /* painel escuro atrás dos textos */
  .hero-textos {
    padding: 0.75rem 1rem 0.5rem;
    border-radius: 1rem;
    background: rgba(0, 0, 0, 0.3);
  }

  .hero-titulo {
    font-size: 7.6rem;
  }

  /* botões um embaixo do outro */
  .hero-botoes {
    flex-direction: column;
    gap: 1.25rem;
  }

  .btn-agendar,
  .btn-servicos {
    flex: none;
    width: 100%;
    height: 3.4rem;
  }

  /* os 3 benefícios em linha */
  .beneficios {
    flex-direction: row;
    align-items: stretch;
  }

  .beneficio {
    flex: 1 1 0;
    min-width: 0;
    width: auto;
    height: auto;
  }
}

/* ========== CELULAR (design próprio) ========== */
@media (max-width: 640px) {
  .hero {
    padding-top: 10rem;
  }

  .hero-topo {
    flex-direction: column;
    align-items: stretch;
    gap: 3rem;
  }

  .hero-esquerda {
    width: 100%;
    gap: 2.75rem;
  }

  .hero-titulo {
    font-size: 6rem;
  }

  /* os dois botões lado a lado */
  .hero-botoes {
    flex-direction: row;
    gap: 0.75rem;
  }

  .btn-agendar,
  .btn-servicos {
    flex: 1 1 0;
    width: auto;
    min-width: 0;
    height: 3.4375rem;
  }

  .btn-agendar {
    gap: 0.5rem;
    letter-spacing: 0.03rem;
  }

  .btn-agendar-texto {
    font-size: 1.25rem;
  }

  .btn-servicos {
    font-size: 1.25rem;
    letter-spacing: 0.04rem;
  }

  /* benefícios empilhados */
  .beneficios {
    flex-direction: column;
  }

  .beneficio {
    flex: none;           /* o que faltava: sem isso a altura vira 0 */
    width: 100%;
    height: auto;
  }
}

</style>