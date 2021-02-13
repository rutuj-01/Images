<template>
  <div class="container">
    <b-form @submit="onSubmit">
      <b-form-group
        id="input-group-1"
        label="Email address:"
        label-for="input-1"
        description="We'll never share your email with anyone else."
      >
        <b-form-input
          id="input-1"
          v-model="form.email"
          type="email"
          placeholder="Enter email"
          required
        ></b-form-input>
      </b-form-group>

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
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-3" label="Paste your URL :" label-for="input-3">
        <b-form-input
          id="input-3"
          v-model="form.avatar"
          required
        ></b-form-input>
      </b-form-group>

<b-card class="mt-3" header="Form Data Result">
      <pre class="m-0">{{ form }}</pre>
<b-container fluid class="p-4 bg-dark"  >
    <b-row>
        <b-col>
          
          <b-img thumbnail fluid :src="getImage()" alt="Image 1" style="width: 300px ;height: 300px"></b-img>
          <p style="color: white"> Name:  {{ form.name }} </p>
          <p style="color: white">Caption:  {{ form.caption }}</p>
        </b-col>
        
        
    </b-row>
</b-container>
    </b-card>
      <b-button type="submit" variant="primary">Submit</b-button>
    </b-form>
    
  </div>
</template>

<script>
export default {
  data() {
    return {
        form: {
          email: '',
          name: '',
          avatar: '',
          caption: '',

        },
        
      }
    },
    methods: {
      onSubmit() {
        this.getImage();
        // alert(JSON.stringify(this.form))
      },
      getImage()
      {
        return (this.form.avatar);
      }
    }
  }

</script>