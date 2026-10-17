<script setup>
import QuadroHorarios from './QuadroHorarios.vue'
import OfertaCard from './OfertaCard.vue'
import BotaoAgendar from './BotaoAgendar.vue'

const horarios = [
  { dia: 'Segunda-feira', horas: '08h às 18h' },
  { dia: 'Terça-feira', horas: '08h às 18h' },
  { dia: 'Quarta-feira', horas: '08h às 18h' },
  { dia: 'Quinta-feira', horas: '08h às 18h' },
  { dia: 'Sexta-feira', horas: '08h às 18h' },
  { dia: 'Sábado', horas: '08h às 18h' },
  { dia: 'Domingo', horas: '08h às 18h' },
]

// cada objeto vira um card. Propriedades que você não escrever usam o valor padrão do OfertaCard
const ofertas = [
  { descricao: 'No corte americano' },
  // para mostrar uma segunda oferta, tire as duas barras do começo da linha abaixo:
  // { precoAntigo: 'De R$ 40,00', preco: 'R$ 30,00', descricao: 'Na barba' },
]
</script>

<template>
  <section id="ofertas" class="ofertas">

    <div class="overlay"></div>

    <div class="ofertas-conteudo">
      <div class="ofertas-linha">
        <QuadroHorarios :horarios="horarios" />

        <div class="ofertas-lateral">
          <OfertaCard v-for="oferta in ofertas" :key="oferta.descricao" v-bind="oferta" />
        </div>
      </div>

      <BotaoAgendar />
    </div>
  </section>
</template>

<style scoped>
.ofertas {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  min-height: 100dvh;
  padding: 6.875rem var(--margem-lateral) 2.5rem;
  box-sizing: border-box;
  background-color: #1c1c1c;
  background: url('../assets/imagens/sessaohorarios.jpg') center / cover no-repeat #1c1c1c;
}


.overlay {
  position: absolute;
  inset: 0;
  z-index: 1;
  background-color: rgba(0, 0, 0, 0.787);

}

.ofertas-conteudo {
  display: flex;
  width: 100%;
  flex-direction: column;
  align-items: flex-start;
  /* botão alinhado à esquerda */
  gap: 4rem;
  z-index: 2;
}

.ofertas-linha {
  display: flex;
  width: 100%;
  /* agora ocupa a largura toda entre as margens */
  align-items: stretch;
  /* quadro e cards com a mesma altura */
  gap: 2rem;
}

/* a "div da direita": pega todo o espaço que o quadro deixa livre */
.ofertas-lateral {
  display: flex;
  flex: 1;
  min-width: 0;
  justify-content: center;
  /* 1 card fica no centro; 2 cards ficam lado a lado, centralizados */
  align-items: stretch;
  gap: 2rem;
}

/* cada card: ideal de 22rem, mas pode encolher se houver dois */
.ofertas-lateral>* {
  flex: 0 1 22rem;
  min-width: 0;
}

@media (max-width: 1024px) {
  .ofertas {
    max-width: 26rem;
  }

  .ofertas-conteudo {
    align-items: center;
    gap: 2rem;
  }

  .ofertas-linha {
    flex-direction: column;
    align-items: center;
    gap: 2rem;
  }

  .ofertas-lateral {
    width: 100%;
    flex: none;
    flex-direction: column;
    align-items: center;
  }

  .ofertas-lateral>* {
    flex: 0 0 auto;
    /* na coluna, o tamanho vem da largura e não do flex-basis */
    width: 100%;
  }
}
</style>