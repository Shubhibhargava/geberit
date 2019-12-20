<template>
   <div> <h1>hii {{ users.email }}    {{name}}</h1></div>
</template>

<script>
  export default {
    data() {
      return {
        has_error: false,
        users: null,
        name:sessionStorage.name
      }
    },
    mounted() {
      this.getUsers()
    },
    methods: {
      getUsers() {
        this.$http({
          url: `users/`+this.$route.params.id,
          method: 'GET'
        })
            .then((res) => {
              this.users = res.data.user
            }, () => {
              this.has_error = true
            })
      }
    }
  }
</script>