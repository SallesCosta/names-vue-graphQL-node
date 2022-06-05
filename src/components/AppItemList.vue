<template>
  <div>
    <h5>
      {{ title }}<span class="badge-light">{{ items.length }}</span>
    </h5>
    <div class="card">
      <div class="card-body">
        <ul class="list-group">
          <li class="list-group-item" v-for="item in items" v-bind:key="item">
            <div class="row">
              <div class="col-md">
                {{ item }}
              </div>
              <div class="col-md text-right">
                <button class="btn btn-info" v-on:click="removeItem(item)">
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
            placeholder="digite o item"
            v-model="pre"
            v-on:keyup.enter="addItem(pre)"
          />
          <div class="input-group-append">
            <button v-on:click="addItem(pre)" class="btn btn-info">
              <span class="fa fa-plus" />
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AppItemList',
  props: ['items', 'title'],
  data() {
    return {
      item: '',
      pre: '',
    }
  },
  methods: {
    addItem(i) {
      this.$emit('addItem', i)
      this.pre = ''
    },
    removeItem(i) {
      this.$emit('removeItem', i)
    },
  },
}
</script>

<style></style>
