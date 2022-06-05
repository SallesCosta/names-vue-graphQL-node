<template>
  <div>
    <div id="slogan" class="text-center">
      <h1>NameGator</h1>
      <h6 class="text-secondary">Gerador de Nomes com Vue, GraphQL e Node</h6>
    </div>
    <div id="main">
      <div id="container">
        <div class="row">
          <div class="col-md">
            <h5>
              Prefixos<span class="badge-light">{{ prefixes.length }}</span>
            </h5>
            <div class="card">
              <div class="card-body">
                <ul class="list-group">
                  <li
                    class="list-group-item"
                    v-for="prefix in prefixes"
                    v-bind:key="prefix"
                  >
                    <div class="row">
                      <div class="col-md">
                        {{ prefix }}
                      </div>
                      <div class="col-md text-right">
                        <button
                          class="btn btn-info"
                          v-on:click="remove(prefix)"
                        >
                          <span class="fa fa-trash"></span>
                        </button>
                      </div>
                    </div>
                  </li>
                </ul>
                <br />
                <div class="input-group">
                  <input
                    class="form-control"
                    type="text"
                    placeholder="digite o prefixo"
                    v-model="pre"
                    v-on:keyup.enter="addPrefix(pre)"
                  />
                  <div class="input-group-append">
                    <button v-on:click="addPrefix(pre)" class="btn btn-info">
                      <span class="fa fa-plus" />
                    </button>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="col-md">
            <h5>
              Sufixos<span class="badge-info">{{ sufixes.length }}</span>
            </h5>
            <div class="card">
              <div class="card-body">
                <ul class="list-group">
                  <li
                    class="list-group-item"
                    v-for="sufix in sufixes"
                    v-bind:key="sufix"
                  >
                    <div class="row">
                      <div class="col-md">
                        {{ sufix }}
                      </div>
                      <div class="col-md text-right">
                        <button class="btn btn-info" v-on:click="remove(sufix)">
                          <span class="fa fa-trash"></span>
                        </button>
                      </div>
                    </div>
                  </li>
                </ul>
                <br />
                <div class="input-group">
                  <input
                    class="form-control"
                    type="text"
                    placeholder="digite o sufixo"
                    v-model="suf"
                    v-on:keyup.enter="addSufix(suf)"
                  />

                  <div class="input-group-append">
                    <button v-on:click="addSufix(suf)" class="btn btn-info">
                      <span class="fa fa-plus" />
                    </button>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <br />
        <h5>
          Dominios <span class="badge-info">{{ domains.length }}</span>
        </h5>
        <div class="card">
          <div class="card-body">
            <ul
              class="list-group"
              v-for="domain in domains"
              v-bind:key="domain.name"
            >
              <li class="list-group-item">
                <div class="row">
                  <div class="col-md">
                    {{ domain.name }} 
                  </div>
                  <div class="col-md text-right">
                    <a
                      class="btn btn-info"
                      v-bind:href='domain.checkout'
                      target="_blank"
                    >
                      <span class="fa fa-shopping-cart"></span>
                    </a>
                  </div>
                </div>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import 'bootstrap/dist/css/bootstrap.css'
import 'font-awesome/css/font-awesome.css'

export default {
  name: 'App',
  data: function () {
    return {
      pre: '',
      suf: '',
      prefixes: ['Air', 'Flight', 'Jet'],
      sufixes: ['Abc', 'Bcd', 'Cde'],
    }
  },
  methods: {
    addPrefix(p) {
      this.prefixes.push(p)
      this.pre = ''
    },
    addSufix(s) {
      this.sufixes.push(s)
      this.suf = ''
    },
    remove(el) {
      const verificacao = this.prefixes.includes(el)
      verificacao
        ? this.prefixes.splice(this.prefixes.indexOf(el), 1)
        : this.sufixes.splice(this.sufixes.indexOf(el), 1)
    },
  },
  computed: {
    domains() {
      console.log('aqui...')
      const domains = []
      for (const prefix of this.prefixes) {
        for (const sufix of this.sufixes) {
          const name = prefix + sufix
          const checkout = `https://cart.hostgator.com.br/?pid=d&sld=${name.toLowerCase()}&tld=.com&domainCycle=3&_ga=2.1724209.164945295.1654446855-1077287454.1654446855`
          domains.push({ name, checkout })
        }
      }
      return domains
    },
  },
}
</script>

<style>
#slogan {
  margin-top: 30px;
  margin-botton: 30px;
}

#main {
  background: #f1f1f1;
  padding-top: 30px;
  padding-botton: 90px;
}
</style>
