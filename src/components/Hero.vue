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
    <video
      class="hero-video"
      autoplay
      muted
      loop
      playsinline
    >
      <source src="../assets/imagens/.mp4" type="video/mp4" />
    </video>

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
@media (max-width: 1024px) {
  .hero {
    padding: 6rem var(--margem-lateral) 2.5rem;

    height: auto;           /* libera a altura: o conteúdo empilhado não cabe em 1 tela */
    min-height: 100dvh;
    overflow: visible;
    align-items: flex-start;
  }

  .hero-conteudo {
    align-items: center;
  }

  .hero-topo {
    flex-direction: column;
    gap: 2rem;
  }

  .hero-esquerda {
    width: 100%;
    align-items: center;
    gap: 2rem;
  }

  .hero-textos {
    align-items: center;
    text-align: center;
  }

  .hero-titulo {
    align-items: center;
    font-size: clamp(5rem, 22vw, 9rem);
  }

  .titulo-linha-1,
  .titulo-linha-2 {
    height: auto;
    line-height: 0.9;
  }

  .hero-botoes {
    width: 100%;
    height: auto;
    flex-wrap: wrap;
    gap: 1rem;
    padding: 1rem;
  }

  .btn-agendar,
  .btn-servicos {
    flex: 1 1 14rem; /* lado a lado se couber, senão um embaixo do outro */
    width: auto;
  }

  .beneficios {
    flex-direction: column;
    width: 100%;
  }

  .beneficio {
    width: 100%;
    height: auto;
  }
}
</style>