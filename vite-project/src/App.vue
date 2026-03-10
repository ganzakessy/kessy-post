<script>
export default {
  data() {
    return {
      posts: []
    }
  },

  mounted() {
    fetch("https://dummyjson.com/posts")
      .then(res => res.json())
      .then(data => {
        this.posts = data.posts
      })
  }
}
</script>

<template>
  <div class="container">
    <h1 class="title">Posts API</h1>

    <div class="posts">
      <div class="post-card" v-for="post in posts" :key="post.id">
        <h2>{{ post.title }}</h2>
        <p class="body">{{ post.body }}</p>

        <div class="info">
          <span>👍 {{ post.reactions }}</span>
          <span>ID: {{ post.id }}</span>
        </div>

        <button class="btn">Read More</button>
      </div>
    </div>
  </div>
</template>

<style>
body{
  margin:0;
  font-family: Arial, Helvetica, sans-serif;
  background:black;
}

.container{
  padding:40px;
}

.title{
  text-align:center;
  color:green;
  font-size:42px;
  margin-bottom:40px;
  letter-spacing:2px;
}

.posts{
  display:grid;
  grid-template-columns: repeat(auto-fit,minmax(280px,1fr));
  gap:25px;
}

.post-card{
  background:white;
  padding:20px;
  border-radius:10px;
  border-top:5px solid green;
  box-shadow:0 6px 15px rgba(0,0,0,0.4);
  transition:0.3s;
}

.post-card:hover{
  transform:scale(1.05);
}

.post-card h2{
  color:wheat;
  margin-bottom:10px;
}

.body{
  color:#444;
  margin-bottom:15px;
}

.info{
  display:flex;
  justify-content:space-between;
  margin-bottom:15px;
  font-weight:bold;
  color:green;
}

.btn{
  background:green;
  color:white;
  border:none;
  padding:10px 15px;
  border-radius:6px;
  cursor:pointer;
  font-weight:bold;
}

.btn:hover{
  background:black;
}
</style>