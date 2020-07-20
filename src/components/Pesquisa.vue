<template>
    <div class="container">
        <img class="imagem" src="./../../public/img/gitsearch.jpg">
        <div class="form">
            <b-form @submit.stop.prevent id="form-control" >
                <input v-model="username" class="nomeusu" type="text"> 
                <button v-on:click="getUser" class="btn"><b-icon-search style="color: #FFF;"></b-icon-search></button>
                <b-form-invalid-feedback :state="validation">
                  Usuário não encontrado
                </b-form-invalid-feedback>
            </b-form>
        </div>

        <div class="row mt-3" v-if="user.length !== 0">
          <div id="userdiv" class="col-md-4">
            <Profile :user="user"/>
          </div> 
          <div id="repodiv" class="col-md-6">
            <Repo v-for="repo in repos" :key="repo" :repo="repo"/>  
          </div> 
      </div>
    </div>
</template>

<script>
import Profile from './Profile.vue'
import Repo from './Repo.vue'
import axios from 'axios'

export default {
  name: 'App',
  data() {
    return {
      github: {
        url: 'https://api.github.com/users',
        client_id: 'Iv1.98adcb3574d860ea',
        client_secret: '010c6066306a3f5e21354673d6a13fd4fe87078e',
        count: 7,
        sort: 'created: asc'
      },
      user: [],
      repos: [],
      username: "",
      valid: 3
    }
  },
  components: {
    Profile,
    Repo,
  },
  computed: {
    validation() {
      return this.valid > 2
    }
  },
  methods: {
    getUser(){
      const user = this.username;
      const self = this;
      const { url, client_id, client_secret, count, sort } = this.github;
  
      axios.get(`${url}/${user}?client_id=${client_id}&client_secret=${client_secret}`).then(({data}) => this.user = data)
        .catch(function(){
            self.valid = 1;
        });
      this.valid = 3;
        
      axios.get(`${url}/${user}/repos?per_page=${count}&sort=${sort}&client_id=${client_id}&client_secret=${client_secret}`).then(({data}) => this.repos = data);
    },
  }
}
</script>

<style>
.container{
    margin-top: 2%;
    align-items: center;
}

#userdiv {
  position: absolute;
  margin-left: 185px;
}

#repodiv {
  position: absolute;
  margin-left: 570px;
}

img.imagem{
    display: block;
    margin-left: auto;
    margin-right: auto;
    margin-top: auto;
    z-index: 10;
}

.form {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

.nomeusu{
    width: 650px;
    height: 40px;
    border: 2px solid black;
    outline: none;
}

.btn {
    background-color: black;
    margin-bottom:0.8%;
    border-width: 2px;
    width: 100px;
    border-radius: 0px;
}

</style>