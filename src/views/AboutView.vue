<template>
  <div class="about">
    <h1>This is an about page</h1>
    {{ userData }}
  </div>
</template>

<script>
export default {
  data() {
    return {
      userData: {}
    }
  },
  methods: {
    getUser() {
      console.log(import.meta.env.VITE_TEXT)
      console.log(import.meta.env.VITE_PATH)

      this.$http
        .get(`${import.meta.env.VITE_PATH}?gender=female`)
        .then((res) => {
          console.log(res)
          this.userData = res.data.results
        })
        .catch((err) => {
          console.log(err)
        })
    }
  },
  created() {
    this.getUser()
  }
}
</script>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
