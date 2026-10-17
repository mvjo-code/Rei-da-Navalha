<script setup>
import { ref, computed } from 'vue'
import ServicoCard from './ServicoCard.vue'
import BotaoAgendar from './BotaoAgendar.vue'

// import imgBarba from '../assets/imagens/barba.jpg'  // exemplo de como importar as fotos

// preco e duracao são valores de exemplo: troque pelos reais
const servicos = [
  { titulo: 'Corte', descricao: 'Estilo e precisão para o seu visual.', imagem: 'src/assets/imagens/exemploservico.png', preco: 'R$ 30', duracao: '40 min' },
  { titulo: 'Barba', descricao: 'Cuidado e definição para a sua barba.', imagem: 'src/assets/imagens/barbacard.jpg', preco: 'R$ 25', duracao: '30 min' },
  { titulo: 'Sobrancelha', descricao: 'Acabamento limpo e alinhado.', imagem: 'src/assets/imagens/sobrancelha.jpg', preco: 'R$ 10', duracao: '15 min' },
  { titulo: 'Pigmentação', descricao: 'Cobertura natural e uniforme.', imagem: 'src/assets/imagens/pigmentacao.jpg', preco: 'R$ 35', duracao: '30 min' },
  { titulo: 'Combo', descricao: 'Corte e barba com preço especial.', imagem: 'src/assets/imagens/combo.jpg', preco: 'R$ 50', duracao: '1h 10min' },
]

const ativo = ref(1)

const servicoAtivo = computed(() => servicos[ativo.value])

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
    <!-- coloque aqui a imagem de fundo (veja o comentário no CSS) -->
    <div class="servicos-overlay"></div>

    <div class="servicos-conteudo">
      <header class="servicos-cabecalho">
        <h2 class="servicos-titulo">PRINCIPAIS    SERVIÇOS</h2>
        <span class="servicos-traco"></span>
      </header>

      <div class="palco">
        <ServicoCard v-for="(servico, i) in servicos" :key="servico.titulo" v-bind="servico"
          :class="['item', classe(i)]" :style="{ '--offset': posicao(i) }"
          @click="classe(i) === 'lateral' && (ativo = i)" />
      </div>

      <div class="controles">
        <button class="seta" type="button" aria-label="Serviço anterior" @click="anterior">
          <svg viewBox="0 0 24 24" fill="none">
            <path d="M15 18l-6-6 6-6" stroke="currentColor" stroke-width="2" stroke-linecap="round"
              stroke-linejoin="round" />
          </svg>
        </button>

        <div class="pontos">
          <button v-for="(servico, i) in servicos" :key="servico.titulo" type="button"
            :class="['ponto', { ativo: i === ativo }]" :aria-label="`Ver ${servico.titulo}`"
            @click="ativo = i"></button>
        </div>

        <button class="seta" type="button" aria-label="Próximo serviço" @click="proximo">
          <svg viewBox="0 0 24 24" fill="none">
            <path d="M9 18l6-6-6-6" stroke="currentColor" stroke-width="2" stroke-linecap="round"
              stroke-linejoin="round" />
          </svg>
        </button>
      </div>

      <BotaoAgendar :texto="`Agendar ${servicoAtivo.titulo}`" href="#contato" class="botao-servico" />
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
  overflow-x: clip;
  /* os cards laterais saem pela borda da tela sem criar rolagem */
  background: url('src/assets/imagens/texturaservicos.png') center / cover no-repeat #1c1c1c;
}

/* fundo em largura total, sem painel: escuro nas bordas e embaixo, mais leve no centro */
.servicos-overlay {
  position: absolute;
  inset: 0;
  z-index: 0;
  pointer-events: none;
}

.servicos-conteudo {
  position: relative;
  z-index: 1;
  display: flex;
  width: 100%;
  flex-direction: column;
  align-items: center;
  gap: 2rem;
}

/* ---------- título ---------- */
.servicos-cabecalho {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.75rem;
}

.servicos-titulo {
  margin: 0;
  color: rgba(255, 255, 255, 0.85);
  text-align: center;
  -webkit-text-stroke: 1px rgba(212, 91, 14, 0.78);
  font-family: 'Bebas Neue', sans-serif;
  font-size: 7rem;
  font-weight: 400;
  line-height: 1;
  text-transform: uppercase;
}

.servicos-traco {
  width: 4rem;
  height: 3px;
  background: #d55b0e;
}

/* ---------- carrossel ---------- */
.palco {
  position: relative;
  width: calc(100% + 2 * var(--margem-lateral));
  margin-inline: calc(-1 * var(--margem-lateral));
  height: 22rem;
  --distancia: 32rem;        /* distância entre o centro e os cards laterais */
  --escala-lateral: 0.6;     /* tamanho dos cards laterais */
}

.item {
  --escala: 1;
  position: absolute;
  top: 50%;
  left: 50%;
  will-change: transform, opacity;
  transform: translate(-50%, -50%) translateX(calc(var(--offset) * var(--distancia))) scale(var(--escala));
  transition:
    transform 0.6s cubic-bezier(0.22, 1, 0.36, 1),
    opacity 0.6s ease;
}

.item.ativo {
  z-index: 3;
}

.item.ativo:hover {
  --escala: 1.03;
}

.item.lateral {
  z-index: 2;
  opacity: 0.5;
  cursor: pointer;
  --escala: var(--escala-lateral);
}

.item.lateral:hover {
  opacity: 0.8;
}

.item.oculto {
  z-index: 1;
  opacity: 0;
  pointer-events: none;
  --escala: 0.5;
}

/* ---------- setas e indicadores ---------- */
.controles {
  display: flex;
  align-items: center;
  gap: 1.5rem;
}

.seta {
  display: flex;
  width: 2.75rem;
  height: 2.75rem;
  padding: 0;
  justify-content: center;
  align-items: center;
  border-radius: 50%;
  border: 1px solid rgba(255, 133, 56, 0.7);
  background: transparent;
  color: #ff8538;
  cursor: pointer;
  transition:
    transform 0.35s cubic-bezier(0.22, 1, 0.36, 1),
    background-color 0.3s ease,
    color 0.3s ease;
}

.seta svg {
  width: 1.25rem;
  height: 1.25rem;
}

.seta:hover {
  background: #d45b0e;
  color: #fff;
  transform: scale(1.08);
}

.seta:active {
  transform: scale(0.92);
}

.pontos {
  display: flex;
  align-items: center;
  gap: 0.625rem;
}

.ponto {
  width: 0.5rem;
  height: 0.5rem;
  padding: 0;
  border: none;
  border-radius: 999px;
  background: rgba(255, 255, 255, 0.3);
  cursor: pointer;
  transition:
    width 0.35s cubic-bezier(0.22, 1, 0.36, 1),
    background-color 0.35s ease;
}

.ponto:hover {
  background: rgba(255, 255, 255, 0.6);
}

.ponto.ativo {
  width: 1.75rem;
  /* o ponto ativo fica alongado e laranja */
  background: #d55b0e;
}

/* ---------- botão (largura e espaçamento próprios para caber "Agendar sobrancelha") ---------- */
.botao-servico {
  --btn-agendar-largura: 24rem;
  --btn-agendar-espaco: 0.15rem;
  max-width: 100%;
}

/* ---------- tablet e celular ---------- */
@media (max-width: 1024px) {
  .servicos {
    align-items: flex-start;
    padding-top: 6rem;
  }

  .servicos-titulo {
    font-size: clamp(3rem, 12vw, 4.5rem);
  }

  .palco {
    height: 28rem;
  }

  /* no celular só o card central cabe: as setas e os pontos fazem a troca */
  .item.lateral {
    opacity: 0;
    pointer-events: none;
  }
}

@media (prefers-reduced-motion: reduce) {

  .item,
  .seta,
  .ponto {
    transition: none;
  }
}
</style>