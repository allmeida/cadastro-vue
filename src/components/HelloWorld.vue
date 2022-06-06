<template>
  <div class="container">
      <!-- <h1 v-if="page == 1"></h1> -->
      <!-- <h1 v-if="page == 2">Sobre o atendimento</h1>
      <h1 v-if="page == 3">Revisão dos Cadastro</h1>
      <h1 v-if="page == 4"></h1> -->
    <div class="row">  
      <!-- Pagina Sobre o Profissional -->
      <template v-if="page == 1">
        <div class="container">
          <div class="card">
            <div class="card-body">
              <h1>Sobre o  Profissional</h1>
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

                <div class="row input_estado">
                  <div class="col-sm-3">
                    <div class="form-group">
                      <label for="inputEstados">Estado*</label>
                      <select id="inputEstados" v-model="estadoSelecionado" class="form-control" >
                        <option v-for="estado in estados" :key="estado.index" v-bind:value="estado"> {{ estado }} </option>
                      </select>
                    </div>
                  </div>
                  <div class="col-sm-3">
                    <div class="form-group">
                      <label for="cidades">Cidade*</label>
                      <select id="cidades" class="form-control">
                        <option selected v-for="cidade in cidadeSelecionada" :key="cidade.index"> {{ cidade }} </option>
                      </select>
                    </div>
                  </div>
              </div>

              <div class="mt-5">
                <button class="w-50 btn" v-on:click="nextPage(page == 2)">PROXIMO</button>
              </div>

            </form>
          </div>
        </div>
      </template>

      <!-- Pagina Sobre o Atendimento -->
      <template v-if="page == 2">
        <div class="container">
          <div class="card">
            <div class="card-body">
              <h1>Revisão dos dados</h1>
              <h3>Detalhes do atendimento</h3>
            </div>
            <form>
              <div class="row">
                <div class="col">
                  <div class="form-group col-sm-12">
                    <label for="especialidades" class="form-label">Especialidade principal*</label>
                    <select v-model="especialidades" class="form-select" id="especialidades">
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
                    <div class="form-group col-sm-4">
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
                  <div class="col cards-list">
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
                        <div class="form-check" data-toggle="collapse" data-target="#collapseExample" aria-expanded="false" aria-controls="collapseExample">
                          <input class="form-check-input" type="checkbox" value="credito" id="flexCheckDefaultCartaoCredito" v-model="pagamento">
                          <label class="form-check-label" for="flexCheckDefaultCartaoCredito">
                          Cartão de crédito
                          </label>
                          <div class="credito">
                            <div class="form-check collapse" id="collapseExample">
                              <input class="form-check-input" type="radio" name="flexRadioDefault" id="um" value="1x sem juros" v-model="vezes">
                              <label class="form-check-label" for="flexRadioDefault1">
                                1x, sem juros
                              </label>
                            </div>
                            <div class="form-check collapse" id="collapseExample">
                              <input class="form-check-input" type="radio" name="flexRadioDefault" id="duas" value="2x sem juros" checked v-model="vezes">
                              <label class="form-check-label" for="flexRadioDefault2">
                                2x, sem juros
                              </label>
                            </div>
                            <div class="form-check collapse" id="collapseExample">
                              <input class="form-check-input" type="radio" name="flexRadioDefault" id="tres" checked value="3x sem juros" v-model="vezes">
                              <label class="form-check-label" for="flexRadioDefault3">
                                3x, sem juros
                              </label>
                            </div>
                          </div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>

                <div class=" mt-0">
                  <button class="w-50 btn" v-on:click="nextPage(page == 3)">PROXIMO</button>
                </div>

            </form>
          </div>
        </div>
      </template>

      <!-- Pagina Revisão do Cadastro -->
      <template v-if="page == 3">
        <div class="container">
          <div class="card">
            <div class="card-body">
              <h1>Revisão do Cadastro</h1>
            </div>
            <div class="row">
              <div class="col-md-6">
                  <div>
                      <h7> <strong>NOME COMPLETO:</strong></h7>
                      <p>{{ nome }}</p>
                  </div>
                  <div>
                      <h7><strong>NÚMERO DO CPF:</strong></h7>
                      <p>{{ cpf }}</p>
                  </div>
                  <div>
                      <h7><strong>NÚMERO DE TELEFONE:</strong></h7>
                      <p>{{ telefone }}</p>
                  </div>
                  <div>
                      <h7><strong>ESPECIALIDADE PRINCIPAL:</strong></h7>
                      <p>{{ especialidade }}</p>
                  </div>
                  <div>
                      <h7><strong>ESTADO/CIDADE</strong></h7>
                      <p>{{ estadoSelecionado }}/{{ cidadeSelecionada }}</p>
                  </div>
                  <div>
                      <h7><strong>VALOR DA CONSULTA</strong></h7>
                      <p>{{ valor }}</p>
                  </div>
                  <div>
                      <h7><strong>FORMA DE PAGAMENTO</strong></h7>
                      <p>{{ pagamento }}</p>
                  </div>
                </div>
              <div class="col-md-6">
                <div class="box">
                  <img src="./desktop-pagina-3.png" alt="">
                </div>
              </div>
            </div>

            <div class="row">
              <div class="col-6">
                <button type="button" class="mt-4 btn-warning" v-on:click="returnInicio (page == 1)">EDITAR CADASTRO</button>
              </div>
            </div>

            <div class="mt-10">
              <button class="w-50 btn" v-on:click="nextPage(page == 4)">PROXIMO</button>
            </div>

          </div>
        </div>
      </template>

      <!-- Pagina Finalizar Cadastro -->
      <template v-if="page == 4">
        <div class="container">
          <div class="card">
            <div class="card-center">
              <h1>Revisão do Cadastro</h1>
            </div>
            <div class="row">
              <h3>
                Parabéns, cadastro realizado com sucesso !
              </h3>
            </div>
          </div>
        </div>
      </template>

      <!-- <div v-if="page < 4">
        <button class="w-50 btn" v-on:click="nextPage()">PROXIMO</button>
      </div> -->

    </div>
  </div>
</template>

<script>

// import api from '../services/api.js';

export default {
  name: 'HelloWorld',
  data: function(){
    return {
    page: 1,
    nome: "",
    cpf: "",
    telefone: "",
    especialidades: "",
    inputEstados: "",
    cidadeSelecionada: "",    
    valor: "",
    pagamento: [],
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
    margin-bottom: 25px;
    font-family: Comfortaa, Open sans-serif, Avenir, Helvetica, Arial, sans-serif;
}

h3 {
    margin-bottom: 0px;
    font-family: Comfortaa, Open sans-serif, Avenir, Helvetica, Arial, sans-serif;
}

p {
    font-family: Arial, Helvetica, sans-serif;
    font-size: 12px;
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

#card .card-box {
    background: #F9F9F9;
    width: 350px;
    padding: 10px;
    align-items: center;
    border-radius: 10px;
    box-shadow: 5px 5px 5px 0px rgba(0,0,0,0.10), 6px 6px 6px 6px rgba(0,0,0,0.10);
}

.cards-list {
  margin: 2px;
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

.input-group-text {
    background-color: #483698;
    border: none;
    color: white;
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

.input_estado {
  margin: 2px;
}

label {
    font-family: Arial, Helvetica, sans-serif;
    font-size: 14px;
    padding: 5px;
}
</style>
