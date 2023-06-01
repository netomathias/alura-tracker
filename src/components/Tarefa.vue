
import Cronometro from './Cronometro.vue';

<template>
    <Box class="box has-text-weight-bold">
        <div class="columns">
            <div class="column is-7">
               {{ tarefa.descricao || 'Tarefa sem descrição'}}
            </div>
            <div class="column">
                <Cronometro :tempo-em-segundos="tarefa.duracaoEmSegundos"/>
            </div>
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

