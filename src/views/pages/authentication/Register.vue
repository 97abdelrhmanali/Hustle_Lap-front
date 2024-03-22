<template>
  <div class="auth-wrapper auth-v2">
    <b-row class="auth-inner m-0">



      <!-- Left Text-->
      <b-col
        lg="8"
        class="d-none d-lg-flex align-items-center p-5 parent"
        :style="{ backgroundImage:'linear-gradient(rgba(0,0,0,0.7),rgba(0,0,0,0.7)), url(' + imgUrl + ')' }"
      >
      
        
        <div class="w-100 d-lg-flex align-items-center justify-content-center px-5">
          <!-- <b-img
            fluid
            :src="imgUrl"
            alt="Login V2"
          /> -->

          <h1 style="font-weight: bolder; font-size: 50px; color: beige;" >
            Let's start playing the game to better your future
          </h1>
        </div>
      </b-col>
      <!-- /Left Text-->

      <!-- Register-->
      <b-col
        lg="4"
        class="d-flex align-items-center auth-bg px-2 p-lg-5"
      >

         <!-- Brand logo-->
        <b-link class="brand-logo d-flex justify-content-end w-75">
            <vuexy-logo />
        </b-link>
        <!-- /Brand logo-->

        <b-col
          sm="8"
          md="6"
          lg="12"
          class="px-xl-2 mx-auto"
        >
          <b-card-title class="mb-1">
            Student Sign Up
          </b-card-title>
          <!-- <b-card-text class="mb-2">
            Make your app management easy and fun!
          </b-card-text> -->

          <!-- form -->
          <validation-observer
            ref="registerForm"
            #default="{invalid}"
          >
            <b-form
              class="auth-register-form mt-2"
              @submit.prevent="register"
            >

            
              <!-- username -->
              <b-form-group
                label="Username"
                label-for="register-username"
              >
                <validation-provider
                  #default="{ errors }"
                  name="Username"
                  vid="username"
                  rules="required"
                >


                <b-input-group class="input-group-merge">
                  
                  <b-input-group-prepend is-text>
                    <feather-icon icon="UserIcon" />
                  </b-input-group-prepend>

                  <b-form-input
                    id="register-username"
                    v-model="usernname"
                    name="register-username"
                    :state="errors.length > 0 ? false:null"
                    placeholder="johndoe"
                  />
                  
                  <b-input-group-append is-text>
                    <feather-icon icon="XIcon" />
                  </b-input-group-append>

                </b-input-group>

                  <small class="text-danger">{{ errors[0] }}</small>
                </validation-provider>
              </b-form-group>

              <!-- email -->
              <b-form-group
                label="Email"
                label-for="register-email"
              >
                <validation-provider
                  #default="{ errors }"
                  name="Email"
                  vid="email"
                  rules="required|email"
                >

                <b-input-group class="input-group-merge">
                  
                  <b-input-group-prepend is-text>
                    <feather-icon icon="MailIcon" />
                  </b-input-group-prepend>


                  <b-form-input
                    id="register-email"
                    v-model="userEmail"
                    name="register-email"
                    :state="errors.length > 0 ? false:null"
                    placeholder="john@example.com"
                  />

                  <b-input-group-append is-text>
                    <feather-icon icon="XIcon" />
                   </b-input-group-append>

                </b-input-group>
                  <small class="text-danger">{{ errors[0] }}</small>
                </validation-provider>
              </b-form-group>


             <!-- PhoneNumber -->
              <b-form-group
                label="Phone"
                label-for="register-phone"
              >
                <validation-provider
                  #default="{ errors }"
                  name="Phone"
                  vid="phone"
                  rules="required"
                >

                <b-input-group class="input-group-merge">
                  
                  <b-input-group-prepend is-text>
                    <feather-icon icon="PhoneIcon" />
                  </b-input-group-prepend>

                  
                  <b-form-input
                    id="register-phone"
                    v-model="userPhone"
                    name="register-phone"
                    :state="errors.length > 0 ? false:null"
                    placeholder="0123455678"
                  />

                  <b-input-group-append is-text>
                    <feather-icon icon="XIcon" />
                   </b-input-group-append>

                </b-input-group>
                  <small class="text-danger">{{ errors[0] }}</small>
                </validation-provider>
              </b-form-group>

              <!-- password -->
              <b-form-group
                label-for="register-password"
                label="Password"
              >
                <validation-provider
                  #default="{ errors }"
                  name="Password"
                  vid="password"
                  rules="required"
                >
                  <b-input-group
                    class="input-group-merge"
                    :class="errors.length > 0 ? 'is-invalid':null"
                  >

                    <b-input-group-prepend is-text>
                      <feather-icon icon="LockIcon" />
                    </b-input-group-prepend>

                    <b-form-input
                      id="register-password"
                      v-model="password"
                      :state="errors.length > 0 ? false:null"
                      class="form-control-merge"
                      :type="passwordFieldType"
                      name="register-password"
                      placeholder="············"
                    />

                    <b-input-group-append is-text>
                      <feather-icon
                        :icon="passwordToggleIcon"
                        class="cursor-pointer"
                        @click="togglePasswordVisibility"
                      />
                    </b-input-group-append>
                  </b-input-group>
                  <small class="text-danger">{{ errors[0] }}</small>
                </validation-provider>
              </b-form-group>

              <!-- <b-form-group>
                <b-form-checkbox
                  id="register-privacy-policy"
                  v-model="status"
                  name="checkbox-1"
                >
                  I agree to
                  <b-link>privacy policy & terms</b-link>
                </b-form-checkbox>
              </b-form-group> -->

              <b-button
                variant="primary"
                block
                type="submit"
                :disabled="invalid"
                class="mt-2 rounded-pill"
              >
                Sign up
              </b-button>

              <p class="text-center mt-2">
                <span>Already have an account?</span>
                <b-link :to="{name:'auth-login'}">
                <span>&nbsp;Login</span>
                </b-link>
              </p>

              
              <b-button
                variant="outline-primary"
                block
                type="submit"
                :disabled="invalid"
                class="rounded-pill"
              >
                Teacher Sign up
              </b-button>

            </b-form>
          </validation-observer>



          <!-- divider -->
          <!-- <div class="divider my-2">
            <div class="divider-text">
              or
            </div>
          </div> -->
<!-- 
          <div class="auth-footer-btn d-flex justify-content-center">
            <b-button
              variant="facebook"
              href="javascript:void(0)"
            >
              <feather-icon icon="FacebookIcon" />
            </b-button>
            <b-button
              variant="twitter"
              href="javascript:void(0)"
            >
              <feather-icon icon="TwitterIcon" />
            </b-button>
            <b-button
              variant="google"
              href="javascript:void(0)"
            >
              <feather-icon icon="MailIcon" />
            </b-button> -->
            <!-- <b-button
              variant="github"
              href="javascript:void(0)"
            >
              <feather-icon icon="GithubIcon" />
            </b-button>
          </div> -->


        </b-col>
      </b-col>
    <!-- /Register-->
    </b-row>
  </div>
</template>

<script>
/* eslint-disable global-require */
import { ValidationProvider, ValidationObserver } from 'vee-validate'
import VuexyLogo from '@core/layouts/components/Logo.vue'
import {
  BRow, BCol,BAlert, BLink,BInputGroupPrepend, BButton, BForm, BFormCheckbox, BFormGroup, BFormInput, BInputGroup, BInputGroupAppend, BImg, BCardTitle, BCardText,
} from 'bootstrap-vue'
import { required, email } from '@validations'
import { togglePasswordVisibility } from '@core/mixins/ui/forms'
import store from '@/store/index'
import useJwt from '@/auth/jwt/useJwt'
import Colors from '@/views/ui/colors/Colors.vue'

export default {
  components: {
    VuexyLogo,
    BRow,
    BCol,
    BLink,
    BInputGroupPrepend,
    BFormGroup,
    BFormInput,
    BInputGroupAppend,
    BInputGroup,
    BFormCheckbox,
    BCardText,
    BCardTitle,
    BImg,
    BForm,
    BButton,
    BAlert,
    // validations
    ValidationProvider,
    ValidationObserver,
  },
  mixins: [togglePasswordVisibility],
  data() {
    return {
      status: '',
      username: '',
      userPhone:'',
      userEmail: '',
      password: '',
      sideImg: require('@/assets/images/pages/register-v2.svg'),
      // validation
      required,
      email,
    }
  },
  computed: {
    passwordToggleIcon() {
      return this.passwordFieldType === 'password' ? 'EyeIcon' : 'EyeOffIcon'
    },
    imgUrl() {
      if (store.state.appConfig.layout.skin === 'dark') {
        // eslint-disable-next-line vue/no-side-effects-in-computed-properties
        this.sideImg = require('@/assets/images/pages/register-v2-dark.svg')
        return this.sideImg
      }
      return this.sideImg
    },
  },
  methods: {
    register() {
      this.$refs.registerForm.validate().then(success => {
        if (success) {
          useJwt.register({
            username: this.username,
            email: this.userEmail,
            password: this.password,
          })
            .then(response => {
              useJwt.setToken(response.data.accessToken)
              useJwt.setRefreshToken(response.data.refreshToken)
              localStorage.setItem('userData', JSON.stringify(response.data.userData))
              this.$ability.update(response.data.userData.ability)
              this.$router.push('/')
            })
            .catch(error => {
              this.$refs.registerForm.setErrors(error.response.data.error)
            })
        }
      })
    },
  },
}
/* eslint-disable global-require */
</script>

<style lang="scss">
@import '@core/scss/vue/pages/page-auth.scss';
</style>
