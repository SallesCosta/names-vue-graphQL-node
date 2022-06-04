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
                        <button
                          class="btn btn-info"
                          v-on:click="remove(sufix)"
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
              v-bind:key="domain"
            >
              <li class="list-group-item">{{ domain }}</li>
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
      prefixes: ['Air', 'Jet', 'Flight'],
      sufixes: ['Hub', 'Station', 'Mart'],
      domains: [],
    }
  },
  methods: {
    addPrefix(p) {
      this.prefixes.push(p)
      this.pre = ''
      this.generate()
    },
    addSufix(s) {
      this.sufixes.push(s)
      this.suf = ''
      this.generate()
    },
    generate() {
      this.domains = []
      for (const prefix of this.prefixes) {
        for (const sufix of this.sufixes) {
          this.domains.push(prefix + sufix)
        }
      }
    },
    remove(el) {
      const verificacao = this.prefixes.includes(el)
      verificacao
        ? this.prefixes.splice(this.prefixes.indexOf(el), 1)
        : this.sufixes.splice(this.sufixes.indexOf(el), 1)
      this.generate()
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
