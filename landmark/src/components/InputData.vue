<template>

  <form>
      <div type="submit" class="submit">
        <button>Delete Details</button>
        </div>
        
    <label>Title: {{title}}</label>
    <input type="text" required v-model="posts.title">

<label>Category: {{category}}</label>
<select v-model="posts.category">
        <option value="Developer">Web Developer</option>
        <option value="Designer">Web Designer</option>
    </select>

<label>Description: {{description}}</label>
<input type="description" required v-model="posts.description">

<label>Image URL:</label>
    <input type="text" v-model="posts.tempImage" @keyup.alt="addImage">
    <div v-for="image in images" :key="image" class="pill">
    <span @click="deleteImage(image)">{{image}}</span>
    </div>

<label>Terms accepted: {{terms}}</label>
<input type="checkbox" required v-model="posts.terms">


  </form>
</template>
<script>
import * as Vue from 'vue' 
import axios from 'axios'
import VueAxios from 'vue-axios'

export default {
      
      data() {
          
          return {
              posts: {
                  title: null,
              description: "",
              category: "",
              terms: false,
              names: [],
              tempImage: "",
              images: [],
              descriptionError: "",
              }
              
          }
      },
      methods: {
          addImage(e) {
              if (e.key === "," && this.tempImage) {
                  if (!this.images.includes(this.tempImage)) {
                     this.images.push(this.tempImage)
                  }
                  this.tempImage =""
              }
          },
          deleteImage(image) {
              this.images = this.images.filter((item) => {
                  return image !== item
              })
          },
          handleSubmit(e) {
              this.axios.post('http://localhost:3000/posts',this.posts)
              .then((result)=>{
                  console.warn(result)
              })
              e.preventDefault();
              this.descriptionError = this.description.length > 5
               ? "" : "description must b e atleat 6 chars long"
               if (!this.descriptionError) {
                   console.log('title: ',this.title)
                   console.log('description: ',this.description)
                   console.log('category: ', this.category)
                   console.log('images: ', this.images)
                   console.log('terms accepted: ', this.terms)
               }
          }
      },
    //   mounted() {
    //       fetch('http://localhost:3000/afford')
    //        .then(res => res.json())
    //        .then(data => this.afford = data)
    //        .catch(err => console.log(err.message))
    //   }
  }

  const app = Vue.createApp()
app.use(VueAxios, axios)
</script>

<style>
  form {
      max-width: 420px;
      margin: 30px auto;
      background: white;
      text-align: left;
      padding: 40px;
      border-radius: 10px;
  }
  label {
      color: #aaa;
      display: inline-block;
      margin: 25px 0 15px;
      font-size: 0.6em;
      text-transform: uppercase;
      letter-spacing: 1px;
      font-weight: bold;
  }
  input, select {
      display:block;
      padding: 10px 6px;
      width: 100%;
      box-sizing: border-box;
      border: none;
      border-bottom: 1px solid #ddd;
      color: #555;
  }
  input[type="checkbox"] {
      display: inline-block;
      width: 16px;
      margin: 0 10px 0 0;
      position: relative;
      top: 2px;
  }
  .pill {
      display: inline-block;
      margin: 20px 10px 0 0;
      padding: 6px 12px;
      background-color: #eee;
      border-radius: 20px;
      font-size: 12px;
      letter-spacing: 1px;
      font-weight: bold;
      color: #777;
      cursor: pointer;
  }
  button {
      background: #0b6dff;
      border: 0;
      padding: 10px 20px;
      margin-top: 20px;
      color: white;
      border-radius: 20px;
  }
  .submit {
      text-align: center;
  }
  .error {
      color: #ff0062;
      margin-top: 10px;
      font-size: 0.8em;
      font-weight: bold;
  }
</style>
