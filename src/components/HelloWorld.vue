<template>
  <div class="container">
    <b-form>
      <b-form-group id="input-group-2" label="Your Name:" label-for="input-2">
        <b-form-input
          id="input-2"
          v-model="form.name"
          placeholder="Enter name"
          required
        ></b-form-input>
      </b-form-group>
        <b-form-group id="input-group-4" label="Caption:" label-for="input-4">
        <b-form-input
          id="input-4"
          v-model="form.caption"
          placeholder="Enter caption"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-3" label="Paste your URL :" label-for="input-3">
        <b-form-input
          id="input-3"
          v-model="form.avatar"
          required
        ></b-form-input>
      </b-form-group>
      <b-button type="submit" variant="primary" v-on:click="onSubmit()">Submit</b-button>
    </b-form>    
    <div class="row"  style="margin-top: 30px;">

      <div class="col-4" v-for="(meme,index) in memes[0]" :key="index" style="margin-top: 20px;">
      
    <b-card
      :title="meme.name" 
      :img-src="meme.avatar"
      img-alt="Image"
      img-top
      style="max-width: 20rem;"
      tag="article" 
      class="card h-100"
    >
    {{ meme.caption }}
  </b-card>
</div>
</div>
  </div>
</template>

<script>
  import axios from 'axios'
export default {
  data() {
    return {
        form: {
          
          name: '',
          avatar: '',
          caption: '',
          
        },
        memes:[]
      }
    },
    created(){
      axios.get('http://localhost:8000/api/memes')
            .then(res=>{
                console.log(res.data);
                this.memes.push(res.data);
                // alert(this.memes);

            })
    },
    methods: {
      onSubmit() {
        
        axios.post('http://localhost:8000/api/posts?name='+this.form.name+'&caption='+this.form.caption+'&avatar='+this.form.avatar)  
                .then(res => console.log(res))
                .catch(err => console.log(err));

            },

      getImage()
      {
        return (this.form.avatar);
      }
    }
  }

</script>