
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
</style>
