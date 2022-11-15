<template>
    <div id="burger-table">
        <div>
            <div id="table-head">
                <div class="order-id">#:</div>
                <div>Cliente: </div>
                <div>Pão: </div>
                <div>Carnes: </div>
                <div>Opcionais</div>
                <div>Ações: </div> 
            </div>
        </div>
        <div id="table-rows">
            <div class="burger-table-row">
                <div class="order-number">1</div>
                <div>Kauã</div>
                <div>3 Queijos</div>
                <div>Maminha</div>
                <div>
                    <ul>
                        <li>Bacon</li>
                        <li>Cheddar</li>
                    </ul>
                </div>
                <div>
                    <select name status="" class="status">
                        <option value="">Selecione</option>
                    </select>
                    <button class ="delete-btn">Cancelar</button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'Dashboard',
        data(){
            return {

            }
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
    }

    #table-head div{
        width: 19%;
    }
    .burger-table-row div {
        width: 19%
    }

    .burger-table-row {
        width: 100%;
        padding: 12px;
        border-bottom: 1px solid #ccc;
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