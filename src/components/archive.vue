<template>
  <div class="container">

   <div class="row"> 

    <div class="col-md-4 col-sm-12">

    <form @submit.prevent="addBook">
      <div class="card text-left w-100">

        <div class="card-block">

          <p class="card-text">
          Title : <input type="text" v-model="newBook.title" class="w-100 form-control"> 
          </p>

          <p class="card-text">
          Author : <input type="text"v-model="newBook.author" class="w-100 form-control">
          </p>
          <p class="card-text p-0 m-0">Url :
          <div class="input-group">
            <div class="input-group-addon">http:</div>
            <input type="text" class="form-control" id="inlineFormInputGroup" v-model="newBook.url">
          </div>
          </p>
          <input type="submit" class="btn btn-primary" style="cursor: pointer;" value="Add Book">
      </div>
      </div>
      </form>
    </div>
    <!-- <input type="text" class="form-control">   Search -->
      <div class="col-md-8 col-sm-12">

      <div class="card w-100 m-4">
        <img class="card-img-top" src="" alt="Card image cap">
        <div class="card-header">Book lists</div>
        <div class="card-block">
          <table class="table table-striped">
            <thead>
              <tr>
                <th>#</th>
                <th>Title</th>
                <th colspan="2">Author</th>
              </tr>
            </thead>
            <tbody class="text-left">
              <tr v-for="(book, i) in books">
                <td>{{i+1}}</td>
                <td>
                  <a :href="book.url">{{book.title}}</a>
                </td>
                <td>{{book.author}} </td>
                <td><span style="cursor: pointer;" aria-hidden="true" @click="removeBook(book)"><img src="../assets/clarity-icon/essential-shapes/trash-solid.svg" alt="x" class="shape"></span></td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
  
    </div>
   
   

      </div>
    </form>
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

let booksRef = db.ref('books')

export default {
  firebase: {
    books: booksRef
  },
  data () {
    return {
      newBook: {
        author: '',
        title: '',
        url: ''
      },
      removeSuccess: true
    }
  },
  methods: {
    addBook () {
      booksRef.push(this.newBook)
      this.newBook.title = ''
      this.newBook.author = ''
      this.newBook.url = ''
    },
    removeBook (book) {
      booksRef.child(book['.key']).remove()
      setInterval(() => {
        this.removeSuccess = false
      }, 3000)
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
.shape{
  height: 20px;
  width: 20px;
}

</style>
