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
  display: flex;
  width: 22rem;                 /* estimado pela imagem */
  max-width: 100%;
  padding: 1.25rem 1.0625rem;
  flex-direction: column;
  align-items: center;
  gap: 1.0625rem;
  flex-shrink: 0;
  box-sizing: border-box;
  border-radius: 0.625rem;
  border: 1px solid #fff;
  background: rgba(0, 0, 0, 0.5);
}

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
  font-size: 4.5rem;            /* estimado pela imagem */
  line-height: 0.95;
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

.oferta-botao {
  position: relative;
  overflow: hidden;
  display: flex;
  width: 100%;
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
  transition: background-color 0.3s ease;
}

.oferta-botao:hover {
  background: #b5520f;
}

/* feixe de luz */
.oferta-botao::before {
  content: '';
  position: absolute;
  top: 0;
  left: -75%;
  width: 50%;
  height: 100%;
  background: linear-gradient(120deg, transparent 0%, rgba(255, 255, 255, 0.3) 50%, transparent 100%);
  transform: skewX(-20deg);
  pointer-events: none;
}

.oferta-botao:hover::before {
  animation: feixe 0.6s ease-in-out;
}

@keyframes feixe {
  from { left: -75%; }
  to { left: 125%; }
}

.oferta-rodape {
  margin: auto 0 0;             /* empurra o rodapé para o fim do card */
  color: rgba(255, 255, 255, 0.85);
  font-family: 'Bebas Neue', sans-serif;
  font-size: 1.375rem;
  font-weight: 400;
  text-align: center;
  text-transform: uppercase;
}

@media (max-width: 1024px) {
  .oferta {
    width: 100%;
    max-width: 26rem;
  }
}

@media (prefers-reduced-motion: reduce) {
  .oferta-botao:hover::before {
    animation: none;
  }
}
</style>