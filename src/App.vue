<script>
export default {
  data: () => ({
    // posts: []
    usersList: [
    
    ],
    message:'',
    firstName:'',
    email:'',
    message: '',
    messageClasses: '',

  }),
  created() {
    // console.log('fetch start')
    // fetch('https://jsonplaceholder.typicode.com/users')
    // .then(function (res) { return res.json()})
    // .then(json => this.usersList = json)
    // console.log('fetch end')
  }
  ,methods:{
    addUser(){
      if(this.firstName===''||this.email===''){
        this.showMsg('please enter Values' ,true)
            return
      
      }
      this.usersList.push({name:this.firstName,email:this.email})
      this.firstName=''
      this.email=""
      this.showMsg('user added suceccsfully')
    }
    ,
    showMsg(message ,isError = false){
if(isError){
 this.messageClasses='error' 
}
else{
  this.messageClasses='success' 
}
this.message=message
setTimeout(this.removeMsg, 3000)
    },


    
    removeMsg(){
 this.message=" "
 this.messageClasses=""
    },
    removeAllUser(){
      this.usersList=[]
this.showMsg('userlist is emptied')
      
    },
    removeLastUser(){
      this.usersList.pop()
    },
    removeFirstUser(){
     this.usersList.shift() 
    },


  }
}
</script>

<template>
  <header class=" header has-text-centered has-text-white  is-size-5 py-3 is-fixed-top">
    login Form with vuejs
   </header>
  <!-- <nav>
    <div class="logo">
   
     login with vueComponents 
    </div>
    <div class="menu">
      <ul>
        <li> home</li>
        <li> About</li>
        <li> services</li>
        <li> contact</li>
      </ul> 
    </div>
  </nav> -->
<div class="container">

 <div class="form">
  <form id="my-form" @submit.prevent="addUser">
<h2> from with VueComponents</h2>

<div v-if="message" class="msg" :class="messageClasses" v-text="message"></div>

              <div>
                <label for="name">Name</label>
                <input type="text" v-model.trim="firstName" name="name"  >
              </div>
              <div>
                <label for="email">email</label>
                <input type="email" name="email" v-model.trim="email">
              </div>
              <div>
                <button class="button">submit</button>
              </div>
 </form>
<div class="buttons ">
<button @click="removeAllUser" > remove all users</button>
<button @click="removeFirstUser" > remove first user</button>
<button @click="removeLastUser" > remove last user</button>
  </div>
 
 <ul class="items" >
  <li  class="item" v-for="(user, i) in usersList">
    #{{ i + 1 }} {{ user.name }}: {{ user.email }}
    <span class="icon" @click="removeTask(i)"> <i class="fa fa-trash"></i></span>

  </li>
 </ul>

        
    
        
 </div>
 </div>

  <!-- <main>
    <div class="row">
      <div class="column is-4" v-for="post in posts"> // for (let i = 0; i<arr.length; i++) {
        <div class="card">
          <h4>{{ post.title }}</h4>
          <p>{{ post.body }}</p>
        </div>
      </div>
    </div>  }//coment
  </main> -->
</template>


<style>
*{
  margin:0;
  padding: 0;
}
body{
    background-image:url('./assets/black-bg.jpg');
    background-size: cover;
    height: 100vh;
}
nav{
  background-color: #b1cfed;
  /* height:30px; */
  /* padding: 10px; */
  /* display: flex;
  align-items: center;
  justify-content: space-around; */
  text-align: center;
  line-height: 60px;
  height: 60px;
 
}
.menu ul{
  display: flex;
  list-style: none;
 
}
.menu ul li{
  padding: 10px;
  color: white;
font-size: 18px;
border-radius: 3px;

}

.container {
    margin: auto;
    width: 500px;
    overflow: auto;
    padding: 3rem 2rem;
  }
#my-form{
  background-color: #91a1cc;
    /* margin: 200px auto; */
    padding: 20px;
    /* position: absolute;
    left: 43%;
    top: 50%; */
    border-radius: 23px;
    /* height: 100px; */
    margin-top: 82px;
}
#my-form label {
    /* display: block;
    font-size: 1.2rem; */
    font-weight: bold;
    color: aliceblue;
    margin: 10px 0 ;
  }
header{
  background-color: #292e7ebb;
    position: fixed;
    width: 100%;
    z-index: 9;
    height: 40px;
    color: white;
    text-align: center;
    line-height: 40px;
    padding: 10px;
}
/* input[type="text"] ,input[type="email"]{
  padding: 7px;
    background: none;
    border: none;
    border-bottom: 1px solid #2c2929;
    outline: none;
    color: white;
    margin-bottom: 20px;
} */
#my-form  input[type='text'] ,input[type='email'] {
    width: 100%;
    padding: 1px 5px;
    /* border-radius: 5px; */
    border: none;
    border-bottom: 1px solid rgb(97, 93, 93);
    background: none;
    outline: none;
    /* color: white; */
    font-size: 16px;
    caret-color: #91a1cc;
    margin-bottom: 10px;
    margin-top: 17px;
  }
  ::placeholder{
    /* color:#b1cfed8c; */

  }
  .button{
    padding: 10px 18px;
    /* text-align: center; */
    border: none;
    border-radius: 8px;
    /* margin: 0 auto; */
    width: 95%;
    margin-top: 6%;
   
  }
  h2{
    text-align: center;
    color: white;
  }
  li{
    background-color: #91a1cc;
    margin-bottom: 10px;
    padding: 10px;
    margin-top: 10px;
    border-radius: 5px;
  }
  .error{
    background-color: red;
    padding: 10px;
    margin:10px 0
  }
  .success{
    background-color: greenyellow;
    padding: 10px;
    margin:10px 0
  }
  .buttons{
    background-color: #91A1CC;
    padding: 10px;
  }
  .buttons button{
    background-color: #fff;
    border-color: #dbdbdb;
    border-width: 1px;
    color: #363636;
    cursor: pointer;
    justify-content: center;
    padding-bottom: calc(0.5em - 1px);
    padding-left: 1em;
    padding-right: 1em;
    padding-top: calc(0.5em - 1px);
    text-align: center;
    white-space: nowrap;
    background-color: #fff;
    border-color: #dbdbdb;
    border-width: 1px;
    color: #363636;
    cursor: pointer;
    justify-content: center;
    padding-bottom: calc(0.5em - 1px);
    padding-left: 1em;
    padding-right: 1em;
    padding-top: calc(0.5em - 1px);
    text-align: center;
    white-space: nowrap;
    margin-bottom: 10px;
    border-radius: 8px;
    margin-right: 10px;
  }
</style>