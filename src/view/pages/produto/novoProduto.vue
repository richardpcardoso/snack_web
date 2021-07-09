<template>
  <div>
    <h3 class="text-warning mt-10 mb-5">Novo Produto</h3>
    <b-form @submit="onSubmit" @reset="onReset" v-if="show">
      <b-form-group
          id="input-group-1"
          label="Nome do produto:"
          label-for="input-1"
      >
        <b-form-input
            id="input-1"
            v-model="form.email"
            type="email"
            required
            placeholder="Nome do Produto"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-2" label="Descrição:" label-for="input-2">
        <b-form-input
            id="input-2"
            v-model="form.name"
            required
            placeholder="Desfrição do produto"
        ></b-form-input>
      </b-form-group>

      <label>Imagem: </label>
      <b-form-file
          v-model="file"
          :state="Boolean(file)"
          placeholder="Escolha um arquivo ou solte-o aqui..."
          drop-placeholder="Solte o arquivo aqui..."
      ></b-form-file>
      <div class="mt-1 mb-10">Arquivo selecionado : {{ file ? file.name : '' }}</div>

      <b-form-group label="Situação:">
        <b-form-radio name="some-radios" value="A">Disponível</b-form-radio>
        <b-form-radio name="some-radios" value="B">Indisponível</b-form-radio>
      </b-form-group>

      <router-link
          to="/cardapio"
          v-slot="{ href, navigate, isActive, isExactActive }"
      >
        <a :href="href" class="btn btn-success mr-3" @click="navigate">
          <span class="menu-text"> Salvar</span>
        </a>
      </router-link>
      <b-button type="reset" variant="danger">Limpar</b-button>
    </b-form>
  </div>
</template>

<script>

export default {
  data() {
    return {
      form: {
        email: '',
        name: '',
        food: null,
        checked: []
      },
      foods: [{ text: 'Select One', value: null }, 'Carrots', 'Beans', 'Tomatoes', 'Corn'],
      show: true
    }
  },
  methods: {
    onSubmit(evt) {
      evt.preventDefault()
      alert(JSON.stringify(this.form))
    },
    onReset(evt) {
      evt.preventDefault()
      // Reset our form values
      this.form.email = ''
      this.form.name = ''
      this.form.food = null
      this.form.checked = []
      // Trick to reset/clear native browser form validation state
      this.show = false
      this.$nextTick(() => {
        this.show = true
      })
    }
  }
};
</script>
