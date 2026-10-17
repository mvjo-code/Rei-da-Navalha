<script setup>
import CampoContato from './CampoContato.vue'
import BotaoAgendar from './BotaoAgendar.vue'
import Rodape from './Rodape.vue'

const campos = [
    {
        label: 'Telefone (WhatsApp)',
        valor: '(81) 98878-0290',
        href: 'https://wa.me/5581988780290',
    },
    {
        label: 'E-mail',
        valor: 'contatomh11@gmail.com',
        href: 'mailto:contatomh11@gmail.com',
    },
    {
        label: 'Endereço',
        valor: 'Cohab / Pernambuco',
    },
]

const redes = [
    { nome: 'Instagram', href: 'https://www.instagram.com/' },
    { nome: 'Facebook', href: 'https://www.facebook.com/' },
]

</script>

<template>
    <section id="sobre" class="sobre-contato">
        <div class="conteudo">
            <header class="apresentacao">
                <h2 class="apresentacao-titulo">Sua aparência é nosso foco!</h2>
                <p class="apresentacao-subtitulo">
                    Somos a Barbearia Rei da Navalha — um espaço pensado para corte, barba e atendimento
                    com <span class="destaque">foco total na sua aparência.</span>
                </p>
            </header>

            <div class="colunas">
                <!-- ============ coluna da esquerda ============ -->
                <div class="sobre">
                    <h3 class="coluna-titulo">Sobre nós</h3>

                    <div class="sobre-logo">
                        <span class="sobre-linha"></span>
                        <!-- coloque aqui a logo -->
                        <!-- <img class="sobre-logo-img" src="../assets/logo-mini.png" alt="" /> -->
                        <img src="../assets/Logotipo.png" alt="logo" class="sobre-logo-img">
                        <span class="sobre-linha"></span>
                    </div>

                    <div class="sobre-bloco">
                        <h4 class="sobre-nome">Rei da Navalha</h4>
                        <p class="sobre-sub">Barbearia</p>
                        <p class="sobre-texto">
                            Especialistas em corte e barba, com dedicação total à sua aparência. Cada cliente
                            merece o melhor — e é isso que entregamos, com precisão e respeito.
                        </p>
                    </div>

                    <div class="sobre-mini">
                        <span class="sobre-divisor"></span>
                        <h4 class="sobre-mini-titulo">Sua aparência é nosso foco!</h4>
                        <p class="sobre-texto">
                            Nossa filosofia busca preservar a sua identidade em primeiro lugar, buscando sempre
                            entender a imagem e a vibe que você quer passar para todos que estão ao seu redor.
                        </p>
                    </div>
                    <!-- novo: botão e horário vieram da coluna da direita -->
                    <div class="sobre-agendar">
                        <BotaoAgendar />


                    </div>
                </div>

                <!-- ============ coluna da direita ============ -->
                <div id="contato" class="contato">
                    <h3 class="coluna-titulo">Contatos</h3>

                    <div class="contato-caixa">
                        <div class="contato-campos">
                            <CampoContato v-for="campo in campos" :key="campo.label" v-bind="campo" />

                            <div class="redes">
                                <span class="redes-label">Redes sociais</span>

                                <div class="redes-botoes">
                                    <a v-for="rede in redes" :key="rede.nome" :href="rede.href" class="rede"
                                        target="_blank" rel="noopener">
                                        {{ rede.nome }}
                                    </a>
                                </div>
                            </div>
                        </div>
                        <div class="funcionamento">
                            <span class="funcionamento-label">Horário de funcionamento</span>
                            <span class="funcionamento-texto">Segunda a domingo — 08h às 18h</span>
                        </div>


                    </div>
                </div>
            </div>
        </div>
    </section>
    <Rodape />
</template>

<style scoped>
.sobre-contato {
    --zoom: 0.85;
    /* escala da seção: 1 = tamanho do design, menor = mais compacta */
    --altura-navbar: 85px;
    /* altura da sua navbar: meça no DevTools e ajuste */
    --margem-interna: calc(var(--margem-lateral) / var(--zoom));

    zoom: var(--zoom);
    display: flex;
    width: 100%;
    min-height: calc(100dvh / var(--zoom));
    flex-direction: column;
    background: #0f0f0f;
}

.conteudo {
    display: flex;
    flex: 1 0 0;
    padding: calc(var(--altura-navbar) / var(--zoom) + 1.5rem) var(--margem-interna) 2.5rem;
    box-sizing: border-box;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    /* em telas altas, o conteúdo fica no meio do espaço livre */
    gap: 3.5rem;
    background:
        linear-gradient(0deg, rgba(0, 0, 0, 0.38) 0%, rgba(0, 0, 0, 0.38) 100%),
        url('src/assets/imagens/texturaservicos.png') center / cover no-repeat,
        #1c1c1c;
}

/* ---------- apresentação ---------- */
.apresentacao {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 1.125rem;
    align-self: stretch;
}

.apresentacao-titulo {
    margin: 0;
    align-self: stretch;
    color: rgba(255, 255, 255, 0.78);
    text-align: center;
    font-family: 'Bebas Neue', sans-serif;
    font-size: 4rem;
    font-weight: 400;
    line-height: normal;
    letter-spacing: 0.36rem;
    text-transform: uppercase;
}

.apresentacao-subtitulo {
    width: 53.75rem;
    max-width: 100%;
    margin: 0;
    color: rgba(255, 255, 255, 0.67);
    text-align: center;
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1.75rem;
    font-weight: 400;
    line-height: 115%;
    text-transform: uppercase;
}

.destaque {
    color: #f57d30;
}

/* ---------- duas colunas ---------- */
.colunas {
    display: flex;
    align-items: flex-start;
    gap: 3rem;
    align-self: stretch;
}

.coluna-titulo {
    margin: 0;
    color: rgba(255, 255, 255, 0.85);
    font-family: 'Bebas Neue', sans-serif;
    font-size: 2rem;
    font-weight: 400;
    line-height: normal;
    letter-spacing: 0.18rem;
    text-transform: uppercase;
}

/* ---------- coluna da esquerda ---------- */
.sobre {
    display: flex;
    width: 23.75rem;
    height: 100%;
    flex-shrink: 0;
    flex-direction: column;
    align-items: flex-start;
    gap: 1.75rem;
    justify-content: space-around;
}

.sobre-logo {
    display: flex;
    align-items: center;
    gap: 2rem;
}

.sobre-linha {
    width: 4.3rem;
    /* estimado pela imagem */
    height: 2px;
    background: #d55b0e;
}

.sobre-logo-img {
    width: 3rem;
    height: 2.8125rem;
    object-fit: cover;
}

.sobre-bloco {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    gap: 0.375rem;
    align-self: stretch;
}

.sobre-nome {
    margin: 0;
    color: #d55b0e;
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1.75rem;
    font-weight: 400;
    line-height: normal;
    letter-spacing: 0.105rem;
    text-transform: uppercase;
}

.sobre-sub {
    margin: 0;
    color: rgba(255, 255, 255, 0.5);
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1rem;
    font-weight: 400;
    line-height: normal;
    letter-spacing: 0.09rem;
    text-transform: uppercase;
}

.sobre-texto {
    margin: 0;
    align-self: stretch;
    color: rgba(255, 255, 255, 0.67);
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1.0625rem;
    font-weight: 400;
    line-height: 150%;
    letter-spacing: 0.031875rem;
    text-transform: uppercase;
}

.sobre-mini {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    align-self: stretch;
}

.sobre-divisor {
    align-self: stretch;
    height: 1px;
    opacity: 0.4;
    background: #d55b0e;
}

.sobre-mini-titulo {
    display: flex;
    margin: 0;
    padding-top: 0.875rem;
    padding-bottom: 0.375rem;
    align-self: stretch;
    color: #d55b0e;
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1.25rem;
    font-weight: 400;
    line-height: normal;
    letter-spacing: 0.1125rem;
    text-transform: uppercase;
}

/* ---------- coluna da direita ---------- */
.contato {
    display: flex;
    min-width: 0;
    flex: 1 0 0;
    flex-direction: column;
    align-items: flex-start;
    gap: 1.5rem;
    scroll-margin-top: 7rem;
    /* o título não fica escondido atrás da navbar ao clicar no link */
    background: linear-gradient(90deg, rgba(212, 91, 14, 0.04) 0%, rgba(95, 37, 0, 0.16) 100%);
}


.contato-caixa {
    position: relative;
    display: flex;
    padding: 1.5rem;
    flex-direction: column;
    align-items: flex-start;
    gap: 1.25rem;
    align-self: stretch;
    box-sizing: border-box;
    border-radius: 1.5rem;
    border: 2px solid rgba(249, 249, 249, 0.43);
    background: rgba(0, 0, 0, 0.5);
}


.contato-campos {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    gap: 1.125rem;
    align-self: stretch;
}

/* ---------- redes sociais (o frame sem cantos arredondados) ---------- */
.redes {
    display: flex;
    padding: 0.375rem 0.5rem;
    flex-direction: column;
    align-items: flex-start;
    gap: 0.5rem;
    align-self: stretch;
    box-sizing: border-box;
    border: 1px solid rgba(212, 91, 14, 0.68);
}

.redes-label {
    color: rgb(255, 255, 255);
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1.125rem;
    font-weight: 400;
    line-height: normal;
    letter-spacing: 0.10125rem;
    text-transform: uppercase;
}

.redes-botoes {
    
    display: flex;
    align-items: flex-start;
    gap: 0.75rem;
    align-self: stretch;
}

.rede {
    display: flex;
    height: 3.5rem;
    flex: 1 0 0;
    justify-content: center;
    align-items: center;
    box-sizing: border-box;
    border-radius: 0.75rem;
    /* estimado pela imagem */
    border: 1px solid rgba(255, 255, 255, 0.1);
    background: rgba(0, 0, 0, 0.4);
    color: rgba(255, 255, 255, 0.67);
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1.375rem;
    font-weight: 400;
    line-height: normal;
    letter-spacing: 0.12375rem;
    text-transform: uppercase;
    text-decoration: none;
    transition:
        border-color 0.3s ease,
        color 0.3s ease,
        background-color 0.3s ease;

    background-color: #d55a0e8a;
}

.rede:hover {
    border-color: rgba(212, 91, 14, 0.68);
    color: #fff;
    background-color: #d55a0eb5;
}

.rede:active {
    background-color: rgba(212, 91, 14, 0.68);
    color: #fff;
}

/* ---------- botão + horário ---------- */
/* ---------- botão + horário (agora na coluna da esquerda) ---------- */
.sobre-agendar {
    display: flex;
    margin-top: 0.5rem;
    /* respiro extra depois do texto */
    flex-direction: column;
    align-items: flex-start;
    gap: 1rem;
}

.funcionamento {
  display: flex;
  padding: 0 0.5rem;           /* novo: alinha com o texto dos campos */
  flex-direction: column;
  gap: 0.25rem;
}
.funcionamento-label,
.funcionamento-texto {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1.125rem;
    font-weight: 400;
    line-height: normal;
    letter-spacing: 0.10125rem;
    text-transform: uppercase;
}

.funcionamento-label {
    color: rgba(255, 255, 255, 0.85);
}

.funcionamento-texto {
    color: rgba(255, 255, 255, 0.67);
}

/* ---------- tablet e celular ---------- */
@media (max-width: 1024px) {

    .sobre-contato {
        --zoom: 1;
    }

    .apresentacao-titulo {
        font-size: clamp(2.25rem, 9vw, 4rem);
        letter-spacing: 0.1em;
    }

    .apresentacao-subtitulo {
        font-size: clamp(1.25rem, 4.5vw, 1.75rem);
    }

    .colunas {
        flex-direction: column;
        gap: 2.5rem;
    }

    .sobre,
    .contato {
        width: 100%;
        flex: none;
    }

    .contato-caixa::before {
        animation: none;
    }

}
</style>