<script setup>
import { ref } from 'vue'

const menuAberto = ref(false)

const carros = [
  {
    nome: 'Ford Galaxie 500',
    tipo: 'Elegância que atravessa gerações',
    imagem: 'public/carros/imgs/WhatsApp Image 2026-10-13 at 15.08.56 (1).jpeg',
    alt: 'Ford Galaxie 500 clássico'
  },
  {
    nome: 'Chevrolet Pick-up C-10',
    tipo: 'Charme rústico com muita personalidade',
    imagem: 'public/carros/imgs/WhatsApp Image 2026-10-13 at 15.08.56.jpeg',
    alt: 'Chevrolet Pick-up C-10 clássica'
  },
  {
    nome: 'Chevrolet Blazer',
    tipo: 'Elegância clássica e momentos que ficam para sempre',
    imagem: 'public/carros/imgs/WhatsApp Image 2026-10-13 at 15.08.57.jpeg',
    alt: 'Chevrolet Pick-up C-10 clássica'
  }
]

function fecharMenu() {
  menuAberto.value = false
}

function pedirOrcamento(nomeCarro) {
  const telefone = '5547999314278'
  const mensagem = `Olá! Gostaria de saber mais sobre o aluguel do ${nomeCarro} para um casamento.`
  window.open(`https://wa.me/${telefone}?text=${encodeURIComponent(mensagem)}`, '_blank')
}
</script>

<template>
  <header class="topo">
    <a class="marca" href="#inicio" @click="fecharMenu">
      <span class="marca-simbolo">✦</span>
      <span>CLÁSSICOS <em>DO AMOR</em></span>
    </a>

    <button class="menu-botao" @click="menuAberto = !menuAberto" aria-label="Abrir menu">☰</button>

    <nav :class="{ aberto: menuAberto }">
      <a href="#inicio" @click="fecharMenu">Início</a>
      <a href="#carros" @click="fecharMenu">Nossos carros</a>
      <a href="#historia" @click="fecharMenu">Nossa história</a>
      <a class="nav-contato" href="#contato" @click="fecharMenu">Fale conosco</a>
    </nav>
  </header>

  <main>
    <section id="inicio" class="hero">
      <div class="hero-fundo"></div>
      <div class="hero-conteudo">
        <p class="sobretitulo">UM TOQUE DE HISTÓRIA NO SEU GRANDE DIA</p>
        <h1>O amor merece<br /><span>uma chegada inesquecível.</span></h1>
        <p class="hero-texto">Carros clássicos para transformar o caminho até o altar em uma lembrança para a vida toda.</p>
        <a class="botao botao-dourado" href="#carros">Conheça nossos clássicos <span>→</span></a>
      </div>
      <div class="hero-legenda"><span>ESTILO ATEMPORAL</span><span>♥</span><span>MEMÓRIAS ETERNAS</span></div>
    </section>

    <section class="introducao" id="historia">
      <p class="sobretitulo verde">MAIS QUE UM CARRO, PARTE DA SUA HISTÓRIA</p>
      <h2>O charme do passado.<br /><span>A emoção de um novo começo.</span></h2>
      <p class="introducao-texto">Acreditamos que os detalhes fazem toda a diferença. Por isso, nossos carros clássicos ajudam a deixar o seu casamento ainda mais especial, com beleza, personalidade e muito romantismo.</p>
      <div class="linha-decorativa"><span>✦</span></div>
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
        <article class="carro-card" v-for="(carro, index) in carros" :key="carro.nome">
          <div class="carro-foto">
            <img :src="carro.imagem" :alt="carro.alt" />
            <span class="numero-carro">0{{ index + 1 }}</span>
          </div>
          <div class="carro-info">
            <p class="carro-tipo">{{ carro.tipo }}</p>
            <h3>{{ carro.nome }}</h3>
            <p class="carro-descricao">Uma escolha cheia de personalidade para fotos incríveis e uma chegada marcante.</p>
            <button class="link-orcamento" @click="pedirOrcamento(carro.nome)">Consultar disponibilidade <span>↗</span></button>
          </div>
        </article>
      </div>
      <p class="aviso-fotos">Adicione suas fotos reais na pasta <strong>public/carros</strong> usando os nomes indicados no projeto.</p>
    </section>

    <section class="frase-destaque">
      <span class="aspas">“</span>
      <p>Alguns momentos passam.<br />Outros se tornam <em>eternos.</em></p>
      <span class="tracinho"></span>
      <small>CLÁSSICOS DO AMOR</small>
    </section>

    <section id="contato" class="contato">
      <div>
        <p class="sobretitulo">VAMOS FAZER PARTE DESSE MOMENTO?</p>
        <h2>Seu grande dia<br /><span>começa aqui.</span></h2>
        <p>Converse com a gente e descubra qual clássico vai acompanhar sua história.</p>
      </div>
      <div class="contato-acoes">
        <a class="botao botao-dourado" href="https://wa.me/5547999314278" target="_blank" rel="noreferrer">Falar pelo WhatsApp ↗</a>
        <a href="https://www.instagram.com/" target="_blank" rel="noreferrer">Instagram ↗</a>
        <a href="https://www.facebook.com/" target="_blank" rel="noreferrer">Facebook ↗</a>
      </div>
    </section>
  </main>

  <footer>
    <a class="marca marca-rodape" href="#inicio"><span class="marca-simbolo">✦</span><span>CLÁSSICOS <em>DO AMOR</em></span></a>
    <p>O charme dos clássicos para celebrar o amor.</p>
    <span class="copyright">© 2026 Clássicos do Amor</span>
  </footer>
</template>
