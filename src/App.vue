<template>
  <main class="columns is-gapless" :class="{'modo-escuro' : modoEscuroAtivo}">
    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema"/>
    </div>

    <div class="column is-three-quarter conteudo">
        <Formulario @aoSalvarTarefa="salvarTarefa"/>

        <div class="lista">
          <Box v-if="listaEstaVazia">
            Você não está muito produtivo hoje! :(
          </Box>
          <Tarefa v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
        </div>
    </div>

  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import Box from './components/Box.vue';
import Formulario from './components/Formulario.vue';
import Tarefa from './components/Tarefa.vue';
import type ITarefa from './interfaces/iTarefas';

export default defineComponent({
  data() {
    return {
      tarefas: [] as unknown as ITarefa[],
      modoEscuroAtivo: false
      }
  },
  computed: {
    listaEstaVazia(): boolean {
      return this.tarefas.length === 0;
    }
  },
  methods: {
    salvarTarefa(tarefa: ITarefa) { 
      this.tarefas.push(tarefa);

    },
    trocarTema(modoEscuro: boolean) {
      this.modoEscuroAtivo = modoEscuro;
    }
  },
  components: {
    BarraLateral,
    Formulario,
    Tarefa,
    Box
},
})
</script>

<style scoped>

.lista {
  padding: 0.5rem;
}

main {
  --bg-primario: #fff;
  --texto-primario: #000;
  --box-primario: #FAF0CA;
  
}

main.modo-escuro {
  --bg-primario: #2b2d42;
  --texto-primario: #fff;
  --box-primario: grey;
}

.conteudo {
  background-color: var(--bg-primario);
}
</style>
