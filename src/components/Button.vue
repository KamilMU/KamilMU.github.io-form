<template>
  <div>
    <button class="button" type="submit" :disabled="submitStatus === 'PENDING'">
      Submit!
    </button>
    <p v-if="submitStatus === 'OK'">Thanks for your submission!</p>
    <p v-if="submitStatus === 'ERROR'">Please fill the form correctly.</p>
    <p v-if="submitStatus === 'PENDING'">Sending...</p>
  </div>
</template>

<script>
export default {
  name: "Button",
  props: ["submitStatus"],
};
</script>

<style>
</style>