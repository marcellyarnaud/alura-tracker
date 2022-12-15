<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <Cronometro_name :tempoEmSegundos="tempoEmSegundos" />
    <button class="button" @click="iniciar" :disabled="cronometroRodando">
      <span class="icon">
        <i class="fas fa-play"></i>
      </span>
      <span>play</span>
    </button>
    <button class="button" @click="finalizar" :disabled="!cronometroRodando">
      <span class="icon">
        <i class="fas fa-stop"></i>
      </span>
      <span>stop</span>
    </button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Cronometro_name from './Cronometro_name.vue'

export default defineComponent({
  name: "Temporizador_name",
  emits: ['aoTemporizadorFinalizado'],
  components:{
    Cronometro_name
  },
  data(){
    return {
      tempoEmSegundos: 0,
      Cronometro_name: 0,
      cronometroRodando: false
    }
  }, 
  methods:{
    iniciar (){
      ///começar a contagem 
      this.cronometroRodando = true
      this.Cronometro_name= setInterval(()=> {
        this.tempoEmSegundos += 1
      },1000)
    },
    finalizar(){
      this.cronometroRodando = false
      clearInterval(this.Cronometro_name)
      this.$emit ('aoTemporizadorFinalizado', this.tempoEmSegundos)
      this.tempoEmSegundos = 0
    }
  }
});
</script>