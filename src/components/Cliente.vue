<template>
    <div class="cliente">
        <h1>Componente Cliente</h1>
        <p>{{ nome }}</p>
        <p>{{ descricao }}</p>
    </div>
</template>

<script>
export default {
    data() {
        return {
            nome: "Eduardo Freire Fernandes",
            numero: "27",
            email: "email@email",
            idade: 23,
            descricao:"Lorem ipsum it Lorem"
        };
    },
};
</script>

<style scoped>
.cliente {
    color: darkblue;
    text-align: center;
}
</style>