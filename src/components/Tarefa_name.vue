<template>
  <Box_name>
    <div class="columns">
      <div class="column is-7">{{tarefa.descricao || 'Tarefa sem descrição '}}</div>
      <div class="column">
        <Cronometro_name :tempoEmSegundos="tarefa.duracaoEmSegundos"/>
      </div>
    </div>
  </Box_name>
</template>

<script lang="ts">
import { defineComponent, PropType } from "vue";
import Cronometro_name from "./Cronometro_name.vue";
import ITarefa from '../interfaces/ITarefa'
import Box_name from './Box_name.vue'


export default defineComponent({
  name: "Tarefa_name",
  components: {
    Cronometro_name,
    Box_name
  },
  props: { 
    tarefa:{
        type: Object as PropType<ITarefa>,
        required: true
    }
  }
}); 
</script>

<style scoped>
.box{
    background: #fff3ac;
}
</style>