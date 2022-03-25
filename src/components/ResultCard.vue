<template>
  <div class="result-card">
    <div class="card-icon">
      <h3>Resultat Score</h3>
    </div>
   {{currentRaiting}}
  </div>

</template>

<script>
export default {
  name: 'ResultCard',
  props: {
    currentRaiting: String
  }
}
</script>

<style scoped lang="scss">
.result-card {
  color: #fff;
}
</style>
