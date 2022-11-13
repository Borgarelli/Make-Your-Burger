<template>
    <p>Componente de mensagem</p>
    <div>
        <div>
            <form id="id-form">
              <div class="input-container">
                <label for="nome">Nome do Cliente </label>
                <input type="text" id="nome" name="nome" v-model="nome" placeholder="Digite o seu nome">
              </div>
              <div class="input-container">
                <label for="pao">Escolha o pão: </label>
                <select name="pao" id="pao" v-model="pao">
                    <option value="">Selecione o seu pão: </option>
                    <option value="integral">Integral</option>
                </select>           
              </div>
              <div class="input-container">
                <label for="carne">Escolha a carne do seu lanche: </label>
                <select name="carne" id="carne" v-model="carne">
                    <option value="">Selecione o tipo de carne: </option>
                    <option value="maminha">Maminha</option>
                </select>           
              </div>
              <div id="opicional-container">
                <label id="opcional-title" for="opcional">Selecione os opcionais: </label>
                 <div class="checkbox-container">
                    <input type="checkbox" name="opcional" v-model="opcional" value="presunto">
                    <span> Presunto</span>
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

            }
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

    #optional-container {
        flex-direction: row;
        flex-wrap: wrap;
    }

    #opcional-title {
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
        margin-top: 10px
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