<template>
  <div class="createUser">
    <h2>アカウント作成</h2>
    <input type="text" placeholder="Username" v-model="username">
    <input type="password" placeholder="Password" v-model="password">
    <button @click="createUser">アカウント作成</button>
    <p>既にアカウントを持っている
      <router-link to="/signin">ログイン</router-link>
    </p>
  </div>
</template>

<script>
  import firebase from 'firebase'
  export default {
    name: 'createUser',
    data () {
      return {
        username: '',
        password: ''
      }
    },
    methods: {
      createUser: function () {
        firebase.auth().createUserWithEmailAndPassword(this.username, this.password)
          .then(user => {
            alert('Create account!!!')
          })
          .catch(error => {
            alert(error.message)
          })
      }
    }
  }
</script>
