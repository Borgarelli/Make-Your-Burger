<template>
    <Message :msg="msg" v-show="msg" />
    <div id="burger-table">
        <div>
            <div id="table-head">
                <div class="order-id">#:</div>
                <div>Cliente: </div>
                <div>Pão: </div>
                <div>Carnes: </div>
                <div>Opcionais: </div>
                <div>Ações: </div> 
            </div>
        </div>
        <div id="table-rows">
            <div class="burger-table-row" v-for="burger in burgers" :key="burger.id">
                <div class="order-number">{{burger.id}}</div>
                <div>{{burger.nome}}</div>
                <div>{{burger.pao}}</div>
                <div>{{burger.carne}}</div>
                <div>
                    <ul>
                        <li v-for="(opcional, index) in burger.opcionais" :key="index">
                            {{opcional}}
                        </li>
                    </ul>
                </div>
                <div>
                    <select name="status" class="status" @change="updateBurger($event, burger.id)">
                        <!-- <option value="">Selecione</option> -->
                        <option v-for="stat in status" :key="stat.id" :value="stat.tipo" :selected="burger.status == stat.tipo"> <!--Aqui o :selected está bindado para definir o status em que o pedido do hamburger se encontra, no caso como o pedido ja foi solicitado, todos os status de pedidos estaram como solicitados por enquanto-->
                            {{stat.tipo}}
                        </option>
                    </select>
                    <button class ="delete-btn" @click="deleteBurger(burger.id)">Cancelar</button>                    
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import Message from './Message.vue';
    export default {
        name: 'Dashboard',
        components: {
            Message
        },
        data(){
            return {
                burgers: null, //Ao invés de criar um objeto para cada coluna da tabela burgers, foi criado um para retornar todos os dados
                burger_id: null, //E apenas um para retornar o id
                status: [],
                msg: null

            }
        },
        methods:{
            async getPedidos() {

                const req = await fetch("http://localhost:3000/burgers");
                const data = await req.json();

                this.burgers = data; //Transforma os valores recebidos do banco em data, no caso retorna todos os valores armazenados na tabela de burgers, ou seja, todos os pedidos cadastrados pelo formulário

                //resgatar o status
                this.getStatus();
            },

            async getStatus() {
                const req = await fetch("http://localhost:3000/status");
                const data = await req.json();

                this.status = data;
            },
            
            async deleteBurger(id) { //Metódo para excluir burgers

                const req = await fetch(`http://localhost:3000/burgers/${id}`, {
                    method: "DELETE"
                });

                const res = await req.json();

                this.getPedidos(); //Já faz um retorno dos burgers registrados, logo após exlcuir algum

                this.msg = "Pedido cancelado";

                setTimeout(() => this.msg="", 3000);
            },

            async updateBurger(event, id) { //Método para atualização de status dentro do banco e no site

                const option = event.target.value;
                const dataJson = JSON.stringify ({status: option});

                const req = await fetch(`http://localhost:3000/burgers/${id}`, {
                    method: "PATCH",
                    headers: {"Content-type": "application/json" },
                    body: dataJson 
                });

                const res = await req.json(); //basicamente recebe os parametros passados pela requisição

                this.msg = `Pedido Nº ${res.id} está ${res.status}`; //Retorna a mensagem dizendo qual pedido foi alterado e para qual ação ele foi alterado
                setTimeout(() => this.msg = "", 3000);
            }
        },
        mounted(){
            this.getPedidos()
        }
    }
</script>

<style scoped>
    #burger-table{
        max-width: 1200px;
        margin: 0 auto;
    }

    #table-head,
    #table-rows,
    .burger-table-row {
        display: flex;
        flex-wrap: wrap;
    }

    #table-head {
        font-weight: bold;
        padding: 12px;
        border-bottom: 3px solid #333;
        cursor: default;
    }

    #table-head div{
        width: 19%;
    }
    .burger-table-row div {
        width: 19%;
        cursor: default;
    }

    .burger-table-row {
        width: 100%;
        padding: 12px;
        border-bottom: 1px solid #ccc;
    }

    .burger-table-row li {
        margin-bottom: 10px;
    }

    
    #table-head .order-id,
    .burger-table-row .order-number{
        width: 5%;
    }
    select {
        padding: 12px 6px;
        margin-right: 12px;
    }

    .delete-btn{
        background-color: #222;
        color: #FCBA03;
        font-weight: bold;
        border: 2px solid #222;
        padding: 10px;
        font-size: 16px;
        margin: 0 auto;
        cursor: pointer;
        transition: .5s;
    }

    .delete-btn:hover {
        background-color: transparent;
        color: #222;
    }
</style>