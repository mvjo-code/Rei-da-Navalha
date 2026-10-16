<script setup>
import { ref } from 'vue'
import ServicoCard from './ServicoCard.vue'
import BotaoAgendar from './BotaoAgendar.vue'

// import imgBarba from '../assets/imagens/barba.jpg'  // exemplo de como importar as fotos

const servicos = [
  { titulo: 'Corte', descricao: 'Estilo e precisão para o seu visual.', imagem: '' },
  { titulo: 'Barba', descricao: 'Cuidado e definição para a sua barba.', imagem: '' },
  { titulo: 'Sobrancelha', descricao: 'Acabamento limpo e alinhado.', imagem: '' },
  { titulo: 'Pigmentação', descricao: 'Cobertura natural e uniforme.', imagem: '' },
  { titulo: 'Combo', descricao: 'Corte e barba com preço especial.', imagem: '' },
]

const ativo = ref(1)

function proximo() {
  ativo.value = (ativo.value + 1) % servicos.length
}

function anterior() {
  ativo.value = (ativo.value - 1 + servicos.length) % servicos.length
}

// distância do card até o card ativo: 0 = centro, -1 = esquerda, 1 = direita
function posicao(i) {
  const n = servicos.length
  let d = (i - ativo.value) % n
  if (d > n / 2) d -= n
  if (d < -n / 2) d += n
  return d
}

function classe(i) {
  const d = Math.abs(posicao(i))
  if (d === 0) return 'ativo'
  if (d === 1) return 'lateral'
  return 'oculto'
}
</script>

<template>
  <section id="servicos" class="servicos">
    <!-- coloque aqui a imagem/vídeo de fundo -->

    <div class="overlay"></div>

    <div class="servicos-caixa">
      <h2 class="servicos-titulo">Serviços</h2>

      <div class="carrossel">
        <button class="seta seta-esquerda" type="button" aria-label="Serviço anterior" @click="anterior">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 72 70" fill="none">
            <path
              d="M1 35L28.2222 1V19.8511L71 19.8889V50.1111H28.2222V69L1 35Z"
              stroke="currentColor"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
            />
          </svg>
        </button>

        <div class="palco">
          <ServicoCard
            v-for="(servico, i) in servicos"
            :key="servico.titulo"
            v-bind="servico"
            :class="['item', classe(i)]"
            :style="{ '--offset': posicao(i) }"
            @click="classe(i) === 'lateral' && (ativo = i)"
          />
        </div>

       <button class="seta seta-direita" type="button" aria-label="Próximo serviço" @click="proximo">
  <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 72 70" fill="none">
    <path
      d="M71 35L43.7778 1V19.8511L1 19.8889V50.1111H43.7778V69L71 35Z"
      stroke="currentColor"
      stroke-width="2"
      stroke-linecap="round"
      stroke-linejoin="round"
    />
  </svg>
</button>

      </div>

      <BotaoAgendar />
    </div>
  </section>
</template>

<style scoped>
.servicos {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  min-height: 100dvh;
  padding: 6.875rem var(--margem-lateral) 2.5rem;
  box-sizing: border-box;
  background-color: #1c1c1c;
   background: url('../assets/imagens/cortando.jpg') center / cover no-repeat; 
}
.overlay {
  position: absolute;
  inset: 0;
  z-index: 1;
  background-color: rgba(0, 0, 0, 0.802);

}


.servicos-caixa {
  display: flex;
  width: min(100%, 71rem);   /* estimado pela imagem */
  height: 46.1875rem;        /* 739px */
  padding: 3rem 0 3.5rem;
  box-sizing: border-box;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  background:
    linear-gradient(90deg, rgba(212, 91, 14, 0.05) 0%, rgba(95, 37, 0, 0.23) 100%),
    rgba(0, 0, 0, 0.32);
    z-index: 1;
}

.servicos-titulo {
  margin: 0;
  color: rgba(255, 255, 255, 0.85);
  text-align: center;
  -webkit-text-stroke: 1px rgba(212, 91, 14, 0.78);
  font-family: 'Bebas Neue', sans-serif;
  font-size: 6rem;
  font-weight: 400;
  line-height: normal;
  text-transform: uppercase;
}

/* ---------- carrossel ---------- */
.carrossel {
  position: relative;
  display: flex;
  width: 100%;
  flex: 1;
  align-items: center;
  justify-content: space-between;
  padding: 0 3.9rem;         /* 63px de cada lado */
  box-sizing: border-box;
}

.palco {
  position: relative;
  flex: 1;
  height: 13rem;
}

.item {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%) translateX(calc(var(--offset) * 17rem)) scale(1);
  transition:
    transform 0.6s cubic-bezier(0.22, 1, 0.36, 1),
    opacity 0.6s ease;
}

.item.ativo {
  z-index: 3;
}

.item.ativo:hover {
  transform: translate(-50%, -50%) translateX(calc(var(--offset) * 17rem)) scale(1.05);
}

.item.ativo:active {
  transform: translate(-50%, -50%) translateX(calc(var(--offset) * 17rem)) scale(0.97);
}

.item.lateral {
  z-index: 2;
  opacity: 0.85;
  cursor: pointer;
  transform: translate(-50%, -50%) translateX(calc(var(--offset) * 17rem)) scale(0.55);
}

.item.lateral:hover {
  opacity: 1;
}

.item.oculto {
  z-index: 1;
  opacity: 0;
  pointer-events: none;
  transform: translate(-50%, -50%) translateX(calc(var(--offset) * 17rem)) scale(0.4);
}

/* ---------- setas ---------- */
.seta {
  width: 4.375rem;
  height: 4.25rem;
  padding: 0;
  flex-shrink: 0;
  border: none;
  background: none;
  color: rgba(255, 133, 56, 0.88);
  cursor: pointer;
  transition:
    transform 0.35s cubic-bezier(0.22, 1, 0.36, 1),
    filter 0.35s ease;
}

.seta svg {
  display: block;
  width: 100%;
  height: 100%;
}

.seta:hover {
  filter: drop-shadow(0 0 8px rgba(255, 133, 56, 0.6));
}

.seta-esquerda:hover {
  transform: translateX(-6px);
}

.seta-direita:hover {
  transform: translateX(6px);
}

/* clique: encolhe um pouco, mantendo o deslocamento do hover */
.seta-esquerda:active {
  transform: translateX(-3px) scale(0.92);
}

.seta-direita:active {
  transform: translateX(3px) scale(0.92);
}
/* ---------- tablet e celular ---------- */
@media (max-width: 1024px) {
  .servicos-caixa {
    height: auto;
    min-height: 40rem;
    gap: 2rem;
  }

  .servicos-titulo {
    font-size: clamp(3.5rem, 14vw, 6rem);
  }

  .carrossel {
    padding: 0 0.5rem;
  }

  .seta {
    width: 3rem;
    height: 2.9rem;
  }

  /* no celular só o card central cabe */
  .item.lateral {
    opacity: 0;
    pointer-events: none;
  }
}

@media (prefers-reduced-motion: reduce) {
  .item,
  .seta {
    transition: none;
  }
}
</style>