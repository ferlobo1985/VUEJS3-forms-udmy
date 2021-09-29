<template>
  <form
    @submit="checkForm"
  >
    <div class="row">
      <div class="col-xl-12">
        <h1>Contact us</h1>
        <hr />

        <div class="form-group">
          <label for="name">Name</label>
          <input
            type="text"
            id="name"
            class="form-control"
            v-model.lazy="formData.name"
          />
        </div>
 
        <div class="form-group">
          <label for="email">email</label>
          <input
            type="email"
            id="email"
            class="form-control"
            v-model="formData.email"
          />
        </div>

        <div class="form-group">
          <label for="subject">Subject</label>
          <input
            type="text"
            id="subject"
            class="form-control"
            v-model="formData.subject"
          />
        </div>

        <div class="form-group">
          <label for="message">Message</label>
          <textarea
            class="form-control"
            rows="3"
            id="message"
            v-model="formData.message"
          ></textarea>
        </div>


        <div class="form-group">
            <h5>Want more spam ? </h5>
            <div class="form-check">
                <input class="form-check-input" type="checkbox" value="Newsletter" id="newsletter"
                v-model="formData.extras"
                >
                <label class="form-check-label" for="newsletter">
                    Newsletter
                </label>
            </div>
            <div class="form-check">
                <input class="form-check-input" type="checkbox" value="Promotions" id="promotions"
                v-model="formData.extras"
                >
                <label class="form-check-label" for="newsletter">
                    Promotions
                </label>
            </div>
         </div>

        <div class="form-group">
            <h5>What are you ? </h5>
            <div class="form-check">
                <input class="form-check-input" type="radio" id="human" value="human" name="origin"
                v-model="formData.gender"
                >
                <label class="form-check-label" for="human">
                    Human
                </label>
            </div>
            <div class="form-check">
                <input class="form-check-input" type="radio" id="alien" value="alien" name="origin"
                v-model="formData.gender"
                >
                <label class="form-check-label" for="alien">
                    Alien
                </label>
            </div>
        </div>

        <div class="form-group">
          <label for="country">Country</label>
          <select class="form-control" id="country"
            v-model="formData.country"
          >
            <option 
              v-for="(country, index) in countries"
              :key="index+country"
            >
              {{ country }}
            </option>
          </select>
        </div>

        <button
          class="btn btn-primary"
        >
          Submit
        </button>

        <hr/>

        <p v-if="this.errors.length">
            <b>Ooops, fix the errors:</b>
            <ul>
              <li v-for="error in errors" :key="error">
                {{ error }}
              </li>
            </ul>
        </p>

       
      </div>
    </div>
  </form>
</template>


<script>
  export default {
    data(){
      return {
        errors:[],
        countries:[
          'EEUU',
          'India',
          'China',
          'Russia',
          'Israel'
        ],
        formData:{
          name:'',
          email:'',
          subject:'',
          message:'',
          extras:[],
          gender:'alien',
          country:''
        }
      }
    },
    methods:{
      checkForm(e){
        e.preventDefault();
        this.errors = [];

        if(!this.formData.name){
          this.errors.push('Sorry, the name is required')
        }

        if(!this.formData.email){
          this.errors.push('Sorry, the email is required')
        } else if(!this.validEmail(this.email)){
          this.errors.push('Sorry, the email is not valid')
        }

        if(!this.errors.length){
          this.submitForm()
        }

      },
      submitForm(){
        console.log(JSON.stringify(this.formData))
      },
      validEmail(email){
        const re = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;

        return re.test(email);
      }
    }
  }
</script>