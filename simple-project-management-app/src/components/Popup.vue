<template>

  <v-dialog max-width="600px" v-model="dialog">

    <v-btn flat slot="activator" class="success">
      <v-icon left class="white--text">add</v-icon>
      <span>new project</span>
    </v-btn>

    <v-card>
      <v-card-title>
        <h2>Add a new project</h2>
      </v-card-title>

      <v-card-text>
        <!-- ref makes it easier to grab it in methods -->
        <v-form ref="form">
          <v-text-field label="Title" v-model="title" prepend-icon="folder" :rules="inputRules"></v-text-field>
          <v-textarea label="Information" v-model="content" prepend-icon="edit" :rules="inputRules"></v-textarea>

          <!-- date picker -->
          <v-menu>
            <v-text-field :value="formattedDate" :rules="required" slot="activator" label="Due date" prepend-icon="date_range"></v-text-field>
            <v-date-picker v-model="due"></v-date-picker>
          </v-menu>

          <v-spacer></v-spacer>

          <v-btn flat class="success mx-0 mt-3" @click="submit()" :loading="loading">Add project</v-btn>
        </v-form>
      </v-card-text>

    </v-card>

  </v-dialog>

</template>


<script>
import format from 'date-fns/format'

export default {
  data() {
    return {
      title: '',
      content: '',
      due: null,
      inputRules: [
        v => v.length >= 3 || 'Minimum length is 3 characters'
      ],
      required: [
        v => v.length > 0 || 'Field is required'
      ],
      loading: false,
      dialog: false
    }
  },

  computed: {
    formattedDate() {
      return this.due ? format(this.due, 'Do MMM YYYY') : '';
    }
  },

  methods: {
    sleep(ms) {
      return new Promise(resolve => setTimeout(resolve, ms));
    },
    submit() {
      if(this.$refs.form.validate()){
        this.loading = true;

        // simulate service call that takes time
        // had trouble calling sleep, getting error that sleep isn't defined; of course, I had to use this.sleep instead
        this.sleep(1500).then(() => {
          console.log(this.title, this.content, this.due);
          this.loading = false;
          this.dialog = false;
          this.$emit('projectAdded');
        });
      }
    }
  }

}
</script>
