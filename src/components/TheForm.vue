<template>
  <form @submit.prevent="SubmitForm">
  <!-----------------------------------V - BIND----------------------------------->
    <div class="form-control">
      <label for="user-name">Your Name</label>
      <input id="user-name" name="user-name" type="text" v-model="name" @blur="validateInput()" />
      <span v-if="validateUserName">Please enter atleast 1 character</span>
    </div>
    <p>{{name}}</p>
    <p>validateUserName : {{validateUserName}}</p>
  <!-----------------------------------V - BIND----------------------------------->
    <div class="form-control">
      <label for="age">Your Age (Years)</label>
      <input id="age" name="age" type="number" v-model="age"/>
    </div>
    <p>{{age}}</p>

    <!-----------------------------------DROP DOWN----------------------------------->
    <div class="form-control">
      <label for="referrer">How did you hear about us?</label>
      <select id="referrer" name="referrer" v-model="hearAboutUs">
        <option value="google">Google</option>
        <option value="wom">Word of mouth</option>
        <option value="newspaper">Newspaper</option>
      </select>
    </div>
    <p>{{hearAboutUs}}</p>

    <!-----------------------------------CHECK BOX----------------------------------->
    <div class="form-control">
      <h2>What are you interested in?</h2>
      <div>
        <input id="interest-news" name="intrestedIn" value="NewsA" type="checkbox" v-model="intrestedIn" />
        <label for="interest-news">News</label>
      </div>
      <div>
        <input id="interest-tutorials" name="intrestedIn" value="Tutorials" type="checkbox" v-model="intrestedIn" />
        <label for="interest-tutorials">Tutorials</label>
      </div>
      <div>
        <input id="interest-nothing" name="intrestedIn" value="Nothing" type="checkbox" v-model="intrestedIn" />
        <label for="interest-nothing">Nothing</label>
      </div>
    </div>
    <p>{{intrestedIn}}</p>

    <!-----------------------------------RADIO BUTTON----------------------------------->
    <div class="form-control">
      <h2>How do you learn?</h2>
      <div>
        <input id="how-video" name="how" type="radio" v-model="learningChoice" />
        <label for="how-video">Video Courses</label>
      </div>
      <div>
        <input id="how-blogs" name="how" type="radio" v-model="learningChoice" />
        <label for="how-blogs">Blogs</label>
      </div>
      <div>
        <input id="how-other" name="how" type="radio" v-model="learningChoice" />
        <label for="how-other">Other</label>
      </div>
    </div>
    <div>
    <p>{{learningChoice}}</p>

      <button>Save Data</button>
    </div>
  </form>
</template>

<script>
  export default {
    computed :{
      validateUserNameInput(){
        return  this.name == '' ? true :false ;
      }
    },
    data(){
      return{
        validateUserName : false,
        name : '',
        age : '',
        hearAboutUs : '',
        intrestedIn : [],
        learningChoice : '',
      }
    },
    methods : {
      validateInput(){
        console.log('blur event called');
         this.validateUserName  = this.name == '' ? true : false;
      },
      SubmitForm(){
        console.log('I am submitted');
      }
    }
  }
</script>

<style scoped>
form {
  margin: 2rem auto;
  max-width: 40rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 2rem;
  background-color: #ffffff;
}

.form-control {
  margin: 0.5rem 0;
}

label {
  font-weight: bold;
}

h2 {
  font-size: 1rem;
  margin: 0.5rem 0;
}

input,
select {
  display: block;
  width: 100%;
  font: inherit;
  margin-top: 0.5rem;
}

select {
  width: auto;
}

input[type='checkbox'],
input[type='radio'] {
  display: inline-block;
  width: auto;
  margin-right: 1rem;
}

input[type='checkbox'] + label,
input[type='radio'] + label {
  font-weight: normal;
}

button {
  font: inherit;
  border: 1px solid #0076bb;
  background-color: #0076bb;
  color: white;
  cursor: pointer;
  padding: 0.75rem 2rem;
  border-radius: 30px;
}

button:hover,
button:active {
  border-color: #002350;
  background-color: #002350;
}
</style>