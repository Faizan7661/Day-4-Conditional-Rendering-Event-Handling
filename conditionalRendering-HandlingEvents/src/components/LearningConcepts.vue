<script setup>
import {ref} from 'vue'

const awesome = ref(true);

const type = ref(1);
const answers = ref({});


const showArticle = ref(true)
const items = ref([
    {message : "Mohammed Faizan"},
    {message : "Developer"}
])

const details = ref(
    [
        {name : "Mohammed Faizan",designation : "Developer" , stayingIn : "Nampally"},
        {name : "Nikhilesh",designation : "Developer" , stayingIn : "kachiguda"},
        {name : "Tarun",designation : "Developer" , stayingIn : "Hitech City"}

    ]
)
const bookObject = ref({
    title : "Five Feet Apart",
    author : "I dont Know the Name",
    publishedon : "22-Feb-2024"
})

const notAwesomeStyling =ref({
    color : 'red'
})
const userDetails = ref([
    {id : 1, Question : "What Is Your Name?" },
    {id:2, Question: "What is your Designation?"},
    {id : 3, Question : "What are the topics you learned today?"}
])

</script>

<template>
    <div class="container">
      <div class="left">
        <h1 class="title">Learning Conditional Rendering</h1>
        <br>
        <h2 v-if="awesome" class="message">Vue is awesome!</h2>
        <h2 v-else :style="notAwesomeStyling">Oh no 😢</h2>
        <button @click="awesome = !awesome" class="toggle-button">Toggle</button>
        <br>
        <br>
        <hr>
        <div>
          <h1 v-if="type==1">1</h1>
          <h1 v-else-if="type==2">2</h1>
          <h1 v-else-if="type==3">3</h1>
          <h1 v-else>Not A Number</h1>
          <button class="toggle-button" @click="type=2">Change to 2</button>
          <br>
          <button class="toggle-button" @click="type=3">Change to 3</button>
          <br>
          <button class="toggle-button" @click="type=8">Change to none</button>       
        </div>
        <br><hr>
        <template v-if="showArticle">
          <h1 class="title">Showing Article</h1>
          <p class="message">Lorem, ipsum dolor sit amet consectetur adipisicing elit. Quia corporis voluptate harum molestiae similique. Corporis, odio. Quas esse illo animi cumque, accusamus laboriosam earum dignissimos nostrum. Nobis dignissimos quasi quae?</p>
        </template>
        <br>
        <hr>
        <br>
        <div v-show="showArticle">
          <h3 class="title">V-show directive</h3>
          <p class="message">Lorem ipsum dolor sit amet consectetur adipisicing elit. Animi fuga neque iste, deleniti harum quod mollitia architecto ab nisi minus, quaerat dignissimos sit dolor quisquam placeat, necessitatibus nesciunt aliquid totam!</p>
        </div>
        <br>
        <hr>
        <br>
        <div>
          <h1 class="title">V-for directive example</h1>
          <li class="message" v-for="item in items">{{ item.message }}</li>
        </div>
        <br><hr>
      </div>
      <div class="right">
        <div>
          <h1 class="title">Details of My Batch Mates</h1>
          <ul class="message" v-for="detail in details">
            <li>
              Name - {{ detail.name }},
              Designation - {{ detail.designation }},
              Location - {{ detail.stayingIn }}
            </li>
          </ul>
        </div>
        <br><hr>
        <div>
          <h1 class="title">v-for with an Object</h1>
          <li class="message" v-for="(value,key) in bookObject">
            {{ key}} : {{ value }}
          </li>
        </div>
        <br><hr>
        <div>
            
        </div>
      </div>
    </div>

  
    <div>
        <h2>Write your details</h2>
        <ul v-for="user in userDetails" :key="user.id">
        <li>{{ user.Question }}</li>
        <li><input type="text" name="question1" v-model="answers[user.id]" ></li>
        </ul><br>
        <hr>
        <h1 v-for="(answer, id) in answers" :key="id" class="message">{{ answer }}</h1>
    </div>

  
  </template>

<style scoped>
container {
  display: flex;
  justify-content: space-between;
  padding: 20px;
}

.left, .right {
  flex: 1;
}

.title {
  color: #333;
}

.message {
  font-size: 1.2em;
  color: #007bff;
}

.toggle-button {
  padding: 0.5em 1em;
  margin-top: 1em;
  background-color: #007bff;
  color: #fff;
  border: none;
  cursor: pointer;
}
.right {
  margin-left: 20px; 
}

.toggle-button:hover {
  background-color: #0056b3;
}
</style>    