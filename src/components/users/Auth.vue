<template>
    <div id="auth" class='auth'>
      <amplify-authenticator
        username-alias="email"
        v-if="authState !== 'signedin'"
      >
        <amplify-sign-up
          slot="sign-up"
          username-alias="email"
          :form-fields.prop="formFields"
          header-text="Sign Up"
          submit-button-text="Sign Up"
        ></amplify-sign-up>
      </amplify-authenticator>
    </div>
</template>

<script>
import { onAuthUIStateChange } from '@aws-amplify/ui-components';

export default {
  name: 'Auth',
  data () {
    return {
      user: undefined,
      authState: undefined,
      formFields: [
        {
          type: 'email',
          label: 'Email Address',
          placeholder: 'Enter your email address',
          required: true
        },
        {
          type: 'password',
          label: 'Password',
          placeholder: 'Enter your password',
          required: true
        }
      ]
    };
  },
  beforeDestroy () {
    return onAuthUIStateChange;
  }
};
</script>

<style scoped>

.auth {
  margin: 0 auto;
  max-width: 460px;
}

amplify-authenticator {
  --container-align: flex-start;
  --container-height: 0;
    padding: 2em;
}
.toast{
  position: static !important;
}
</style>
