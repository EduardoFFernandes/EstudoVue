<template>
    <div id="app">
        <h1>Clientes</h1>
        <div class="cadastro">
            <input type="text" placeholder="Nome" v-model="nomeField" /><br />
            <input
                type="text"
                placeholder="Descrição"
                v-model="descricaoField"
            /><br />
            <button @click="cadastrarCliente()">Cadastrar</button>
        </div>
        <hr />
        <div class="clientes">
            <div v-for="cliente in clientes" :key="cliente.id">
                <Cliente :cliente="cliente" />
            </div>
        </div>
    </div>
</template>

<script>
import Cliente from "./components/Cliente";
export default {
    name: "App",
    data() {
        return {
            nomeField: "",
            descricaoField: "",
            clientes: [
                {
                    id: 1,
                    nome: "Eduardo Freire Fernandes",
                    descricao: "Descricao 1",
                },
                {
                    id: 2,
                    nome: "Fernando Freire Fernandes",
                    descricao: "Descricao 2",
                },
                {
                    id: 3,
                    nome: "Joao Freire Fernandes",
                    descricao: "Descricao 3",
                },
                {
                    id: 4,
                    nome: "Gabriel Freire Fernandes",
                    descricao: "Descricao 4",
                },
                {
                    id: 5,
                    nome: "Allison Freire Fernandes",
                    descricao: "Descricao 5",
                },
            ],
        };
    },
    components: {
        Cliente,
    },
    methods: {
        cadastrarCliente: function() {
          this.clientes.push({nome: this.nomeField, descricao: this.descricaoField, id: Date.now()});
          this.nomeField = "";
          this.descricaoField = "";
        }
    }
};
</script>

<style scoped>
#app {
    text-align: center;
    background-color: cyan;
    background-image: linear-gradient(
        to bottom right,
        rgb(118, 245, 160),
        rgb(22, 63, 27)
    );
}
.clientes {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: space-around;
    margin: 0px 10% 0px 10%;
}
.cadastro {
    display: flex;
    flex-direction: column;
    align-items: center;
}
</style>