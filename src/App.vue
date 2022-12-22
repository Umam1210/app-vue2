<template>
  <div class="p-5" style="background-color: lightcoral; height: 100vh;">
    <b-card>
      <p class="fs-2">{{ jokes?.setup }}</p>
      <p class="fs-5">{{ jokes?.punchline }}</p>
      <div class="d-flex justify-content-end">
        <button class="bg-danger rounded border border-none text-white py-1 px-4" @click="reloadPage">Reload</button>
      </div>
    </b-card>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'App',
  data() {
    return {
      jokes: []
    }
  },

  async mounted() {
    let result = await axios.get("https://official-joke-api.appspot.com/random_joke")
    this.jokes = result?.data
    console.log(this.jokes);
  },
  methods: {
    reloadPage() {
      window.location.reload()
    }
  }
}
</script>


