<template>
    <div id="burger-table">
        <div>
            <div id="burger-table-heading">
                <div class="order-id">#:</div>
                <div>Cliente: </div>
                <div>Pão: </div>
                <div>Carne: </div>
                <div>Opcionais: </div>
                <div>Ações: </div>
            </div>

            <div id="burger-table-rows">
                <div class="burger-table-row" v-for="burger in burgers" :key="burger.id">
                    <div class="order-number">{{ burger.id }}</div>
                    <div>{{ burger.nome }}</div>
                    <div>{{ burger.pao }}</div>
                    <div>{{ burger.carne }}</div>
                    <div>
                        <ul>
                            <li v-for="(opcional, index) in burger.opcionais" :key="index">
                                {{ opcional }}
                            </li>
                        </ul>
                    </div>
                    <div>
                        <select name="status" class="status" @change="updateBurger($event, burger.id)">
                            <option value="">Selecione</option>
                            <option v-for="s in status" :key="s.id" :value="s.tipo" :selected="burger.status == s.tipo">
                                {{ s.tipo }}
                            </option>
                        </select>
                        <button class="delete-btn" @click="deleteBurger(burger.id)">Cancelar</button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>

    export default {
        name: "Dashboard",

        data() {
            return {
                burgers: null,
                burgers_id: null,
                status: []
            }
        },

        methods: {
            async getPedidos() {

                const req = await fetch ('http://localhost:3000/burgers')

                const data = await req.json()

                this.burgers = data

                //resgatar os status
                this.getStatus()

            },

            async getStatus() {
                const req = await fetch ('http://localhost:3000/status')

                const data = await req.json()

                this.status = data
            },

            async deleteBurger(id) {
                const req = await fetch (`http://localhost:3000/burgers/${id}`, {
                    method: "DELETE"
                })

                const res = await req.json

                //msg

                this.getPedidos()
            },

            async updateBurger(event, id) {

                const option = event.target.value

                const dataJson = JSON.stringify({status: option})

                const req = await fetch (`http://localhost:3000/burgers/${id}`, {
                    method: "PATCH",
                    headers: {'Content-Type': 'application/json'},
                    body: dataJson
                })

                const res = await req.json

                console.log(res)



            }
        },
        
        mounted() {
            this.getPedidos()
        }
    }

</script>

<style lang="scss">
    @import '@/scss/index';
</style>