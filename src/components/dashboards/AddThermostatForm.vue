<!-- eslint-disable -->
<template>
  <div>
    <v-container class='form-body'>
      <v-form 
      id='add-dashboard-form' v-model='valid' ref="form" lazy-validation>
        <v-text-field
        v-model='thingName'
        label='iot Name'
        :rules="thingNameRules"
        required
        ></v-text-field>
        <v-text-field
        v-model='remark'
        label='remark'
        required
        ></v-text-field>
          <v-btn id='dashKey' @click='addThermostat(thingName, remark)' :disabled='!valid'  color='white' outlined class='secondary'>
            <p class="info--text mt-4 font-weight-bold">Submit</p>
          </v-btn>
      </v-form>
    </v-container>
  </div>
</template>

<script>
export default {
  name: 'AddThermostatForm',
  data () {
    return {
      remark: '',
      thingName: '',
      thingNameRules: [
        v => !!v || 'key is required'
      ],
      valid: false
    };
  },
  methods: {
    addThermostat (thingName, remark) {
      const dash = {
        thingName: thingName,
        remark: remark
      };
      this.$store.dispatch('addThermostat', dash);
      this.$refs.form.reset();
    }
  }
};
</script>

<style lang="css" scoped>

</style>
