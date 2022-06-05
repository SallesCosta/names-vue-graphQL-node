<template>
  <div>
    <div id="main">
      <div id="container">
        <div class="row">
          <div class="col-md">
            <AppItemList
              title="Prefixos"
              v-bind:items="prefixes"
              v-on:addItem="addPrefix"
              v-on:removeItem="remove"
            />
          </div>
          <div class="col-md">
            <AppItemList
              title="Sufixos"
              v-bind:items="sufixes"
              v-on:addItem="addSufix"
              v-on:removeItem="remove"
            />
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
                      v-bind:href="domain.checkout"
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
import AppItemList from './AppItemList.vue'
export default {
  name: 'DomainList',
  components: {
    AppItemList,
  },
  data: function () {
    return {
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

<style></style>
