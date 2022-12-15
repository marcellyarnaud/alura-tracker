<template>
  <div class="box formulario_name">
    <div class="columns">
      <div
        class="column is-8"
        role="form"
        aria-label="Formulário para criação de uma nova tarefa"
      >
        <input
          type="text"
          class="input"
          placeholder="Qual tarefa você deseja iniciar?"
          v-model="descricao"
          />
      </div>
      <div class="column">
        <Temporizador_name @aoTemporizadorFinalizado="finalizarTarefa"/>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Temporizador_name from './Temporizador_name.vue'

export default defineComponent({
  name: "Formulario_name",
  emits: ['aoSalvarTarefa_name'],
  components:{
    Temporizador_name
  },
  data(){
    return {
      descricao: ''
    }
  },
  methods: {
    finalizarTarefa (tempoDecorrido: number) : void{
      this.$emit ('aoSalvarTarefa_name', {
         duracaoEmSegundos: tempoDecorrido,
         descricao: this.descricao
      })
      this.descricao = ''
    }
  }
});
</script>
<style>
.formulario_name{
  color: var(--texto-primario);
  background-color: var(--bg-primario  );
}
</style>

