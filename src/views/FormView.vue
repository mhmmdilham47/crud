<template>
  <h2>
    <div>
      <h1>Silahkan Masukkan Data Diri Anda</h1>
      <form @submit.prevent="submitForm">
        <div>
          <label for="name">Nama Lengkap</label>
          <input
            type="text"
            id="name"
            v-model="name"
            placeholder="Enter your name"
          />
        </div>
        <div>
          <label for="email">Alamat Email</label>
          <input
            type="email"
            id="email"
            v-model="email"
            placeholder="Enter your email"
          />
        </div>
        <div>
          <label for="password">Password</label>
          <input
            type="password"
            id="password"
            v-model="password"
            placeholder="Enter password"
          />
        </div>
        <div>
          <button @click="addUser" type="submit">Submit</button>
        </div>
      </form>
    </div>
  </h2>
</template>

<script>
import { axios } from 'axios';

export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'users',
  data() {
    return {
      name: "",
      email: "",
      password: "",
    };
  },
  methods: {
    submitForm() {
      const formData = {
        name: this.name,
        email: this.email,
        password: this.password,
      };
      console.log(formData);
      
      axios.post('http://localhost:3000/user', formData)
        .then(res => {
          console.log("data inserted", res.data);
          alert(res.data.message);
          /*
                      this.formData = {
                        name: '',
                        email: '',
                        password: ''
                      }*/
        })
        .catch(function (error) {
          if (error.response) {
            // The request was made and the server responded with a status code
            // that falls out of the range of 2xx
            console.log(error.response.data);
            console.log(error.response.status);
            console.log(error.response.headers);
          } else if (error.request) {
            // The request was made but no response was received
            // `error.request` is an instance of XMLHttpRequest in the browser and an instance of
            // http.ClientRequest in node.js
            console.log(error.request);
          } else {
            // Something happened in setting up the request that triggered an Error
            console.log('Error', error.message);
          }
          console.log(error.config);
        });
    },
//what wrong with this project?
    /*
    addUser(data) {
        axios.post('http://localhost:3000/user', data)
        .then(res => {
            console.log("data inserted", res.data);
            alert(res.data.message);
/*
            this.formData = {
              name: '',
              email: '',
              password: ''
            }
        })
        .catch(function (error) {
          if (error.response) {
            // The request was made and the server responded with a status code
            // that falls out of the range of 2xx
            console.log(error.response.data);
            console.log(error.response.status);
            console.log(error.response.headers);
          } else if (error.request) {
            // The request was made but no response was received
            // `error.request` is an instance of XMLHttpRequest in the browser and an instance of
            // http.ClientRequest in node.js
            console.log(error.request);
          } else {
            // Something happened in setting up the request that triggered an Error
            console.log('Error', error.message);
          }
          console.log(error.config);
        });
    }*/
  },
};
</script>

<style>
form {
  text-align: center;
  background-color: #f4f4f4;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.2);
  max-width: 400px;
  margin: 0 auto;
}

h1 {
  font-size: 24px;
  margin-bottom: 20px;
}

label {
  font-size: 16px;
  display: block;
  margin-bottom: 5px;
  margin-top: 5px;
}

input {
  width: 100%;
  padding-top: 8px;
  padding-bottom: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 16px;
  margin-bottom: 20px;
}

button {
  background-color: #5889f2;
  color: #f4f4f4;
  border: none;
  font-weight: bold;
  margin-top: 10px;
  margin-bottom: 20px;
  padding: 10px 20px;
  border-radius: 4px;
  font-size: 16px;
  cursor: pointer;
  width: 100%;
  transition: background-color 0.3s;
}

h3 {
  background-color: #5889f2;
  border: none;
}

body {
  background-color: aqua;
}
</style>
