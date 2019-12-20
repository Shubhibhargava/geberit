<template>
     <div class="inner shadow p-3 mb-5 bg-white rounded">
      <nav class="navbar navbar-expand-lg navbar-light bg-light">
      
     <a class="navbar-brand" href="#"> <img class="three" src="/images/three.png" ></a>
     <a class="navbar-brand" href="#"> <img class="logo" src="/images/logo.png" ></a>
  
  <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
    <span class="navbar-toggler-icon"></span>
  </button>

  <div class="collapse navbar-collapse" id="navbarSupportedContent">
    <ul class="navbar-nav mr-auto">
     
      
      <div v-if="$auth.check(1)">
            <li class="nav-item"  v-for="(route, key) in routes.user" v-bind:key="route.path">
                <router-link class="nav-link" :to="{ name : route.path }" :key="key">
                    {{route.name}}
                </router-link>
            </li>
        </div>

        <div v-if="$auth.check(2)">
            <li class="nav-item"  v-for="(route, key) in routes.admin" v-bind:key="route.path">
                <router-link class="nav-link" :to="{ name : route.path }" :key="key">
                    {{route.name}}
                </router-link>
            </li>
            </div>

    </ul>
   <form class="form-inline ">
   <!-- Search form -->
   <div id="search-wrapper">
     <div id="s">
<input  @focus="magic_flag = true"  class="form-control searchForm" type="text" placeholder="Search..." aria-label="Search">


<div v-if='magic_flag' id ="oprationDiv" class="popover ls">
    <div class="triangle"></div>
    <div class="popover-content">
        <button type="button">Template</button>
        <button type="button">Task</button>
        <button type="button">Controller</button>
    </div>
</div>
     </div>
   </div>
  </form>&nbsp;&nbsp;&nbsp;&nbsp;
  <div v-if="$auth.check()">
    
                <a href="#" class="btn btn-primary" @click.prevent="$auth.logout()">Logout</a>
           
  </div>
   <div v-if='!$auth.check()'>
  <router-link :to="{ name: 'login' }"><button class="btn btn-primary login">Log in</button></router-link>&nbsp;
  <router-link :to="{ name: 'register' }"><button class="btn btn-primary">Sign up</button></router-link>
  </div>
  </div>
  <!-- fdjhkgdf -->
       
    </nav>
     </div>
</template>
<style scoped>
.s{
  position: relative;
}
.ls{
  position: absolute ;
  top: 10% !important;
  left: 3%;
 
}
.searchForm{
    width: 50%;
    height: 60%;
    margin-left: -50%;
    margin-top: -1.2%;
    position: absolute;
}
.login{
    background-color:#E5EEF1 ;
    color:#036B8E ;
}
.logo{
  width: 80%;
  margin-bottom: 5%;
}
.me{
    
    border-top: orange solid 3px;
}
nav{
margin-left:10%;
    width:80%;
    padding: 0 20px;
    position: relative;
   
}

.panel-body{
  align-content: center;

}
.inner{
  height: 10%;
  padding: 0 !important;
}


.foot{
  margin-top: 40%;
  overflow: hidden;
}




#oprationDiv{
 height: 300%;
  width: 1000% !important;
  border-radius: 10px;
  margin-top: 5%;
  margin-left: 37%;
  padding:10px;
}

.popover>.triangle, .popover>.triangle:after {
    position: absolute;
    display: block;
    width: 0;
    height: 0;
    border-style: solid;
    border-width: 10px;
    border-top-width: 0;
    border-color: transparent;
}

.popover>.triangle {
    top: -10px;
    border-bottom-color: grey;
}

.popover>.triangle:after{
    top: 11px;
    margin: -10px;
    content: " ";
    border-bottom-color: #fff;
}

#oprationDiv>.triangle {
    left: 10px;
}





</style>
<script>
  export default {
    data() {
      return {
        magic_flag:false,
        routes: {
          // UNLOGGED
          unlogged: [
            {
              name: 'Register',
              path: 'register'
            },
            {
              name: 'Log in',
              path: 'login'
            }
          ],
          // LOGGED USER
          user: [
            {
              name: 'Dashboard',
              path: 'dashboard'
            }
          ],
          // LOGGED ADMIN
          admin: [
            {
              name: 'Dashboard',
              path: 'admin.dashboard'
            },
            //{
            //   name: 'View User',
            //   path: 'viewuser'
            // }
          ]
        }
      }
    },
    mounted() {
      //
    }
  }
</script>