<template>
    <p>Componente de mensagem</p>
    <div>
        <div>
            <form id="id-form" @submit="createBurger"> <!--Atribuindo o evento ao formulário, sempre que o botão de submit for utilizado, retorna a mensagem de criação do lanche no console-->
              <div class="input-container">
                <label for="nome">Nome do Cliente </label>
                <input type="text" id="nome" name="nome" v-model="nome" placeholder="Digite o seu nome">
              </div>
              <div class="input-container">
                <label for="pao">Escolha o pão: </label>
                <select name="pao" id="pao" v-model="pao">
                    <option v-for="pao in paes" :key="pao.id" :value="pao.tipo">
                        {{pao.tipo}}
                    </option> <!--Conexão com o banco na coluna de paes-->
                </select>           
              </div>
              <div class="input-container">
                <label for="carne">Escolha a carne do seu lanche: </label>
                <select name="carne" id="carne" v-model="carne">
                    <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">
                        {{carne.tipo}}
                    </option> <!--Conexão com o banco na coluna de carnes-->
                </select>           
              </div>
              <div id="opicional-container">
                <label id="opcionais-title" for="opcionais">Selecione os opcionais: </label>
                 <div class="checkbox-container" v-for="opcional in opcionaisdata" :key="opcional.id">
                    <input id="check" type="checkbox" name="opcionais" v-model="opcionais" :value="opcional.tipo">
                    <span> {{opcional.tipo}} </span> <!--Conexão com o banco na coluna de opcionais-->
                 </div>        
              </div>
                <div class="input-container">
                    <input type="submit"  class="submit-btn" value="Criar meu lanche">
                </div>    
            </form> 
        </div>
    </div>
</template>

<script>
    export default {
        name: 'BurgerForm',
        data(){
            return {
                paes: null, //Estão no plural para identificar que são os recebidos da api "fake"
                carnes: null,
                opcionaisdata: null,
                nome: null,
                pao:null, //São os dados que iram ser enviados para o banco
                carne:null,
                opcionais: [],
                status: "Solicitado",
                msg: null
            }
        },
        methods:{
            async getIngredientes() { //Metódo para retornar todos os ingredientes registrados no banco através no link que o vue gera !!Importante não esquecer de rodar um (npm run backend) para funcionar
                const req = await fetch("http://localhost:3000/ingredientes"); 
                const data = await req.json(); //Define um tempo para retornar os dados através da requisição json

                this.paes = data.paes; //Necessário criar por aqui o metódo, cada um é responsável pela requisição de uma coluna em especifico essa é pelos paes
                this.carnes = data.carnes; //carnes
                this.opcionaisdata = data.opcionais; //opcionais

            },

            async createBurger(e) { //criação do metódo para criar um lanche, atribuindo ele a um evento

                e.preventDefault();

                const data = { //criação do objeto para definir os parametros que serviram para enviar dados ao banco
                    nome: this.nome,
                    pao: this.pao,
                    carne: this.carne,
                    opicionais: Array.from(this.opcionais), //Aqui foi necessário pois como Opcionais no data está como um elemento de lista, foi necessário passar o dado por uma maneira diferente
                    status: "Solicitado"
                }
                const dataJson = JSON.stringify(data); //Objeto que transforma os dados em formato de string e manda para o banco

                const req = await fetch("http://localhost:3000/burgers", { //Aqui cria o metódo post que conecta com o localhost do backend gerado pelo vue
                    method: "POST",
                    headers: {"Content-Type": "application/json"},
                    body: dataJson
                });

                const res = await req.json();

                //colocar uma msg de sistema

                //limpar msg

                //limpar os campos
                this.nome = "";
                this.carne = "";
                this.pao = "";
                this.opcionais = "";
                
            }

            
        },
        mounted(){ //Aqui inia um lyfeciclehook que irá retornar os dados 
            this.getIngredientes()
        }
    }
</script>

<style scoped>
    #id-form{
        max-width: 400px;
        margin: 0 auto;
    }

    .input-container {
        display: flex;
        flex-direction: column;
        margin-bottom: 20px;
    }

    label {
        font-weight: bold;
        margin-bottom: 15px;
        color: #222;
        padding: 5px 10px;
        border-left: 4px solid #FCBA03;
    }

    input, select {
        padding: 5px 10px;
        width: 300px;
    }

    #opicional-container {
        display: flex;
        flex-wrap: wrap;
        
    }

    #opcionais-title {
        width: 100%;
    }

    .checkbox-container {
        display: flex;
        align-items: flex-start;
        width: 50%;
        margin-bottom: 20px;
    }

    .checkbox-container span,
    .checkbox-container input {
        width: auto;
        margin-top: 10px;
    }

    .checkbox-container span {
        margin-left: 6px;
        font-weight: bold;
    }

    .submit-btn{
        background-color: #222;
        color: #FCBA03;
        font-weight: bold;
        border: 2px solid #222;
        padding: 10px;
        font-size: 16px;
        margin: 0 auto; /*Faz o botão ficar centralizado no container */
        cursor: pointer;
        transition: .5s;
    }

    .submit-btn:hover {
        background-color: transparent; /*Para dar efeito de tranparencia ao botão */
        color: #222;
    }
</style>