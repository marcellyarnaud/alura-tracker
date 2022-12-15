<template>
  <main class="columns is-gapless is-multiline" :class="{'modo-escuro': modoEscuroAtivo }">
    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema"/>
    </div>
    <div class="column is-three-quarter conteudo">
      <Formulario_name @aoSalvarTarefa_name="salvarTarefa_name"/>
      <div class="lista">
        <Tarefa_name v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
        <Box_name v-if="listaEstaVazia">
          Você não está muito produtivo hoje :(
        </Box_name>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import Box_name from './components/Box_name.vue'
import Formulario_name from './components/Formulario_name.vue'
import Tarefa_name from './components/Tarefa_name.vue'
import ITarefa from './interfaces/ITarefa'


export default defineComponent({
  name: 'App', 
  components:{
    BarraLateral,
    Formulario_name,
    Tarefa_name,
    Box_name
}, 
  data (){
    return {
      tarefas: [] as ITarefa [],
      modoEscuroAtivo: false
    }
  },
  computed:{
    listaEstaVazia (): boolean {
      return this.tarefas.length === 0
    }
  },
  methods:{
    salvarTarefa_name (tarefa: ITarefa){
      this.tarefas.push(tarefa)
    },
    trocarTema (modoEscuroAtivo: boolean){
      this.modoEscuroAtivo = modoEscuroAtivo
    }
  }
});
</script>

<style>

.lista {
  padding: 1.25rem;
}
main  {
  --bg-primario: #fff;
  --texto-primario: #000;
}
main.modo-escuro{
  --bg-primario: #2b2d42;
  --texto-primario: #ddd;
}
.conteudo  {
  background-color: var(--bg-primario);
}
</style>
 