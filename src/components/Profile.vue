<template>
  <div>
      <div class="row">
          <div class="col-md-4">
              <div style="width: 18rem;">
                  <img class="card-img-top" :src="user.avatar_url" />
                  <p id="nome">{{ user.name }}</p>
                  <p id="login">{{ user.login }}</p>
                  <p id="login"><b-icon-briefcase style="color: #000;"></b-icon-briefcase> {{ user.company }}</p>
                  <p id="login"><b-icon-star style="color: #000;"></b-icon-star> {{ }}</p>
                  <p id="login"><b-icon-geo style="color: #000;"></b-icon-geo> {{ user.location }}</p>
                  <p id="login"><b-icon-calendar2-minus style="color: #000;"></b-icon-calendar2-minus> {{ user.public_repos }}</p>
                  <p id="login"><b-icon-people style="color: #000;"></b-icon-people> {{ user.followers }}</p>
              </div>
          </div>
      </div>
  </div>
</template>

<script>
export default {
    props: ['user']
}
</script>

<style>

#nome {
    font-size: 30px;
    margin-top: 5%;
    margin-left: 5px;
}

#login {
    margin-top: -15px;
    margin-left: 5px;
}


</style>