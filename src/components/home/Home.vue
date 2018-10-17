<template>
  <div>
    <h1 class="titulo">{{ titulo }}</h1>

    <input type="search" class="filtro" v-on:input="filtro = $event.target.value" placeholder="Filtre pelo título da foto">

    <ul class="lista-fotos">
      <li class="lista-fotos-item" v-for="item of filtrar" :key="item.id" >
        <painel :titulo="item.titulo">
          <imagem :url="item.url" :titulo="item.titulo"></imagem>
          <meu-button tipo="button" rotulo="Remover" @button-ative="remove()"></meu-button>
        </painel>
      </li>
    </ul>
    
  </div>
</template>

<script>
import Painel from '../shared/painel/Painel.vue';
import Imagem from '../shared/imagem/Imagem.vue';
import Button from '../shared/button/Button.vue'

export default {

  components: {
    'painel': Painel,
    'imagem': Imagem,
    'meu-button': Button
  },

  computed: {
    filtrar() {

      if(this.filtro) {
        let exp = new RegExp(this.filtro.trim(), 'i');
        return this.imagens.filter(imagem => exp.test(imagem.titulo))
      } else {
        return this.imagens;
      }
    }
  },

  data() {
    return {
      titulo: 'Alura',
      imagens: [],
      filtro: ''
    }
  },

  methods: {
    remove() {
      alert('y89dausad')
    }
  },

  created() {
    
    this.$http.get('http://localhost:3000/v1/fotos')
      .then(res => res.json())
      .then(imagens => this.imagens = imagens, err => console.log(err));
  }
}
</script>

<style>

  .titulo {
    text-align: center;
  }

  .lista-fotos {
    list-style: none;
  }

  .lista-fotos .lista-fotos-item {
    display: inline-block;
  }

  .filtro {
    display: block;
    width: 100%;
  }
</style>
