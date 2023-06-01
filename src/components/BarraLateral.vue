<template>
    <header>
        <h1>
            <img src="../assets/logo.svg" alt="">
        </h1>

        <button class="button" @click="alterarTema">{{ textoDoBotao }}</button>
    </header>
</template>

<script lang="ts">
    import { defineComponent } from 'vue';

    export default defineComponent({
        name: 'BarraLateral',
        emits: ['aoTemaAlterado'],
        data() {
            return {
                modoEscuro: false
            }
        },
        computed: {
            textoDoBotao() {
                if (this.modoEscuro) {
                    return 'Desativar modo escuro'
                }

                return 'Ativar modo escuro'
            }
        },
        methods: {
            alterarTema() {
                this.modoEscuro =!this.modoEscuro;
                this.$emit('aoTemaAlterado', this.modoEscuro);
            }
        }
    })
</script>

<style scoped>
    header {
        background: #0d3b66;
        width: 100%;
        height: 100vh;

        padding: 1rem;
        text-align: center;
    }

    img {
        width: 3rem;
        height: 3rem;
    }

    .button {
        background-color: var(--bg-primario);
        color: var(--texto-primario);
        border: var(--bg-primario);
    }

    @media only screen and (max-width: 768px) {
        header {
            padding: 2.5rem;
            height: auto;
        }
    }
</style>