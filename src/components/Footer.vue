<script setup>
const colunas = [
  {
    titulo: 'Links rápidos',
    links: [
      { texto: 'Início', href: '#inicio' },
      { texto: 'Serviços', href: '#servicos' },
      { texto: 'Ofertas', href: '#ofertas' },
      { texto: 'Horários', href: '#horarios' },
      { texto: 'Sobre', href: '#sobre' },
      { texto: 'Contato', href: '#contato' },
    ],
  },
  {
    titulo: 'Nossos serviços',
    links: [
      { texto: 'Corte', href: '#servicos' },
      { texto: 'Barba', href: '#servicos' },
      { texto: 'Corte americano', href: '#servicos' },
    ],
  },
  {
    titulo: 'Links úteis',
    links: [
      { texto: 'Agendamento', href: '#contato' },
      { texto: 'Horários', href: '#horarios' },
      { texto: 'Contato', href: '#contato' },
      { texto: 'Ofertas', href: '#ofertas' },
    ],
  },
]

const pagamentos = [
  { nome: 'Pix', destaque: true },
  { nome: 'Cartão' },
  { nome: 'Dinheiro' },
]

const ano = new Date().getFullYear()
</script>

<template>
  <footer class="footer">
    <div class="footer-principal">
      <!-- ============ marca ============ -->
      <div class="marca">
        <!-- coloque aqui a logo -->
        <!-- <img class="marca-logo" src="../assets/Logotipo.png" alt="Rei da Navalha" /> -->

        <div class="marca-textos">
          <h3 class="marca-nome">Rei da Navalha</h3>
          <p class="marca-sub">Barbearia</p>
        </div>

        <p class="marca-slogan">Sua aparência é nosso foco!</p>

        <div class="redes">
          <a href="https://www.instagram.com/" class="rede" aria-label="Instagram" target="_blank" rel="noopener">
            <svg class="icone" viewBox="0 0 24 24">
              <rect x="3" y="3" width="18" height="18" rx="5" />
              <circle cx="12" cy="12" r="4" />
              <circle cx="17.5" cy="6.5" r="1" />
            </svg>
          </a>

          <a href="https://www.facebook.com/" class="rede" aria-label="Facebook" target="_blank" rel="noopener">
            <svg class="icone" viewBox="0 0 24 24">
              <path d="M18 2h-3a5 5 0 0 0-5 5v3H7v4h3v8h4v-8h3l1-4h-4V7a1 1 0 0 1 1-1h3z" />
            </svg>
          </a>

          <a href="#" class="rede" aria-label="X" target="_blank" rel="noopener">
            <svg class="icone icone-cheio" viewBox="0 0 24 24">
              <path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z" />
            </svg>
          </a>

          <a href="#" class="rede" aria-label="YouTube" target="_blank" rel="noopener">
            <svg class="icone" viewBox="0 0 24 24">
              <path d="M22.54 6.42a2.78 2.78 0 0 0-1.94-2C18.88 4 12 4 12 4s-6.88 0-8.6.46a2.78 2.78 0 0 0-1.94 2A29 29 0 0 0 1 11.75a29 29 0 0 0 .46 5.33A2.78 2.78 0 0 0 3.4 19c1.72.46 8.6.46 8.6.46s6.88 0 8.6-.46a2.78 2.78 0 0 0 1.94-2 29 29 0 0 0 .46-5.25 29 29 0 0 0-.46-5.33z" />
              <polygon points="9.75 15.02 15.5 11.75 9.75 8.48 9.75 15.02" />
            </svg>
          </a>
        </div>
      </div>

      <!-- ============ colunas de links ============ -->
      <nav
        v-for="coluna in colunas"
        :key="coluna.titulo"
        class="coluna"
        :aria-label="coluna.titulo"
      >
        <h4 class="coluna-titulo">{{ coluna.titulo }}</h4>

        <ul class="lista">
          <li v-for="link in coluna.links" :key="link.texto">
            <a :href="link.href" class="link">{{ link.texto }}</a>
          </li>
        </ul>
      </nav>

      <!-- ============ contato ============ -->
      <div class="coluna">
        <h4 class="coluna-titulo">Contato</h4>

        <ul class="lista lista-contato">
          <li>
            <svg class="icone" viewBox="0 0 24 24">
              <path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 22 16.92z" />
            </svg>
            <a href="https://wa.me/5581988780290" class="link">(81) 98878-0290</a>
          </li>

          <li>
            <svg class="icone" viewBox="0 0 24 24">
              <path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z" />
              <polyline points="22,6 12,13 2,6" />
            </svg>
            <a href="mailto:contatomh11@gmail.com" class="link">contatomh11@gmail.com</a>
          </li>

          <li>
            <svg class="icone" viewBox="0 0 24 24">
              <path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z" />
              <circle cx="12" cy="10" r="3" />
            </svg>
            <span class="texto">Cohab / Pernambuco</span>
          </li>

          <li>
            <svg class="icone" viewBox="0 0 24 24">
              <circle cx="12" cy="12" r="10" />
              <polyline points="12 6 12 12 16 14" />
            </svg>
            <span class="texto">Seg–Dom: 08h às 18h</span>
          </li>
        </ul>

        <div class="pagamento">
          <span class="pagamento-label">Formas de pagamento*</span>

          <div class="pagamento-tags">
            <span
              v-for="item in pagamentos"
              :key="item.nome"
              :class="['tag', { destaque: item.destaque }]"
            >
              {{ item.nome }}
            </span>
          </div>

          <p class="pagamento-nota">*Formas de pagamento a confirmar</p>
        </div>
      </div>
    </div>

    <div class="footer-base">
      <p class="base-texto">Rei da Navalha — Sua aparência é nosso foco!</p>
      <p class="base-texto">© {{ ano }} — Design feito por Matheus</p>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  width: 100%;
  background: linear-gradient(90deg, rgb(0, 0, 0) 0%, rgba(114, 60, 26, 0.244) 100%);
}

.footer-principal {
  display: grid;
  grid-template-columns: 1.25fr repeat(4, 1fr);
  gap: 2rem;
  padding: 2.5rem var(--margem-lateral) 2rem;
  box-sizing: border-box;
}

/* ---------- ícones (todos compartilham o mesmo estilo) ---------- */
.icone {
  width: 1rem;
  height: 1rem;
  flex-shrink: 0;
  fill: none;
  stroke: currentColor;
  stroke-width: 2;
  stroke-linecap: round;
  stroke-linejoin: round;
  color: #d55b0e;
}

.icone-cheio {
  fill: currentColor;
  stroke: none;
}

/* ---------- marca ---------- */
.marca {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 0.75rem;
}

.marca-logo {
  width: 3rem;
  height: 2.8125rem;
  object-fit: cover;
}

.marca-textos {
  display: flex;
  flex-direction: column;
  gap: 0.125rem;
}

.marca-nome {
  margin: 0;
  color: #d55b0e;
  font-family: 'Bebas Neue', sans-serif;
  font-size: 1.25rem;
  font-weight: 400;
  line-height: normal;
  letter-spacing: 0.075rem;
  text-transform: uppercase;
}

.marca-sub {
  margin: 0;
  color: rgba(255, 255, 255, 0.5);
  font-family: 'Bebas Neue', sans-serif;
  font-size: 0.75rem;
  font-weight: 400;
  letter-spacing: 0.1rem;
  text-transform: uppercase;
}

.marca-slogan {
  margin: 0;
  color: rgba(255, 255, 255, 0.67);
  font-family: 'Bebas Neue', sans-serif;
  font-size: 0.8125rem;
  font-weight: 400;
  letter-spacing: 0.05rem;
  text-transform: uppercase;
}

.redes {
  display: flex;
  gap: 0.5rem;
}

.rede {
  display: flex;
  width: 2rem;
  height: 2rem;
  justify-content: center;
  align-items: center;
  box-sizing: border-box;
  border-radius: 0.5rem;
  border: 1px solid rgba(255, 255, 255, 0.12);
  background: rgba(255, 255, 255, 0.04);
  transition:
    transform 0.35s cubic-bezier(0.22, 1, 0.36, 1),
    border-color 0.3s ease,
    background-color 0.3s ease;
}

.rede:hover {
  transform: translateY(-3px);
  border-color: rgba(212, 91, 14, 0.7);
  background: rgba(212, 91, 14, 0.14);
}

/* ---------- colunas ---------- */
.coluna {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 0.875rem;
  min-width: 0;
}

.coluna-titulo {
  margin: 0;
  color: rgba(255, 255, 255, 0.85);
  font-family: 'Bebas Neue', sans-serif;
  font-size: 1rem;
  font-weight: 400;
  line-height: normal;
  letter-spacing: 0.1rem;
  text-transform: uppercase;
}

/* sublinhado laranja curto embaixo do título */
.coluna-titulo::after {
  content: '';
  display: block;
  width: 2.4rem;
  height: 2px;
  margin-top: 0.375rem;
  background: #d55b0e;
}

.lista {
  display: flex;
  margin: 0;
  padding: 0;
  list-style: none;
  flex-direction: column;
  gap: 0.75rem;
}

.link,
.texto {
  color: rgba(255, 255, 255, 0.67);
  font-family: 'Bebas Neue', sans-serif;
  font-size: 0.9375rem;
  font-weight: 400;
  line-height: normal;
  letter-spacing: 0.06rem;
  text-transform: uppercase;
  text-decoration: none;
}

.link {
  display: inline-block;
  transition:
    color 0.3s ease,
    transform 0.35s cubic-bezier(0.22, 1, 0.36, 1);
}

.link:hover {
  color: #f57d30;
  transform: translateX(4px);
}

.lista-contato li {
  display: flex;
  align-items: center;
  gap: 0.625rem;
}

/* ---------- pagamento ---------- */
.pagamento {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 0.5rem;
}

.pagamento-label {
  color: rgba(255, 255, 255, 0.4);
  font-family: 'Bebas Neue', sans-serif;
  font-size: 0.75rem;
  font-weight: 400;
  letter-spacing: 0.06rem;
  text-transform: uppercase;
}

.pagamento-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.tag {
  padding: 0.125rem 0.5rem;
  border-radius: 0.25rem;
  border: 1px solid rgba(255, 255, 255, 0.25);
  color: rgba(255, 255, 255, 0.6);
  font-family: 'Bebas Neue', sans-serif;
  font-size: 0.6875rem;
  font-weight: 400;
  letter-spacing: 0.06rem;
  text-transform: uppercase;
}

.tag.destaque {
  border-color: rgba(212, 91, 14, 0.8);
  color: #d55b0e;
}

.pagamento-nota {
  margin: 0;
  color: rgba(255, 255, 255, 0.35);
  font-family: 'Bebas Neue', sans-serif;
  font-size: 0.625rem;
  font-weight: 400;
  letter-spacing: 0.05rem;
  text-transform: uppercase;
}

/* ---------- barra de baixo ---------- */
.footer-base {
  display: flex;
  padding: 0.875rem var(--margem-lateral);
  justify-content: space-between;
  align-items: center;
  gap: 1rem;
  box-sizing: border-box;
  border-top: 1px solid rgba(255, 255, 255, 0.08);
}

.base-texto {
  margin: 0;
  color: rgba(255, 255, 255, 0.4);
  font-family: 'Bebas Neue', sans-serif;
  font-size: 0.75rem;
  font-weight: 400;
  letter-spacing: 0.06rem;
  text-transform: uppercase;
}

/* ---------- tablet e celular ---------- */
@media (max-width: 1024px) {
  .footer-principal {
    grid-template-columns: repeat(2, 1fr);
    gap: 2.5rem 2rem;
  }

  .marca {
    grid-column: 1 / -1;     /* a marca ocupa a linha inteira */
  }
}

@media (max-width: 600px) {
  .footer-principal {
    grid-template-columns: 1fr;
  }

  .footer-base {
    flex-direction: column;
    align-items: flex-start;
    gap: 0.5rem;
  }
}

@media (prefers-reduced-motion: reduce) {
  .rede,
  .link {
    transition: none;
  }
  .rede:hover,
  .link:hover {
    transform: none;
  }
}
</style>