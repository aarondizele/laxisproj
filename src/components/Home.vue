<template>
  <div class="container-fluid">

    <nav class="navbar navbar-toggleable-md navbar-light fixed-top text-left" style="font-size: 1rem; background: white;">
      <button class="navbar-toggler navbar-toggler-right" type="button" data-toggle="collapse" data-target="#navbarNavDropdown" aria-controls="navbarNavDropdown" aria-expanded="false" aria-label="Toggle navigation"></span>
      </button>
      <a class="navbar-brand" href="#">Laxis Tech.</a>
      <div class="collapse navbar-collapse justify-content-end" id="navbarNavDropdown">
        <ul class="navbar-nav">
           <li class="nav-item dropdown">
            <a class="nav-link dropdown-toggle" href="http://example.com" id="navbarDropdownMenuLink" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false" style="border-bottom: 4px solid #3498db;">
              Services
            </a>
            <div class="dropdown-menu" aria-labelledby="navbarDropdownMenuLink" style="align-text: left">
              <a class="dropdown-item" href="#">Action</a>
              <a class="dropdown-item" href="#">Another action</a>
              <a class="dropdown-item" href="#">Something else here</a>
            </div>
          </li>
          <li class="nav-item becomePartner">
            <a class="nav-link" href="#">Become Partner</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">Contact Us</a>
          </li>
           <li class="nav-item d-flex ">
            <a class="nav-link active mr-sm-2" href="#">En <span class="sr-only">(current)</span></a>
            <span class="mt-2 mr-1 ml-sm-1 mr-sm-1">|</span>
            <a class="nav-link" href="#">Fr </a>
          </li>
        </ul>
      </div>
    </nav>

    <div class="row align-items-center semi-background pl-md-4" style="font-weight: 300;">
      <div class="col-md-7 col-sm-12" >
        <h2 class="pb-4">LAUNCH YOUR PROFESSIONAL WEBSITE TODAY</h2>
        <h5 class="pb-4" style="line-height: 30px;">Because we care about une image, we build the good responsible design to express what your are and the quality of services you offer. <br>Let us build it for you today</h5>
        <button class="btn btn-primary oButton">CONTACT US</button>
      </div>
    </div>

    <!-- <div class="0Banner hidden-sm-down">
    <img src="https://firebasestorage.googleapis.com/v0/b/laxistech-54e69.appspot.com/o/presentation.jpg?alt=media&token=79750d52-599a-49f3-9f82-a1a77d9fc892" alt="" class="">
    </div>   -->

    <div class="row bg-inverse oForm" style="color: white;">
      <div class="col-md-5 pl-md-5 pr-md-5"  v-if="!isSubmit">
      <h3 class="mb-5">Let us know about your project</h3>
        <form @submit.prevent="addNewRequest">

        <div class="input-group">
          <input type="text" class="form-control" placeholder="First name" v-model="newRequest.fname">
          <input type="text" class="form-control" placeholder="Last name" v-model="newRequest.lname">
        </div>

        <input type="text" class="form-control" placeholder="Email" v-model="newRequest.email" email>
        <input type="text" class="form-control" placeholder="Phone" v-model="newRequest.phone" phone>
        <input type="text" class="form-control" placeholder="Society" v-model="newRequest.society">

        <div class="input-group">
          <input type="text" class="form-control" placeholder="City" v-model="newRequest.city">
          <input type="text" class="form-control" placeholder="Country" v-model="newRequest.country">
        </div>

        <input type="submit" class="btn btn-success w-100" value="Continue">

        </form>
      </div>

      <div class="col-md-6" v-else="isSubmit">
        <div class="alert text-uppercase text-center isSubmitted">
          Thanks you, your request was sent and we will contact you as soon as possible
        </div>
      </div>


      <div class="offset-md-1 col-md-6 startinsmall">
        <h2 class="mb-5">Match your project <br/> with your budget</h2>
        <p style="line-height: 30px;">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Repudiandae doloremque, quia, quibusdam quam cum itaque autem modi aliquid quaerat id atque aspernatur eius. Accusantium, odit ratione debitis nobis molestias quis?</p>
      </div>

    </div>

    <div class="row" style="padding: 400px 0"></div>

    <div class="row bg-inverse fullFooter" style="color: white;">

      <div class="col-md-6 align-self-center thatlaxis">
        <h1 class="">So that's Laxis Tech.</h1>
      </div>
      <div class="col-md-6 oFooter">
        <form @submit.prevent="addNewSubscriber">
          <h4 class="mb-4">Get in touch</h4>
          <input type="text" class="form-control" placeholder="Name" v-model="newSubscriber.name">
          <input type="text" class="form-control" placeholder="Email Address" v-model="newSubscriber.email" email>
          <input type="submit" class="btn btn-success" value="Continue">
        </form>
      </div>

      <hr style="width: 100%; height: .5px; background-color: white; background-color: rgba(255,255,255,.3); margin: 50px 0 20px 0;">


      <div class="col-12 d-flex">
        <div class="social mr-4">
          <img src="https://firebasestorage.googleapis.com/v0/b/laxistech-54e69.appspot.com/o/facebook.svg?alt=media&token=5b3e3c03-6f73-4688-a9db-59845002b270" alt="">
        </div>
        <div class="social">
          <img src="https://firebasestorage.googleapis.com/v0/b/laxistech-54e69.appspot.com/o/twitter.svg?alt=media&token=a476db03-6b2a-47f6-a470-e9611ba83184" alt="">
        </div>
      </div>
    </div>

  </div>
</template>

<script>

import Firebase from 'firebase'

let config = {
  apiKey: 'AIzaSyBeAdSk6zAkN7H03WgSmTjUFRwQQ-YZAew',
  authDomain: 'laxistech-54e69.firebaseapp.com',
  databaseURL: 'https://laxistech-54e69.firebaseio.com',
  projectId: 'laxistech-54e69',
  storageBucket: 'laxistech-54e69.appspot.com',
  messagingSenderId: '652978401638'
}

let app = Firebase.initializeApp(config)
let db = app.database()

let booksRef = db.ref('request')
let subscribersRef = db.ref('subscribers')

export default {
  firebase: {
    books: booksRef
  },
  data () {
    return {
      isSubmit: false,
      newRequest: {
        city: '',
        country: '',
        email: '',
        fname: '',
        lname: '',
        phone: ''
      },
      newSubscriber: {
        name: '',
        email: ''
      }
    }
  },
  methods: {
    addNewRequest () {
      booksRef.push(this.newRequest)
      this.isSubmit = true
      this.newRequest.city = ''
      this.newRequest.country = ''
      this.newRequest.email = ''
      this.newRequest.fname = ''
      this.newRequest.lname = ''
      this.newRequest.phone = ''
    },
    addNewSubscriber () {
      subscribersRef.push(this.newSubscriber)
      this.newSubscriber.name = ''
      this.newSubscriber.email = ''
    }
  }

}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

nav{
  height: 70px;
}

button.oButton{
  padding: 18px 26px;
  color: white;
  font-size: 18px;
  outline: none;
  border-radius: 10px;
  font-weight: 400;
}
button{
  cursor: pointer;
}
.shape{
  height: 20px;
  width: 20px;
}
.becomePartner{
  border-radius: 20px;
  padding: 4px 10px;
  background: #3498db;
  color: white;
}
.becomePartner a.nav-link{
  color: white;
}
.carousel-control-prev-icon, .carousel-control-next-icon {
  visibility: hidden;
}

.semi-background, .oForm{
  padding: 160px 0 180px 20px;
}

input[type=text]{
  background: none;
  border-color: white;
  margin-bottom: 20px;
  color: white;
  padding: 14px;
  outline: none;
}
input[type="submit"]{
  border: none;
  background: white;
  color: #333;
  padding: 14px;
  outline: none;
  font-size: 18px;
  cursor: pointer;
}
::placeholder{
  color: white;
}

.isSubmitted{
  border: 2px solid white;
  color: white;
  background: none;
}

.oFooter input[type=text]{
  border: none;
  border-bottom: 1px solid white;
  border-color: rgba(255,255,255,.3);
  padding-bottom: 10px;
  border-radius: none;
  width: 90%;
}
.oFooter{
  position: relative;
}
.oFooter:before{
  content: '';
  height: 110%;
  width: 5px;
  border-left: 1px solid white;
  border-color: rgba(255,255,255,.3);
  position: absolute;
  margin-left: -50px;
}

.social{
  height: 70px;
  width: 70px;
  opacity: .5;
}

.fullFooter{
  padding: 60px 40px;
}

.navbar-light .navbar-nav .nav-link.active, .navbar-light .navbar-nav .nav-link.open, .navbar-light .navbar-nav .open > .nav-link {
    color: #3498db;
}



@media only screen and (max-width: 576px){
}

@media only screen and (max-width: 767px) {
  nav{
    height: auto;
  }
  .fullFooter{
    padding: 40px 20px;
  }
  .becomePartner{
    border-radius:none;
    padding: 0;
    background: none;
  }
  .becomePartner a.nav-link{
    color: #888;
  }
  .startinsmall{
    order: -1;
    margin-bottom: 20px;
  }
  .social{
    height: 40px;
    width: 40px;
    opacity: .5;
  }
  .oFooter:before{
    content: '';
    height: 0;
    width: 0;
    border-left: none;
    border-color: none;
    position: static;
    margin-left: 0;
  }
 }


</style>
