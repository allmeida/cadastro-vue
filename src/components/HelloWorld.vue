<template>
  <div class="container">
    <h1 v-if="page == A">Sobre o Profissional</h1>
    <h1 v-if="page == B">Sobre o Atendimento</h1>
    <h1 v-if="page == C">Revisão do Cadastro</h1>
    <h1 v-if="page == D">Conclusâo do Cadastro</h1>

    <!-- <div class="row"> -->
    <!-- Pagina Sobre o Profissional -->
      <template v-if="page == A">
        <div class="container">
          <div class="card">
            <div class="card-body">
              <h1>Sobre o profissional</h1>
              <h3>Dados do profissional</h3>
            </div>
              <form>
                <div class="row">
                  <div class="col">
                    <div class="form-group col-sm-12 ">
                      <label for="nome">Nome Completo*</label>
                      <input id="nome" class="form-control" name="nome" type="text" v-model="nome" placeholder="Digite o nome completo" />
                    </div>
                    <div class="form-group col-sm-8">
                      <label for="cpf">CPF*</label>
                      <input id="cpf" class="form-control" name="cpf" type="text" v-model="cpf" placeholder="Digite um cpf" />
                    </div>
                    <div class="form-group col-sm-8">
                      <label for="telefone">Número do celular*</label>
                      <input id="telefone" class="form-control" name="telefone" type="text" v-model="telefone" placeholder="(00) 0 0000-0000" />
                    </div>
                  </div>
                  <div class="col-md-6">
                    <div class="box">
                      <img src="./desktop-pagina-1.png" alt="">
                    </div>
                  </div>
                </div>  

                <div class="row">
                <div class="form-group col-md-3">
                  <label for="inputEstados">Estado*</label>
                  <select id="inputEstados" v-model="estadoSelecionado" class="form-control" >
                    <option v-for="estado in estados" :key="estado.index" v-bind:value="estado"> {{ estado }} </option>
                  </select>
                </div>
                <div class="form-group col-md-3">
                  <label for="cidades">Cidade*</label>
                  <select id="cidades" class="form-control">
                    <option selected v-for="cidade in cidadeSelecionada" :key="cidade.index"> {{ cidade }} </option>
                  </select>
                </div>
              </div>
            </form>
          </div>
        </div>
      </template>

      <!-- Pagina Sobre o Atendimento -->
      <template v-if="page == B">
        <div class="container">
          <div class="card">
            <div class="card-body">
              <h1>Sobre o atendimento</h1>
              <h3>Detalhes do atendimento</h3>
            </div>
            <form>
              <div class="row">
                <div class="col">
                  <div class="form-group col-sm-12 mb-4">
                    <label for="especialidade" class="form-label">Especialidade principal*</label>
                    <select v-model="especialidade" class="form-select" id="especialidade">
                      <option>Selecione a especialidade</option>
                      <option>Cardiologia</option>
                      <option>Dermatologia</option>
                      <option>Neurologia</option>
                      <option>Oftalmologia</option>
                      <option>Psiquiatria</option>
                      <option>Urologia</option>
                    </select>
                  </div>
                </div>
                <div class="col-md-6">
                  <div class="box">
                      <img src="./desktop-pagina-2.png" alt="">
                  </div>
                </div>
                </div>         
                <div class="row">
                  <div class="col">
                    <div class="form-group col-sm-4 mb-4">
                      <label for="valor">Informe o preco da consulta*</label>
                      <div class="input-group mb-2 mr-sm-2">
                        <div class="input-group-prepend">
                          <div class="input-group-text">R$</div>
                        </div>
                        <input type="number" class="form-control" id="valor" v-model="valor" placeholder="Valor">
                      </div>
                    </div>
                    <div class="col">
                      <p>Formas de pagamento da consulta*</p>
                    </div>
                  </div>                
                </div>
                <div class="row"> 
                  <div class="cards-list">
                    <div id="card">
                      <div class="card-box mb-3">
                        <div class="form-check">
                          <input class="form-check-input" type="checkbox" value="dinheiro" id="flexCheckDefaultDinheiro" v-model="pagamento">
                          <label class="form-check-label" for="flexCheckDefaultDinheiro">
                            Em dinheiro
                          </label>
                        </div>
                      </div>
                    </div>
                    <div id="card">
                      <div class="card-box mb-3">
                        <div class="form-check">
                          <input class="form-check-input" type="checkbox" value="pix" id="flexCheckDefaultPix" v-model="pagamento">
                          <label class="form-check-label" for="flexCheckDefaultPix">
                            Pix
                          </label>
                        </div>
                      </div>
                    </div>
                    <div id="card">
                      <div class="card-box mb-3">
                        <div class="form-check">
                            <input v-model="pagamento" type="checkbox" class="form-check-input">
                            <label class="form-check-label" for="cartao">Cartao de credito</label>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <!-- <div>
                  <button class="w-50 btn" type="submit" @click.prevent="">PROXIMO</button>
                </div> -->
            </form>
          </div>
        </div>
      </template>

      <!-- Pagina Revisão do Cadastro -->
      <template v-if="page == C">
        <div class="card-body">
          <h3>Revisar Dados</h3>
        </div>
      </template>

      <!-- Pagina Finalizar Cadastro -->
      <template v-if="page == D">
        <div class="card-body">
          <h3>Cadastro Finalizado</h3>
        </div>
      </template>

      <div v-if="D">
        <button type="button" class="mt-4 btn btn-primary" v-on:click="nextPage()">PROXIMO</button>
      </div>

    <!-- </div> -->
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',

  data: function(){
    return {
    nome: "",
    cpf: "",
    telefone: "",
    inputEspecialidades: "",
    inputEstados: "",
    cidadeSelecionada: "",    
    
    estadoSelecionado: '',
    estados: [
    	'Paraná', 'Rio Grande do Sul', 'Santa Catarina'
    ],
    cidades: {
    	Paraná:[
    		'Londrina', 'Maringá'
    	],
    	'Rio Grande do Sul':[
    		'Pelotas', 'Porto Alegre'
    	],
    	'Santa Catarina':[
    		'Florianópolis', 'Joinville'
    	]
    },
    }
    },
    methods: {
      nextPage(){
        this.page++				
      }
    },
    computed: {
      cidadeSelecionada() {
        return this.cidades[this.estadoSelecionado]
      }
  }
};
</script>

<style scoped>
h1 {
    color: #483698;
    margin-bottom: 30px;
    font-family: Arial, Helvetica, sans-serif;
}

h3 {
    margin-bottom: 0px;
    font-family: Arial, Helvetica, sans-serif; 
}

.container {
    width: 100vw;
    height: 100vh;
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
}

.card {
    background: #fff;
    border-radius: 25px;
    display: inline-block;
    height: 700px;
    margin: 1rem;
    position: center;
    width: 800px;
    padding: 30px;
    box-shadow: 0 10px 20px rgba(0,0,0,0.19), 0 6px 6px rgba(0,0,0,0.23);
}

form {
    margin: 1rem;
}

.box img {
    float: right;
    position: absolute;
    width: 400px;
    height: 300px;
    margin-left: -20px;
    margin-top: -15px;
}

.btn {
    background-color: #483698;
    border: none;
    border-radius: 25px;
    color: white;
    padding: 5px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 20px;
    margin-top: 10px;
    cursor: pointer;
}

input, select {
    padding: 5px;
    margin-bottom: 10px;
    display: flex;
    border: 2px solid #483698;
    border-radius: 5px;
    background-color: transparent;
    font-size: 1rem;
}

label {
    font-family: Arial, Helvetica, sans-serif;
    font-size: 14px;
    padding: 5px;
}
</style>
