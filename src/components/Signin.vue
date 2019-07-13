<template>
  <div class="signin">
    <h2>ログイン</h2>
    <input type="text" placeholder="Username" v-model="username">
    <input type="password" placeholder="Password" v-model="password">
    <button @click="signIn">ログイン</button>
    <router-link to="/signup">アカウント作成</router-link>
  </div>
</template>

<script>
  import firebase from 'firebase'
  export default {
    name: 'Signin',
    data: function () {
      return {
        username: '',
        password: ''
      }
    },
    methods: {
      signIn: function () {
        firebase.auth().signInWithEmailAndPassword(this.username, this.password).then(
          user => {
            alert('Success!')
            this.$router.push('/')
          },
          err => {
            alert(err.message)
          }
        )
      }
    }
  }
</script>



