<template>
    <div class="cliente">
        <input type="text" v-model="nome">
        <hr>
        <input type="text" v-model="descricao">
        <h1>Componente Cliente</h1>
        <p>Nome: {{ nome }}</p>
        <p>Descrição: {{ descricao }}</p>
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