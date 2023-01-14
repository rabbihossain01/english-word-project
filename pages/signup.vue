<template>
  <div class="sign-up-page">
    <h1 class="page-title">Sign up to get started</h1>
    <p class="error-message">
      {{ error }}
    </p>
    <form v-if="!showOnboarding" class="form-section" @submit.prevent>
      <div class="input-box">
        <label for="email">Email <span class="red">*</span></label>
        <input id="email" v-model="email" type="email" placeholder="email" />
      </div>
      <div class="input-box">
        <label for="password">Password <span class="red">*</span></label>
        <input v-model="password" type="password" placeholder="password" />
      </div>
      <svg
        v-if="registeringUser"
        xmlns="http://www.w3.org/2000/svg"
        xmlns:xlink="http://www.w3.org/1999/xlink"
        style="
          margin: auto;
          background: rgb(255, 255, 255);
          display: block;
          shape-rendering: auto;
        "
        width="20px"
        height="20px"
        viewBox="0 0 100 100"
        preserveAspectRatio="xMidYMid"
      >
        <circle
          cx="50"
          cy="50"
          fill="none"
          stroke="rgba(27, 143, 180, 1)"
          stroke-width="10"
          r="35"
          stroke-dasharray="164.93361431346415 56.97787143782138"
        >
          <animateTransform
            attributeName="transform"
            type="rotate"
            repeatCount="indefinite"
            dur="1s"
            values="0 50 50;360 50 50"
            keyTimes="0;1"
          ></animateTransform>
        </circle>
      </svg>
      <button v-else class="primary-btn" @click.prevent="signUpWithEmail">
        Register
      </button>
      <p class="or">Or</p>
      <button class="btn-secondary" @click.prevent="signInWithGoogle">
        Continue with
        <svg
          xmlns="http://www.w3.org/2000/svg"
          viewBox="0 0 272 92"
          width="65"
          height="18px"
        >
          <path
            fill="#EA4335"
            d="M115.75 47.18c0 12.77-9.99 22.18-22.25 22.18s-22.25-9.41-22.25-22.18C71.25 34.32 81.24 25 93.5 25s22.25 9.32 22.25 22.18zm-9.74 0c0-7.98-5.79-13.44-12.51-13.44S80.99 39.2 80.99 47.18c0 7.9 5.79 13.44 12.51 13.44s12.51-5.55 12.51-13.44z"
          />
          <path
            fill="#FBBC05"
            d="M163.75 47.18c0 12.77-9.99 22.18-22.25 22.18s-22.25-9.41-22.25-22.18c0-12.85 9.99-22.18 22.25-22.18s22.25 9.32 22.25 22.18zm-9.74 0c0-7.98-5.79-13.44-12.51-13.44s-12.51 5.46-12.51 13.44c0 7.9 5.79 13.44 12.51 13.44s12.51-5.55 12.51-13.44z"
          />
          <path
            fill="#4285F4"
            d="M209.75 26.34v39.82c0 16.38-9.66 23.07-21.08 23.07-10.75 0-17.22-7.19-19.66-13.07l8.48-3.53c1.51 3.61 5.21 7.87 11.17 7.87 7.31 0 11.84-4.51 11.84-13v-3.19h-.34c-2.18 2.69-6.38 5.04-11.68 5.04-11.09 0-21.25-9.66-21.25-22.09 0-12.52 10.16-22.26 21.25-22.26 5.29 0 9.49 2.35 11.68 4.96h.34v-3.61h9.25zm-8.56 20.92c0-7.81-5.21-13.52-11.84-13.52-6.72 0-12.35 5.71-12.35 13.52 0 7.73 5.63 13.36 12.35 13.36 6.63 0 11.84-5.63 11.84-13.36z"
          />
          <path fill="#34A853" d="M225 3v65h-9.5V3h9.5z" />
          <path
            fill="#EA4335"
            d="M262.02 54.48l7.56 5.04c-2.44 3.61-8.32 9.83-18.48 9.83-12.6 0-22.01-9.74-22.01-22.18 0-13.19 9.49-22.18 20.92-22.18 11.51 0 17.14 9.16 18.98 14.11l1.01 2.52-29.65 12.28c2.27 4.45 5.8 6.72 10.75 6.72 4.96 0 8.4-2.44 10.92-6.14zm-23.27-7.98l19.82-8.23c-1.09-2.77-4.37-4.7-8.23-4.7-4.95 0-11.84 4.37-11.59 12.93z"
          />
          <path
            fill="#4285F4"
            d="M35.29 41.41V32H67c.31 1.64.47 3.58.47 5.68 0 7.06-1.93 15.79-8.15 22.01-6.05 6.3-13.78 9.66-24.02 9.66C16.32 69.35.36 53.89.36 34.91.36 15.93 16.32.47 35.3.47c10.5 0 17.98 4.12 23.6 9.49l-6.64 6.64c-4.03-3.78-9.49-6.72-16.97-6.72-13.86 0-24.7 11.17-24.7 25.03 0 13.86 10.84 25.03 24.7 25.03 8.99 0 14.11-3.61 17.39-6.89 2.66-2.66 4.41-6.46 5.1-11.65l-22.49.01z"
          />
        </svg>
      </button>
      <p class="auth-nav-link">
        <span>Already have account ? </span>
        <router-link class="router-link" to="/signin">Sign In </router-link>
      </p>
    </form>
    <div v-else class="signup">
      <template v-if="!showOrgDetailsForm">
        <h2 class="title">Account Info</h2>
        <div class="signup-box">
          <div class="input-box">
            <label for="displayName"
              >Full Name <span class="red">*</span></label
            >
            <input
              id="displayName"
              v-model="userDetails.displayName"
              type="text"
              name="text"
              placeholder="input your full name"
            />
          </div>
          <div class="input-box">
            <label for="username">Username <span class="red">*</span></label>
            <input
              id="username"
              v-model="userDetails.username"
              type="text"
              name="text"
              placeholder="input your username"
            />
          </div>
          <div class="input-box">
            <label for="phone">Phone Number</label>
            <input
              id="phone"
              v-model="userDetails.phoneNumber"
              type="text"
              name="text"
              placeholder="input your phone number"
            />
          </div>
          <div class="input-box">
            <label for="dateofbirth"> Date Of Birth </label>
            <input
              id="dateofbirth"
              v-model="userDetails.dateOfBirth"
              type="text"
              onfocus="(this.type = 'date')"
              name="dateofbirth"
              placeholder="input your date of birth"
            />
          </div>
          <div class="input-box">
            <label for="country">Country <span class="red">*</span></label>
            <select id="country" v-model="userDetails.country" name="country">
              <option value="">Select your ountry</option>
              <option v-for="c in countries" :key="c" :value="c">
                {{ c }}
              </option>
            </select>
          </div>
          <button
            class="primary-btn-full-width"
            :disabled="isSubmitButtonDisabled"
            @click="handleDataSubmission"
          >
            <p v-if="isApiCallRunning">loading...</p>
            <p v-else>submit</p>
          </button>
        </div>
      </template>
      <template v-else>
        <h2 class="title">Organization Info</h2>
        <div class="signup-box">
          <div class="input-box">
            <label for="org-displayName">
              Org Name <span class="red">*</span>
            </label>
            <input
              id="org-displayName"
              v-model="orgDetails.displayName"
              type="text"
              name="org-name"
              placeholder="input your full name"
            />
          </div>
          <div class="input-box">
            <label for="org-username">
              Org Username <span class="red">*</span>
            </label>
            <input
              id="org-username"
              v-model="orgDetails.username"
              type="text"
              name="org-username"
              placeholder="input your username"
            />
          </div>
          <div class="input-box">
            <label for="org-email">Org Email</label>
            <input
              id="org-email"
              v-model="orgDetails.email"
              type="email"
              name="org-email"
              placeholder="input your org email"
            />
          </div>
          <button
            class="primary-btn-full-width"
            :disabled="isSubmitButtonDisabled"
            @click="createNewUser"
          >
            <p v-if="isApiCallRunning">loading...</p>
            <p v-else>submit</p>
          </button>
        </div>
      </template>
    </div>
  </div>
</template>

<script>
export default {
  layout: 'footer-less',
}
</script>

<style lang="scss" scoped>
@import '~/styles/style.scss';

.sign-up-page {
  @extend .flex;
  font-family: $font-primary;
  flex-direction: column;
  padding-top: 2rem;
  background: #f1f1f9;
  min-height: calc(100vh - 4rem);
  .page-title {
    font-size: 2.1rem;
    color: #004b63;
    text-transform: capitalize;
    margin-bottom: 0.8rem;
    @include responsive(phone) {
      font-size: 1.5rem;
      margin-bottom: 0.8rem;
      padding: 0 1rem;
      text-align: center;
    }
  }
  .subtitle {
    font-size: 1rem;
    color: $color-secondary;
    margin-bottom: 1rem;
  }
  .error-message {
    margin-bottom: 1rem;
    color: red;
    text-align: center;
    font-size: 14px;
  }
  .sign-up-as {
    @extend .flex;
    flex-direction: column;
    font-family: $font-primary;
    padding-top: 2rem;
    background: #f7f7ff;
    min-height: calc(100vh - 4rem);
    .container {
      @extend .flex;
      @include responsive(phone) {
        width: 95%;
        margin: 0 auto;
      }

      .sign-up-as-content {
        color: $color-primary;
        width: 519px;
        border-radius: 24px;
        @include responsive(phone) {
          margin-top: 8rem;
        }

        .sign-up-as-item {
          padding: 2rem 2.5rem;
          @include responsive(phone) {
            padding: 2rem 1rem;
          }
          .page-title {
            font-size: 2.1rem;
            text-align: center;
            text-transform: capitalize;
            color: #000066;
            margin-bottom: 1.6rem;
            @include responsive(phone) {
              font-size: 1.5rem;
            }
          }
          .form-group {
            display: flex;
            flex-direction: column;
            padding: 2.3rem 2rem;
            margin-bottom: 2rem;
            @include responsive(phone) {
              padding: 2rem 1.5rem;
            }
            border-radius: 0.5rem;
            background: $color-primary;
            filter: drop-shadow(0px 0px 1px rgba(0, 0, 107, 0.1))
              drop-shadow(0px 0px 5px rgba(0, 0, 255, 0.3));
            .checkbox {
              display: flex;
              align-items: center;
              width: 100%;
              height: 64px;
              border-radius: 8px;
              margin-bottom: 2rem;
              cursor: pointer;
              color: rgba(255, 255, 255, 0.8);
              border: 1px solid rgb(164, 164, 216);
              position: relative;
              padding-left: 3rem;
              font-size: 1.1rem;
              color: #000000;
              &:hover {
                border: 1px solid rgb(115, 115, 255);
              }
              input {
                position: absolute;
                opacity: 0;
                cursor: pointer;
                height: 0;
                width: 0;
              }
              .checkmark {
                position: absolute;
                top: 18px;
                left: 10px;
                height: 23px;
                width: 23px;
                border-radius: 50%;
                border: 2px solid #c7c7c7;
              }
              input:checked ~ .checkmark {
                background-color: #fb0304;
                border: none;
              }
              .checkmark:after {
                content: '';
                position: absolute;
                display: none;
              }

              input:checked ~ .checkmark:after {
                display: block;
              }
              .checkmark:after {
                left: 8px;
                top: 4px;
                width: 5px;
                height: 10px;
                border: solid $color-primary;
                border-width: 0 3px 3px 0;
                -webkit-transform: rotate(45deg);
                -ms-transform: rotate(45deg);
                transform: rotate(45deg);
              }
            }
          }
        }
      }
    }
  }
  form {
    width: 407px;
    display: flex;
    flex-direction: column;
    padding: 2.3rem 2rem;
    margin-bottom: 2rem;
    @include responsive(phone) {
      padding: 2rem 1.5rem;
    }
    @extend .primary-shadow;
    .input-box {
      margin-bottom: 1rem;
    }
    .or {
      text-align: center;
      margin: 0.5rem 0;
      color: #004b63;
    }
    .pd-8 {
      padding: 0.7rem 0.75rem;
    }
    .auth-nav-link {
      margin-top: 0.5rem;
      font-size: 1rem;
    }
  }
  .signup {
    width: 90%;
    max-width: 400px;
    display: flex;
    flex-direction: column;
    padding: 2rem 2rem;
    margin-bottom: 2rem;
    h2 {
      text-align: center;
      margin-bottom: 1rem;
      font-size: 2.1rem;
      color: $color-secondary;
      text-transform: capitalize;
    }
    @include responsive(phone) {
      padding: 2rem 1.5rem;
    }
    @extend .primary-shadow;
    .signup-box {
      .input-box {
        margin-bottom: 1rem;
        label {
          display: block;
          margin: 0 0 0.2rem 0;
          color: #004b63;
          font-size: 0.9rem;
        }
      }
      .submit {
        width: 100%;
      }
    }
  }
}
</style>
