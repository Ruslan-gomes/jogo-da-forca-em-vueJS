<template>
    <div :class="`final ${etapa}`">
        {{texto}}
        <button @click="jogarNovamente">jogar novamente</button>
    </div>
</template>

<script>
export default {
    name: 'final',
    props: {
        etapa: String,
        texto: String,
        jogarNovamente: Function
    }
}
</script>

<style scoped>

.final{
    margin: 20px 6px;
    font-size: 24px;
    font-weight: bold;
    display: flex;
    flex-direction: column;
}

.final.enforcado{
    color: var(--color-text-error);
}

.final.ganhador{
    color: var(--color-text-success);
}
</style>