<template>
    <div>
        <p>Componente de Mensagem</p>
    </div>
    <div>
        <form id="pizza-form">
            <div class="input-container">
                <label for="name">Nome do cliente:</label>
                <input type="text" name="name" id="name" v-model="name" placeholder="Digite o seu nome">
            </div>

            <div class="input-container">
                <label for="mass">Escolha a massa:</label>
                <select name="mass" id="mass" v-model="mass">
                    <option value="">Selecione a massa</option>
                    <option v-for="mass in massas" :key="mass.id" value="mass.tipo">{{mass.tipo}}</option>
                </select>
            </div>

            <div class="input-container">
                <label for="filling">Selecione o seu recheio:</label>
                <select name="filling" id="filling" v-model="filling">
                    <option value="">Selecione o tipo de recheio</option>
                    <option v-for="filling in recheios" :key="filling.id" value="filling.tipo">{{filling.tipo}}</option>
                </select>
            </div>

            <div id="optional-container" class="input-container">
                <label id="optional-title"  for="optional">Selecione os opcionais:</label>
                <div class="checkbox-container" v-for="optional in opcionaisdata" :key="optional.id">
                    <input type="checkbox" name="optional" v-model="opcionais" :value="optional.tipo">
                    <span>{{optional.tipo}}</span>
                </div>
                
            </div>

            <div class="input-container">
                <input type="submit" class="submit-btn" value="Criar minha Pizza!">
            </div>

        </form>
    </div>
</template>
<script>
export default {
    name: "PizzaForm",
    data() {
        return {
            massas: null,
            recheios: null,
            opcionaisdata: null,
            nome: null,
            massa: null,
            recheio: null,
            opcionais: [],
            status: "Solicitado",
            msg: "null"

        }
    },
    methods: {
        async getIngredients() {
            const req = await fetch("http://localhost:3000/ingredientes");
            const data = await req.json();

            this.massas = data.massas;
            this.recheios = data.recheios;
            this.opcionaisdata = data.opcionais;
        }
    },
    mounted() {
        this.getIngredients()
    },
}
</script>
<style scoped>
#pizza-form {
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
    border-left: 4px solid #fcba03;
}

input,
select {
    padding: 5px 10px;
    width: 300px;
}

#optional-container {
    flex-direction: row;
    flex-wrap: wrap;
    
}
#optional-title{
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
}

.checkbox-container span {
    margin-left: 6px;
    font-weight: bold;
}

.submit-btn {
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

.submit-btn:hover{
    background-color: transparent;
    color: #222;
}
</style>