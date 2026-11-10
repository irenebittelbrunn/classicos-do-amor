
<script setup>
import { ref } from "vue";

const menuAberto = ref(false);

const carros = ref([
  {
    nome: "Ford Galaxie 500",
    tipo: "Elegância que atravessa gerações",
    midias: [
      { tipo: "imagem", src: "/carros/imgs/5001.jpeg" },
      { tipo: "imagem", src: "/carros/imgs/5002.jpeg" },
      { tipo: "imagem", src: "/carros/imgs/5004.jpeg" },
      { tipo: "imagem", src: "/carros/imgs/5005.jpeg" },
      { tipo: "imagem", src: "/carros/imgs/5006.jpeg" },
      { tipo: "video", src: "/carros/imgs/500v.mp4" },
    ],
    alt: "Ford Galaxie 500 clássico",
    midiaAtual: 0,
  },
  {
    nome: "Chevrolet Pick-up C-10",
    tipo: "Charme rústico com muita personalidade",
    midias: [
      { tipo: "imagem", src: "/carros/imgs/c102.jpeg" },
      { tipo: "imagem", src: "/carros/imgs/c101.jpeg" },
      { tipo: "imagem", src: "/carros/imgs/c103.jpeg" },
      { tipo: "imagem", src: "/carros/imgs/c104.jpeg" },
      { tipo: "imagem", src: "/carros/imgs/c105.jpeg" },
      { tipo: "imagem", src: "/carros/imgs/c106.jpeg" },
      { tipo: "imagem", src: "/carros/imgs/c108.jpeg" },
      { tipo: "imagem", src: "/carros/imgs/c109.jpeg" },
      { tipo: "video", src: "/carros/imgs/c10v.mp4" },
    ],
    alt: "Chevrolet Pick-up C-10 clássica",
    midiaAtual: 0,
  },
  {
    nome: "Chevrolet Blazer",
    tipo: "Elegância clássica e momentos que ficam para sempre",
    midias: [
      { tipo: "imagem", src: "/carros/imgs/blazer4.jpeg" },
      { tipo: "imagem", src: "/carros/imgs/blazer2.jpeg" },
      { tipo: "imagem", src: "/carros/imgs/blazer3.jpeg" },
      { tipo: "imagem", src: "/carros/imgs/blazer1.jpeg" },
      { tipo: "video", src: "/carros/imgs/blazerv.mp4" },
    ],
    alt: "Chevrolet Blazer clássica",
    midiaAtual: 0,
  },
]);

function fecharMenu() {
  menuAberto.value = false;
}

function proximo(index) {
  const carro = carros.value[index];
  carro.midiaAtual = (carro.midiaAtual + 1) % carro.midias.length;
}

function anterior(index) {
  const carro = carros.value[index];
  carro.midiaAtual =
    (carro.midiaAtual - 1 + carro.midias.length) % carro.midias.length;
}

function selecionarImagem(index, imagem) {
  carros.value[index].midiaAtual = imagem;
}

function pedirOrcamento(nomeCarro) {
  const telefone = "5547992801143";
  const mensagem = `Olá! Gostaria de saber mais sobre o aluguel do ${nomeCarro} para um casamento.`;

  window.open(
    `https://wa.me/${telefone}?text=${encodeURIComponent(mensagem)}`,
    "_blank",
  );
}

const formContato = ref({
  nome: '',
  email: '',
  telefone: '',
  evento: '',
  data: '',
  local: '',
  mensagem: ''
})

function enviarContato() {
  const dados = formContato.value

  const texto = `
Olá! Vim pelo site Clássicos do Amor e gostaria de solicitar um orçamento.

Nome: ${dados.nome}
E-mail: ${dados.email}
WhatsApp: ${dados.telefone}
Evento: ${dados.evento}
Data: ${dados.data || 'Não informada'}
Local: ${dados.local || 'Não informado'}

Mensagem: ${dados.mensagem || 'Nenhuma mensagem adicional.'}
  `

  const numero = '5547992801143'

  const link = `https://wa.me/${numero}?text=${encodeURIComponent(texto)}`

  window.open(link, '_blank')
}

</script>

<template>
  <header class="topo">
    <a class="marca" href="#inicio" @click="fecharMenu">
      <span class="marca-simbolo">✦</span>
      <span>CLÁSSICOS <em>DO AMOR</em></span>
      <p>Joinville(SC)</p>
    </a>

    <button
      class="menu-botao"
      @click="menuAberto = !menuAberto"
      aria-label="Abrir menu"
    >
      ☰
    </button>

    <nav :class="{ aberto: menuAberto }">
      <a href="#inicio" @click="fecharMenu">Início</a>
      <a href="#carros" @click="fecharMenu">Nossos carros</a>
      <a href="#historia" @click="fecharMenu">Nossa história</a>
      <a href="#duvidas">Dúvidas frequentes</a>
      <a class="nav-contato" href="#contato" @click="fecharMenu">
        Fale conosco
      </a>
    </nav>
  </header>

  <main>
    <section id="inicio" class="hero">
      <div class="hero-fundo"></div>

      <div class="hero-conteudo">
        <p class="sobretitulo">
          UM TOQUE DE HISTÓRIA NO SEU GRANDE DIA
        </p>

        <h1>
          O amor merece<br />
          <span>uma chegada inesquecível.</span>
        </h1>

        <p class="hero-texto">
          Carros clássicos para transformar o caminho até o altar em uma
          lembrança para a vida toda.
        </p>

        <a class="botao botao-dourado" href="#carros">
          Conheça nossos clássicos <span>→</span>
        </a>
      </div>

      <div class="hero-legenda">
        <span>ESTILO ATEMPORAL</span>
        <span>♥</span>
        <span>MEMÓRIAS ETERNAS</span>
      </div>
    </section>

    <section class="introducao" id="historia">
      <p class="sobretitulo verde">
        MAIS QUE UM CARRO, PARTE DA SUA HISTÓRIA
      </p>

      <h2>
        O charme do passado.<br />
        <span>A emoção de um novo começo.</span>
      </h2>

      <p class="introducao-texto">
        Acreditamos que os detalhes fazem toda a diferença. Por isso, nossos
        carros clássicos ajudam a deixar o seu casamento ainda mais especial,
        com beleza, personalidade e muito romantismo.
      </p>

      <div class="linha-decorativa">
        <span>✦</span>
      </div>
    </section>

    <section id="carros" class="secao-carros">
      <div class="secao-titulo">
        <div>
          <p class="sobretitulo verde">NOSSA COLEÇÃO</p>
          <h2>Clássicos que <span>encantam</span></h2>
        </div>

        <p>Escolha o carro que combina com a sua história.</p>
      </div>

      <div class="carros-lista">
        <article
          class="carro-card"
          v-for="(carro, index) in carros"
          :key="carro.nome"
        >
          <div class="carro-foto">
            <template v-if="carro.midias[carro.midiaAtual].tipo === 'video'">
              <video
                :key="carro.midiaAtual"
                :src="carro.midias[carro.midiaAtual].src"
                controls
                playsinline
              ></video>
            </template>

            <template v-else>
              <img
                :key="carro.midiaAtual"
                :src="carro.midias[carro.midiaAtual].src"
                :alt="carro.alt"
              />
            </template>

            <button
              class="seta-carrossel esquerda"
              @click="anterior(index)"
              aria-label="Mídia anterior"
            >
              ❮
            </button>

            <button
              class="seta-carrossel direita"
              @click="proximo(index)"
              aria-label="Próxima mídia"
            >
              ❯
            </button>

            <div class="indicadores">
              <span
                v-for="(midia, i) in carro.midias"
                :key="i"
                :class="{ ativa: carro.midiaAtual === i }"
                @click="selecionarImagem(index, i)"
              ></span>
            </div>

            <span class="numero-carro">
              0{{ index + 1 }}
            </span>
          </div>

          <div class="carro-info">
            <p class="carro-tipo">{{ carro.tipo }}</p>

            <h3>{{ carro.nome }}</h3>

            <p class="carro-descricao">
              Uma escolha cheia de personalidade para fotos incríveis e uma
              chegada marcante.
            </p>

            <button
              class="link-orcamento"
              @click="pedirOrcamento(carro.nome)"
            >
              Consultar disponibilidade <span>↗</span>
            </button>
          </div>
        </article>
      </div>
    </section>

    <section class="frase-destaque">
      <span class="aspas">“</span>

      <p>
        Alguns momentos passam.<br />
        Outros se tornam <em>eternos.</em>
      </p>

      <span class="tracinho"></span>

      <small>CLÁSSICOS DO AMOR</small>
    </section>

<section id="duvidas" class="duvidas">

  <div class="duvidas-container">

    <div class="duvidas-lista">
      <h1>Dúvidas Frequentes</h1>

      <details class="faq-item">
        <summary>Quais tipos de eventos vocês atendem?</summary>
        <p>Atendemos casamentos, festas de 15 anos,
        formaturas, aniversários, ensaios fotográficos
        e outras ocasiões especiais.</p>
      </details>

      <details class="faq-item">
        <summary>Como faço para reservar um veículo?</summary>
        <p>Entre em contato pelo WhatsApp ou formulário,
        informe a data e o tipo de evento e consulte
        a disponibilidade do veículo desejado.</p>
      </details>

      <details class="faq-item">
        <summary>Com quanto tempo de antecedência devo reservar?</summary>
        <p>Recomendamos entrar em contato com antecedência
        para aumentar as chances de encontrar o veículo
        disponível na data desejada.</p>
      </details>

      <details class="faq-item">
        <summary>Posso escolher o carro que quero?</summary>
        <p>Sim! Você pode conhecer nossos veículos e
        escolher seu preferido, conforme disponibilidade.</p>
      </details>

      <details class="faq-item">
        <summary>Os carros podem ser decorados?</summary>
        <p>Consulte as possibilidades de decoração e
        personalização durante o orçamento.</p>
      </details>

      <details class="faq-item">
        <summary>Vocês atendem outras cidades?</summary>
        <p>Consulte nossa disponibilidade de atendimento
        para sua cidade e as condições de deslocamento.</p>
      </details>

      <details class="faq-item">
        <summary>Como posso solicitar um orçamento?</summary>
        <p>Você pode preencher nosso formulário de contato
        ou falar diretamente pelo WhatsApp.</p>
      </details>

    </div>

    <div class="duvidas-texto">
      <span>ESTAMOS AQUI PARA AJUDAR</span>

      <h2>Ficou com alguma dúvida?</h2>

      <p>
        Queremos que sua experiência seja especial
        desde o primeiro contato. Confira nossas
        respostas ou fale diretamente conosco.
      </p>

      <a href="#contato" class="duvidas-botao">
        Fale conosco
      </a>

      <div class="frase-duvidas">
        "Cada detalhe merece fazer parte de uma
        lembrança inesquecível."
      </div>
    </div>

  </div>

</section>


<section id="contato" class="contato">
  <div class="contato-titulo">
    <span>CLÁSSICOS DO AMOR</span>
    <h2>Vamos fazer parte da sua história?</h2>
    <p>
      Seja qual for a ocasião, temos um carro especial
      para tornar seu momento ainda mais inesquecível.
    </p>
  </div>

  <form class="formulario" @submit.prevent="enviarContato">

    <div class="campo">
      <label>Nome completo</label>
      <input
        v-model="formContato.nome"
        type="text"
        placeholder="Digite seu nome"
        required
      >
    </div>

    <div class="campo">
      <label>E-mail</label>
      <input
        v-model="formContato.email"
        type="email"
        placeholder="seuemail@email.com"
      >
    </div>

    <div class="campo">
      <label>WhatsApp</label>
      <input
        v-model="formContato.telefone"
        type="tel"
        placeholder="(47) 99999-9999"
        required
      >
    </div>

    <div class="campo">
      <label>Tipo de evento</label>
      <select v-model="formContato.evento" required>
        <option value="">Selecione seu evento</option>
        <option>Casamento</option>
        <option>Festa de 15 anos / Debutante</option>
        <option>Formatura</option>
        <option>Ensaio fotográfico</option>
        <option>Aniversário</option>
        <option>Bodas</option>
        <option>Outro evento</option>
      </select>
    </div>

    <div class="campo">
      <label>Data do evento</label>
      <input
        v-model="formContato.data"
        type="date"
      >
    </div>

    <div class="campo">
      <label>Local do evento</label>
      <input
        v-model="formContato.local"
        type="text"
        placeholder="Cidade ou endereço"
      >
    </div>

    <div class="campo campo-mensagem">
      <label>Conte mais sobre o que procura</label>
      <textarea
        v-model="formContato.mensagem"
        placeholder="Conte um pouco sobre seu evento..."
        rows="5"
      ></textarea>
    </div>

    <button type="submit" class="botao-enviar">
      Solicitar orçamento
    </button>

  </form>
</section>


    <section id="contato" class="contato">
      <div>
        <p class="sobretitulo">
          VAMOS FAZER PARTE DESSE MOMENTO?
        </p>

        <h2>
          Seu grande dia<br />
          <span>começa aqui.</span>
          <br />Joinville/SC📍
        </h2>

        <p>
          Converse com a gente e descubra qual clássico vai acompanhar sua
          história.
        </p>
      </div>

      <div class="contato-acoes">
        <a
          class="botao botao-dourado"
          href="https://wa.me/5547992801143"
          target="_blank"
          rel="noreferrer"
        >
          Falar pelo WhatsApp ↗
        </a>

        <a
          href="https://www.instagram.com/classicosdoamor/"
          target="_blank"
          rel="noreferrer"
        >
          Instagram ↗
        </a>

        <a
          href="https://www.facebook.com/profile.php?id=61595360321247"
          target="_blank"
          rel="noreferrer"
        >
          Facebook ↗
        </a>
      </div>
    </section>
  </main>

  <footer>
    <a class="marca marca-rodape" href="#inicio">
      <span class="marca-simbolo">✦</span>
      <span>CLÁSSICOS <em>DO AMOR</em></span>
    </a>

    <p>O charme dos clássicos para celebrar o amor.</p>

    <span class="copyright">
      © 2026 Clássicos do Amor <br />
      Criado e Desenvolvido por Irene Bittelbrunn.
    </span>
  </footer>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@500;600;700&display=swap');
@keyframes aparecerFoto {
  from {
    opacity: 0.5;
  }

  to {
    opacity: 1;
  }
}

.seta-carrossel {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  width: 40px;
  height: 40px;
  border: none;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.88);
  color: #333;
  font-size: 16px;
  cursor: pointer;
  z-index: 2;
  transition: 0.3s;
}

.seta-carrossel:hover {
  background: #9a7541;
  color: white;
}

.seta-carrossel.esquerda {
  left: 12px;
}

.seta-carrossel.direita {
  right: 12px;
}

.indicadores {
  position: absolute;
  bottom: 15px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  align-items: center;
  gap: 8px;
  z-index: 2;
}

.indicadores span {
  width: 9px;
  height: 9px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.75);
  cursor: pointer;
  transition: 0.3s;
}

.indicadores span.ativa {
  background: #9a7541;
  width: 22px;
  border-radius: 10px;
}

@media (max-width: 600px) {
  .seta-carrossel {
    width: 34px;
    height: 34px;
  }
}

@media (max-width: 600px) {
  .carro-foto {
    height: 280px;
  }
}

.carros-lista .carro-card .carro-foto {
  position: relative;
  width: 100%;
  height: 550px !important;
  min-height: 550px !important;
  aspect-ratio: auto !important;
  overflow: hidden;
}

.carros-lista .carro-card .carro-foto img {
  width: 100%;
  height: 100% !important;
  object-fit: contain;
  display: block;
}

@media (max-width: 600px) {
  .carros-lista .carro-card .carro-foto {
    height: 350px !important;
    min-height: 350px !important;
  }
}

.carro-foto img,
.carro-foto video {
  width: 100%;
  height: 100%;
  object-fit: contain;
  display: block;
}

.contato {
  background: #f3eee6;
  padding: 80px 20px;
  color: #40352b;
}

.contato-titulo {
  text-align: center;
  max-width: 650px;
  margin: 0 auto 40px;
}

.contato-titulo span {
  color: #a88955;
  letter-spacing: 3px;
  font-size: 13px;
}

.contato-titulo h2 {
  font-size: 32px;
  margin: 15px 0;
}

.contato-titulo p {
  color: #75695e;
  line-height: 1.7;
}

.formulario {
  max-width: 750px;
  margin: auto;
  background: #fff;
  padding: 35px;
  border-radius: 8px;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 22px;
  box-shadow: 0 5px 20px rgba(0,0,0,0.05);
}

.campo {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.campo label {
  font-size: 14px;
  font-weight: 600;
}

.campo input,
.campo select,
.campo textarea {
  padding: 13px;
  border: 1px solid #ddd4c8;
  border-radius: 5px;
  font-family: inherit;
  font-size: 14px;
  background: #fff;
  outline: none;
}

.campo input:focus,
.campo select:focus,
.campo textarea:focus {
  border-color: #a88955;
}

.campo-mensagem {
  grid-column: 1 / -1;
}

.botao-enviar {
  grid-column: 1 / -1;
  padding: 15px;
  background: #756044;
  color: white;
  border: none;
  border-radius: 5px;
  font-size: 15px;
  cursor: pointer;
  transition: 0.3s;
}

.botao-enviar:hover {
  background: #a88955;
}

@media (max-width: 600px) {
  .formulario {
    grid-template-columns: 1fr;
    padding: 22px;
  }

  .campo-mensagem,
  .botao-enviar {
    grid-column: 1;
  }

  .contato-titulo h2 {
    font-size: 26px;
  }
}
.contato-titulo {
  width: 100%;
  max-width: 650px;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  margin: 0 auto;
}

.contato-titulo h2 {
  width: 100%;
  text-align: center;
}

.contato-titulo p {
  width: 100%;
  max-width: 520px;
  text-align: center;
  margin: 15px auto 0;
  line-height: 1.8;
}
.formulario {
  width: 100%;
  max-width: 850px;
  box-sizing: border-box;
  padding: 45px;
  gap: 25px;
  border-radius: 10px;
}

.campo input,
.campo select {
  min-height: 50px;
  font-size: 15px;
  padding: 15px;
}

.campo textarea {
  min-height: 140px;
  font-size: 15px;
  padding: 15px;
}

.campo label {
  font-size: 15px;
}

.botao-enviar {
  min-height: 52px;
  font-size: 16px;
}
@media (max-width: 600px) {
  .formulario {
    padding: 22px;
    gap: 18px;
  }

  .contato {
    padding: 55px 18px;
  }

  .contato-titulo h2 {
    font-size: 27px;
  }
}



.duvidas {
  background: #173b31;
  padding: 90px 20px;
  color: #f3eee6;
}

.duvidas-container {
  max-width: 1100px;
  margin: auto;
  display: grid;
  grid-template-columns: 1.2fr 0.8fr;
  gap: 65px;
  align-items: center;
}

/* PERGUNTAS À ESQUERDA */

.duvidas-lista {
  width: 100%;
}

.faq-item {
  background: #f3eee6;
  margin-bottom: 13px;
  padding: 22px 25px;
  border-radius: 5px;
  border: 1px solid #d9cbb8;
  transition: 0.3s;
}

.faq-item:hover {
  background: #fff;
  transform: translateX(4px);
}

.faq-item summary {
  color: #203d32;
  font-size: 15px;
  font-weight: 600;
  cursor: pointer;
  list-style: none;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 15px;
}

.faq-item summary::-webkit-details-marker {
  display: none;
}

.faq-item summary::after {
  content: "+";
  color: #a88955;
  font-size: 23px;
  font-weight: 400;
}

.faq-item[open] summary::after {
  content: "−";
}

.faq-item p {
  color: #75695e;
  font-size: 14px;
  line-height: 1.8;
  margin: 18px 0 0;
  padding-top: 15px;
  border-top: 1px solid #ddd2c4;
}

/* TEXTO À DIREITA */

.duvidas-texto {
  padding: 20px 0;
}

.duvidas-texto span {
  color: #c5a775;
  font-size: 12px;
  letter-spacing: 3px;
}

.duvidas-texto h2 {
  font-size: 38px;
  font-weight: 500;
  line-height: 1.2;
  margin: 20px 0;
  color: #f3eee6;
}

.duvidas-texto p {
  color: #d4d1c7;
  font-size: 16px;
  line-height: 1.9;
  margin-bottom: 30px;
}

.duvidas-botao {
  display: inline-block;
  background: #a88955;
  color: #fff;
  padding: 14px 28px;
  text-decoration: none;
  border-radius: 4px;
  transition: 0.3s;
}

.duvidas-botao:hover {
  background: #c5a775;
}

.frase-duvidas {
  border-left: 2px solid #a88955;
  padding-left: 18px;
  margin-top: 45px;
  color: #c5a775;
  font-family: Georgia, serif;
  font-style: italic;
  font-size: 18px;
  line-height: 1.6;
}

/* CELULAR */

@media (max-width: 750px) {
  .duvidas {
    padding: 60px 20px;
  }

  .duvidas-container {
    grid-template-columns: 1fr;
    gap: 35px;
  }

  .duvidas-texto {
    grid-row: 1;
    text-align: center;
  }

  .duvidas-texto h2 {
    font-size: 30px;
  }

  .frase-duvidas {
    text-align: left;
  }
}
.duvidas-lista h1 {
  color: #f3eee6;
  font-family: 'Cormorant Garamond', serif;
  font-size: 46px;
  font-weight: 600;
  letter-spacing: 1px;
  margin-bottom: 30px;
  padding-bottom: 15px;
}

.duvidas-lista h1::after {
  content: "";
  display: block;
  width: 75px;
  height: 2px;
  background: #c5a775;
  margin-top: 12px;
}

</style>
