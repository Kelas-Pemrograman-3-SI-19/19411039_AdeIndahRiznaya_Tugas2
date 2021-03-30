<template>
  <div class="q-pa-md" style="max-width: 400px">

    <q-form
      @submit="onSubmit"
      @reset="onReset"
      class="q-gutter-md"
    >
      <q-input
        filled
        v-model="form.name"
        label="Nama Lengkap *"
        hint="Nama Lengkap"
        lazy-rules
        :rules="[ val => val && val.length > 0 || 'Nama lengkap tidak boleh kosong']"
      />

      <q-input
        filled
        type="number"
        v-model="form.age"
        label="Usia *"
        lazy-rules
        :rules="[
          val => val !== null && val !== '' || 'Usia tidak boleh kosong',
          val => val > 0 && val < 100 || 'Masukan usia yang benar'
        ]"
      />

      <q-toggle v-model="accept" label="I accept the license and terms" />

      <div>
        <q-btn label="Submit" type="submit" color="primary"/>
        <q-btn label="Reset" type="reset" color="primary" flat class="q-ml-sm" />
      </div>
    </q-form>
    <div>
      <br>
      <label name="nama" style=" font-size: 40px;">{{ datas.name }}</label><br>
      <label usia="usia" style=" font-size: 40px;">{{ datas.age }}</label>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      form: {
        name: null,
        age: null
      },
      datas: {
        name: null,
        age: null
      },
      accept: false
    }
  },

  methods: {
    onSubmit () {
      this.datas = this.form
      console.log(this.datas)
    },

    onReset () {
      this.form.name = null
      this.form.age = null
      this.accept = false
    }
  }
}
</script>
