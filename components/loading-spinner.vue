<template>
  <div class="spinner">
    <div class="loading-spinner">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        xmlns:xlink="http://www.w3.org/1999/xlink"
        :height="height"
        viewBox="0 0 100 100"
        preserveAspectRatio="xMidYMid"
      >
        <circle
          cx="50"
          cy="50"
          fill="none"
          :stroke="color"
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
    </div>
  </div>
</template>

<script>
export default {
  props: {
    color: {
      type: String,
      required: false,
      default: 'rgba(27, 143, 180, 1)',
    },
    height: {
      type: String,
      required: false,
      default: '35px',
    },
  },
}
</script>

<style lang="scss" scoped>
.spinner {
  .loading-spinner {
    margin: auto;
    background: none;
    display: block;
    shape-rendering: auto;
    width: 30px;
    height: 30px;
    padding-top: 1rem;
  }
}
</style>
