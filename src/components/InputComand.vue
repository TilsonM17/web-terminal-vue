<template>
    <div>
        <input type="text" ref="comandInput" v-model="input" @keyup.enter="validaComand">
    </div>
</template>

<script>
import axios from "axios"
import { store } from '../store.js'

export default {
    mounted() {
        this.$refs.comandInput.focus()
    },
    name: 'InputComand',
    data() {
        return {
            urlGithubSearch: "https://api.github.com/users/",
            mainComand: 'github',
            comandsValible: [
                'search',
                'ls',
                'help'

            ],
            input: ''
        }
    },
    methods: {
        validaComand() {
            var splitInput = this.input.split(" ")

            if (splitInput[0] === this.mainComand) {
                splitInput.length > 1 ? this.executeComand(splitInput) : this.printHelp()
            } else {
                alert('Comando não encontrado')
            }
        },
        executeComand(args) {
            this.comandsValible.indexOf(args[1]) > -1 ? this[args[1]](args[2]) : alert('Comando não encontrado 2');
        },
        search(name) {
            axios.get(this.urlGithubSearch + name)
                .then(response => {
                    store.dataResponse = response.data
                })
                .catch(error => {
                    console.log(error)
                })
        },
        printHelp() {
            console.log('Comandos disponiveis:')
        }

    }
}

</script>

<style scoped>
input[type="text"] {
    border: none;
    padding: 10px;
    font-size: 16px;
    width: 300px;
    outline: none;
}
</style>