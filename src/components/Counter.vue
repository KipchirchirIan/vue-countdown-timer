<template>
  <div>
    {{ days }}
    {{ hours }}
    {{ minutes }}
    {{ seconds }}
  </div>
</template>

<script>
export default {
  name: 'Counter',
  data () {
    return {
      days: 0,
      hours: 0,
      minutes: 0,
      seconds: 0
    }
  }
}
</script>

<style scoped>

</style>
