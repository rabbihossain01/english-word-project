<template>
  <div class="new-password-page">
    <h1 class="page-title">Input new password</h1>
    <div v-if="error" class="error-message">{{ error }}</div>
    <form @submit.prevent="newPassword()">
      <div class="input-box">
        <label for="password">Password</label>
        <input
          id="password"
          v-model="password"
          type="password"
          placeholder="password"
        />
      </div>
      <div class="input-box">
        <label for="password">Confirm Password</label>
        <input
          id="password"
          v-model="password1"
          type="password"
          placeholder="Retype password"
        />
      </div>
      <button type="submit" class="primary-btn-full-width">send</button>
    </form>
  </div>
</template>

<script>
export default {
  layout: 'footer-less',

  data() {
    return {
      password: '',
      password1: '',
      error: '',
    }
  },
}
</script>

<style lang="scss" scoped>
@import '@/styles/style.scss';

.new-password-page {
  @extend .flex;
  flex-direction: column;
  background: #f1f1f9;
  min-height: calc(100vh - 4rem);
  .page-title {
    font-size: 2.1rem;
    text-transform: capitalize;
    color: #004b63;
    margin-bottom: 1.6rem;
    @include responsive(phone) {
      font-size: 1.5rem;
    }
  }
  .error-message {
    margin-bottom: 1rem;
    color: red;
    text-align: center;
    font-size: 14px;
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
    .pd-8 {
      padding: 0.7rem 0.75rem;
    }
  }
}
</style>
