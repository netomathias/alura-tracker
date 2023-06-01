
import Cronometro from './Cronometro.vue';

<template>
    <Box class="box has-text-weight-bold">
        <div>
            {{ tarefa.descricao || 'Tarefa sem descrição'}}
        </div>
        <div>
            <Cronometro :tempo-em-segundos="tarefa.duracaoEmSegundos"/>
        </div>
    </Box>
</template>

<script lang="ts">
import { defineComponent, type PropType } from 'vue';
import type ITarefa from '../interfaces/iTarefas';
import Box from './Box.vue';
import Cronometro from './Cronometro.vue';

export default defineComponent({
    name: 'Tarefa',
    props: {
        tarefa: {
            type: Object as PropType<ITarefa>,
            required: true
        }
    },
    components: {
        Cronometro,
        Box
    },
})
</script>

<style scoped>
    .box {
        display: flex;
        justify-content: space-between;
        align-items: center;

        color: var(--texto-primario);
    }
</style>

