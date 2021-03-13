<template>
  <div class="welcome container">
    <p>Welcome</p>
    <div v-if="showLogin">
      <h2>Login</h2>
      <LoginForm @login="enterChat" />
      <p>No account yet? <span @click="showLogin = false">Click here to sign up!</span></p>
    </div>
    <div v-else>
      <h2>Sign Up</h2>
      <SignupForm @signup="enterChat" />
      <p>Already registered? <span @click="showLogin = true">Click here to log in!</span></p>
    </div>
  </div>
</template>

<script>
import LoginForm from '../components/LoginForm.vue'
import SignupForm from '../components/SignupForm.vue'
import { ref } from 'vue'
import { useRouter } from 'vue-router'

export default {
  components: { LoginForm, SignupForm },
  setup() {
    const showLogin = ref(true)
    const router = useRouter()
    const enterChat = () => {
      router.push({ name: 'Chatroom' })
    }
    return { showLogin, enterChat }
  }
}
</script>

<style>
  .welcome {
    text-align: center;
    padding: 20px 0px;
  }
  .welcome form {
    width: 300px;
    margin: 20px auto;
  }
  .welcome label {
    display: block;
    margin: 20px 0 10px;
  }
  .welcome span {
    font-weight: bold;
    text-decoration: underline;
    cursor: pointer;
  }
  .welcome input {
    width: 100%;
    padding: 10px;
    border-radius: 20px;
    border: 1px solid #eee;
    outline: none;
    color: #999;
    margin: 10px auto;
  }
  .welcome button {
    margin: 20px auto;
  }
</style>