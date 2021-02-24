<template>
    <div id="app">
        <div class="columns is-centered">
            <div class="column is-4">
                <input
                    class="input is-primary"
                    type="text"
                    placeholder="Nome"
                    v-model="nomeField"
                    @change="atualizaMensagemErro()"
                />
                <small id="nomeErro" v-show="nomeErro" style="color: darkred"
                    >O nome é invalido, tente novamente!</small
                >
            </div>
            <div class="column is-4">
                <input
                    class="input is-primary"
                    type="text"
                    placeholder="Descrição"
                    v-model="descricaoField"
                    @change="atualizaMensagemErro()"
                />
                <small
                    id="nomeErro"
                    v-show="descricaoErro"
                    style="color: darkred"
                    >Descrição é invalida, tente novamente!</small
                >
            </div>
            <button class="button is-primary" @click="cadastrarCliente()">
                Cadastrar
            </button>
        </div>
        <hr />
        <div class="clientes">
            <div v-for="cliente in orderArray" :key="cliente.id">
                <Cliente
                    :cliente="cliente"
                    @meDelete="deletarCliente($event)"
                />
            </div>
        </div>
    </div>
</template>

<script>
import _ from "lodash";
import Cliente from "./components/Cliente";
export default {
    name: "App",
    data() {
        return {
            nomeField: "",
            descricaoField: "",
            nomeErro: false,
            descricaoErro: false,
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
        clearInput: function () {
            this.nomeField = "";
            this.descricaoField = "";
        },
        cadastrarCliente: function () {
            if (this.nomeField.length < 3) {
                this.nomeErro = true;
                return;
            }
            if (this.descricaoField.length < 1) {
                this.descricaoErro = true;
                return;
            }
            this.clientes.push({
                nome: this.nomeField,
                descricao: this.descricaoField,
                id: Date.now(),
            });
            this.clearInput();
        },
        atualizaMensagemErro: function () {
            this.nomeErro = this.nomeField.length > 3 ? false : true;
            this.descricaoErro = this.descricaoField.length > 1 ? false : true;
        },
        deletarCliente: function ($event) {
            // this.clientes.delete({})
            var id = $event;
            var novoArray = this.clientes.filter((cliente) => cliente.id != id);
            this.clientes = novoArray;
        },
        randomColor: function () {
            const hex = (Math.random()*0xFFFFFF<<0). toString(16)
            return ``
        }
    },
    computed: {
        orderArray: function () {
            return _.orderBy(this.clientes, ["nome", "asc"]);
        },
    },
};
</script>

<style scoped>
#app {
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
</style>