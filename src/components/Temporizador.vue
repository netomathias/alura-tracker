<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
        <Cronometro :tempo-em-segundos="tempoEmSegundos" />
        <BotaoTemporizador icone="fas fa-play" texto="Play" @clicado="iniciar" :desabilitado="cronometroRodando" />
        <BotaoTemporizador icone="fas fa-stop" texto="Stop" @clicado="finalizar" :desabilitado="!cronometroRodando" />
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BotaoTemporizador from './BotaoTemporizador.vue';
import Cronometro from './Cronometro.vue';

export default defineComponent({
    name: "Temporizador",
    emits: ['aoTemporizadorFinalizado'],

    data() {
        return {
            tempoEmSegundos: 0,
            cronometro: 0,
            cronometroRodando: false
        };
    },
    methods: {
        iniciar() {
            this.cronometroRodando = true;
            this.cronometro = setInterval(() => {
                this.tempoEmSegundos += 1;
            }, 1000);
        },
        finalizar() {
            this.cronometroRodando = false;
            clearInterval(this.cronometro);
            this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos);
            this.tempoEmSegundos = 0
        }
    },
    components: { Cronometro, BotaoTemporizador }
})
</script>

<style></style>