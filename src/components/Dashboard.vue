<template>
    <div id="pizza-table">
        <div>
            <div id="pizza-table-heading">
                <div class="order-id">#:</div>
                <div>Cliente:</div>
                <div>Massa:</div>
                <div>Recheio:</div>
                <div>Opcionais:</div>
                <div>Ações:</div>
            </div>
        </div>
        <div id="pizza-table-rows">
            <div class="pizza-table-row">
                <div class="order-number">1</div>
                <div>Fulano</div>
                <div>Massa Fina</div>
                <div>Mussarela</div>
                <div>
                    <ul>
                        <li>Salame</li>
                        <li>Tomate</li>
                    </ul>
                </div>
                <div>
                    <select name="status" id="status">
                        <option value="">Selecione</option>
                    </select>
                    <button class="delete-btn">Cancelar</button>
                </div>
            </div>

        </div>
    </div>
</template>

<script>
export default {
    name: "Dashboard"
}
</script>

<style scoped>
#pizza-table {
    max-width: 1200px;
    margin: 0 auto;
}

#pizza-table-heading,
#pizza-table-rows,
.pizza-table-row {
    display: flex;
    flex-wrap: wrap;
}

#pizza-table-heading {
    font-weight: bold;
    padding: 12px;
    border-bottom: 3px solid #333;
}

.pizza-table-row {
    width: 100%;
    padding: 12px;
    border-bottom: 1px solid #CCC;
}

#pizza-table-heading div,
.pizza-table-row div {
    width: 19%;
}

#pizza-table-heading .order-id,
.pizza-table-row .order-number {
    width: 5%;
}

select {
    padding: 12px 6px;
    margin-right: 12px;
}

.delete-btn {
    background-color: #222;
    color: #fcba03;
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