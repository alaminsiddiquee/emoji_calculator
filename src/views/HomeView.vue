<script>
import axios from 'axios'

export default {
  data() {
    return {
      result: 0,
      error: '',
      form: {
        in1: 0,
        in2: 0,
        op: '+',
      },
      options: [
        {text: '👽', value: '+'},
        {text: '💀', value: '-'},
        {text: '👻', value: '*'},
        {text: '😱', value: '/'}
      ]
    }
  },

  methods: {
    submit(e) {
      axios.post('http://127.0.0.1:8000/api/calculate', this.form)
      .then((res) => {
        this.result = res.data.result
        this.error = ''
      })
      .catch((error) => {
        this.error = error.response.data.message
      })
      e.preventDefault()
    }
  }
}
</script>

<template>
  <main>
    <form class="form" @submit="submit" method="post">
      <div class="form-control">
        <input type="text" v-model="form.in1" placeholder="Enter 1st operand" class="input" />
      </div>
      <div class="form-control">
        <select v-model="form.op">
          <option v-for="option in options" :value="option.value">
            {{ option.text }}
          </option>
        </select>
      </div>
      <div class="form-control">
        <input type="text" v-model="form.in2" placeholder="Enter 2nd operand" class="input" />
      </div>
      <div class="form-control">
        <input type="submit" value="Calculate" class="btn btn-block" />
      </div>

      <div class="form-control">
        <p>Result: {{ result }}</p>
      </div>

      <p class="error">{{ error }}</p>

    </form>
  </main>
</template>
