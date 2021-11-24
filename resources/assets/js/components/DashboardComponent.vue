<template>
  <div>
    <h1>Greenhouse Signup</h1>
    <b-form @submit="onSubmit" @reset="onReset" v-if="show">
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
          v-model="form.username"
          placeholder="Enter name"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-3" label="Gender:" label-for="input-3">
        <b-form-select
          id="input-3"
          v-model="form.gender"
          :options="genders"
          required
        ></b-form-select>
      </b-form-group>

      <b-button type="submit" variant="primary">Submit</b-button>
      <b-button type="reset" variant="danger">Reset</b-button>
      <b-button v-on:click="adddynamicentries" type="button" variant="danger">Insert Dynamic Entries</b-button>
    </b-form>
    <p class="savedinfo btn-info hide ">Saved</p>
              <table class="tabledata table table-striped table ">
                <thead>
                  <th>Id</th>
                  <th>Username</th>
                  <th>Email</th>
                  <th>Gender</th>
                  <th>Signed On</th>
                </thead>
                <tbody>
                <tr  v-for="user in users" >
                  <td>{{user.id}}</td>
                   <td>{{user.username}}</td>
                    <td>{{user.email}}</td>
                     <td>{{user.gender}}</td>
                      <td>{{user.created_at}}</td>
                </tr>
                </tbody>
              </table>
  </div>
  
</template>

<script>
    export default {

        mounted() {
            jQuery('.savedinfo').hide();
            axios.get('/greenhouse')
                .then((res) => {
                    //Perform Success Action
                    console.log(res.data);
                    this.users = res.data;
                    // jQuery('.tabledata').hide();
                    // jQuery('.tabledata').css('background-color', 'orange');
                    // jQuery('.tabledata').show();

                })
                .catch((error) => {
                    // error.response.status Check status code
                    alert('Can not be saved ! ');
                    console.log(error);

                }).finally(() => {
                    //Perform action in always
                });
        },

        data() {
            return {
                form: {
                    email: '',
                    username: '',
                    gender: null,
                    // checked: []
                },
                genders: [{
                    text: 'Select One',
                    value: null
                }, 'Male', 'Female', 'Neutral'],
                show: true,
                users: [],

            }
        },
        methods: {
            onSubmit(event) {
                event.preventDefault()
                console.log(this.form);
                axios.post('/greenhouse', this.form)
                    .then((res) => {
                        //Perform Success Action
                        // console.log(res.data);
                        this.users = res.data;
                        jQuery('.savedinfo').show();
                        setTimeout(function() {
                            jQuery('.savedinfo').hide();
                        }, 3000);

                    })
                    .catch((error) => {
                        // error.response.status Check status code
                        alert('Can not be saved ! ');
                        console.log(error);

                    }).finally(() => {
                        //Perform action in always
                    });
            },
            onReset(event) {
                event.preventDefault()
                    // Reset our form values
                this.form.email = ''
                this.form.username = ''
                this.form.gender = null
                    // this.form.checked = []
                    // Trick to reset/clear native browser form validation state
                this.show = true
                    // this.$nextTick(() => {
                    //     this.show = true
                    // })
            },
            adddynamicentries(event) {
                event.preventDefault()

                axios.post('/greenhouse')
                    .then((res) => {
                        //Perform Success Action
                        // console.log(res.data);
                        this.users = res.data;
                    })
                    .catch((error) => {
                        // error.response.status Check status code
                        alert('Can not be saved ! ');
                        console.log(error);

                    }).finally(() => {
                        //Perform action in always
                    });
            }
        }
    }
</script>