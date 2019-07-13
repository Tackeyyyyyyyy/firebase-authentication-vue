<template>
  <div class="hello">
    <h1>ようこそ {{ name }}!!</h1>
    <h1>{{ msg }}</h1>
  </div>
</template>

<script>
  import firebase from 'firebase'

  export default {
    name: 'HelloWorld',
    data () {
      return {
        msg: 'ログイン成功',
        name: firebase.auth().currentUser.email
      }
    },
    methods: {
      signOut: function () {
        firebase.auth().signOut().then(() => {
          this.$router.push('/signin')
        })
      }
    }
  }
</script>
