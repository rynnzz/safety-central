<template>
  <div>
    <header>
      <img src="~/src/assets/unnamed.png" alt="Logo">
      <h1>Cordova Public College</h1>
    </header>

    <body>
      <h2>Safeguarded, Smart, and<br> Effortless Safety Hub</h2>
      <q-form @submit.prevent="register">
        <q-card class="register-form">
          <q-card-section>
            <div class="form-container">
              <br>
              <input v-model="id_num" type="text" id="id_num" class="id" name="id_num" placeholder="ID Number"><br><br>
              <input v-model="fname" type="text" id="fname" class="fname" name="fname" placeholder="First Name"><br><br>
              <input v-model="mname" type="text" id="mname" class="mname" name="mname" placeholder="Middle Name"><br><br>
              <input v-model="lname" type="text" id="lname" class="lname" name="lname" placeholder="Last Name"><br><br>
              <input v-model="address" type="text" id="address" class="address" name="address"
                placeholder="Address"><br><br>
              <input v-model="age" type="text" id="age" class="age" name="age" placeholder="Age"><br><br>
              <input v-model="b_date" type="text" placeholder="Birth Date" id="b_date" class="b_date" name="b_date"
                onfocus="(this.type='date')"><br><br>
              <input v-model="password" type="password" id="password" class="password" name="password"
                placeholder="Password"><br><br>
              <input v-model="confirm_password" type="password" id="confirm_password" class="confirm_password"
                name="confirm_password" placeholder="Confirm Password"><br><br>
              <input v-model="gname" type="text" id="gname" class="gname" name="gname"
                placeholder="Guardian/Parent Name"><br><br>
              <input v-model="g_cnum" type="text" id="g_cnum" class="g_cnum" name="g_cnum"
                placeholder="Guardian/Parent Contact Number"><br><br>
              <input v-model="s_cnum" type="text" id="s_cnum" class="s_cnum" name="s_cnum"
                placeholder="Student Contact Number"><br><br>
              <input v-model="yr_and_sec" type="text" id="yr_and_sec" class="yr_and_sec" name="yr_and_sec"
                placeholder="Year and Section Format Example: 3C"><br><br>
              <select v-model="course" id="course"
                style="width: 250px; background: rgb(31, 32, 35); border: 1px solid rgb(60, 63, 68); border-radius: 10px; color: rgb(247, 248, 248); height: 46px;">
                <option value="" selected disabled>Course</option>
                <option value="BSIT">BSIT</option>
                <option value="BSHM">BSHM</option>
                <option value="BEED">BEED</option>
                <option value="BSED">BSED</option>
              </select><br><br>
              <q-btn type="submit" align="between" class="text-h7" color="accent" label="Register" icon="person"
                style="width: 160px;" />
              <q-btn type="button" class="btn btn-primary" @click="redirectToLogin"
                label="Already have an account? Go back to Login" style="width: 300px; height: 55px;" />
            </div>
          </q-card-section>
        </q-card>
      </q-form>
    </body>
  </div>
  <q-dialog v-model="registrationSuccess" persistent>
    <q-card class="custom-card" style="width: 700px">
      <q-card-section>
        <div class="text-h6">Your registration was successful!</div>
      </q-card-section>
      <div class="footer">
        <button type="button" class="btn btn-success" @click="redirectToLogin">Go to Login</button>
      </div>
    </q-card>
  </q-dialog>
</template>
<script>
import 'bootstrap/dist/css/bootstrap.min.css'
import 'bootstrap/dist/js/bootstrap.bundle.min.js'

export default {
  data() {
    return {
      id_num: '',
      fname: '',
      mname: '',
      lname: '',
      address: '',
      age: '',
      b_date: '',
      password: '',
      confirm_password: '',
      gname: '',
      g_cnum: '',
      s_cnum: '',
      course: '',
      yr_and_sec: '',
      registrationSuccess: false,
      registrationError: ''
    }
  },
  methods: {
    async register() {
      try {
        const response = await fetch('http://localhost/api/register.php', {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json'
          },
          body: JSON.stringify({
            id_num: this.id_num,
            fname: this.fname,
            mname: this.mname,
            lname: this.lname,
            address: this.address,
            age: this.age,
            b_date: this.b_date,
            password: this.password,
            confirm_password: this.confirm_password,
            gname: this.gname,
            g_cnum: this.g_cnum,
            s_cnum: this.s_cnum,
            course: this.course,
            yr_and_sec: this.yr_and_sec
          })
        })

        console.log('Response:', response)

        if (!response.ok) {

          throw new Error('Network response was not ok')
        }

        const contentType = response.headers.get('content-type')

        if (contentType && contentType.includes('application/json')) {
          const responseData = await response.json()

          if (responseData.success) {
            this.registrationSuccess = true

          } else {
            this.registrationError = responseData.message || 'Unknown error during registration.'
          }
        } else {

          this.registrationError = 'Invalid response format. Expected JSON.'
        }
      } catch (error) {
        console.error('Error during registration:', error)
        this.registrationError = 'An error occurred during registration.'
      }
    },
    redirectToLogin() {
      this.$router.push('/')
    }
  }
}
</script>
<style scoped>
body {
  background-color: #292a2d;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;
  height: 100%;
  margin: 0;
  font-family: 'Product Sans', sans-serif;
}

.btn {
  width: 100px;
}

.id,
.fname,
.mname,
.lname,
.address,
.age,
.b_date,
.password,
.confirm_password,
.gname,
.g_cnum,
.yr_and_sec,
.s_cnum {
  padding: 6px 12px;
  background: rgb(31, 32, 35);
  border: 1px solid rgb(60, 63, 68);
  border-radius: 10px;
  color: rgb(247, 248, 248);
  height: 46px;
  appearance: none;
  transition: border 0.15s ease 0s;
  width: 500px;
  font-family: 'Product Sans', sans-serif;
}

header {
  background-color: #1f1f1f;
  color: white;
  padding: 30px;
  display: flex;
  align-items: left;
  justify-content: left;
  width: 100%;
  height: 150px;
}

h1 {
  color: white;
  padding: 20px;
}

h2 {
  color: white;
  padding: 10px;
  text-align: center;
}

header img {
  width: 100px;
  margin-right: 10px;
}

.register-form {
  background-color: #1f1f1f;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.2);
  text-align: left;
  align-items: center;
  width: 700px;
  box-shadow: 0 25.6px 57.6px 0 rgb(0 0 0 / 22%), 0 4.8px 14.4px 0 rgb(0 0 0 / 18%);
}

form {
  align-items: center;
  text-align: center;
  color: white;
}

.custom-card {
  background-color: #1f1f1f;
  color: white;
  font-size: 25px;
  border: 20px;
}
</style>
