<template>
  <div class="row align-items-center">
    <div class="row align-items-center">
      <div v-for="index in 5" :key="index" class="col align-items-center">
        <div class="word_container align-items-center" :id="'word1-'+index">
          
        </div>
      </div>
    </div>
    <div class="row">
      <div v-for="index in 5" :key="index" class="col">
        <div class="word_container" :id="'word2-'+index">
        </div>
      </div>
    </div>
    <div class="row">
      <div v-for="index in 5" :key="index" class="col">
        <div class="word_container" :id="'word3-'+index">
        </div>
      </div>
    </div>
    <div class="row">
      <div v-for="index in 5" :key="index" class="col">
        <div class="word_container" :id="'word4-'+index">
        </div>
      </div>
    </div>
    <div class="row">
      <div v-for="index in 5" :key="index" class="col">
        <div class="word_container" :id="'word5-'+index">
          {{  }}
        </div>
      </div>
    </div>
    <div class="row">
      <div v-for="index in 5" :key="index" class="col">
        <div class="word_container" :id="'word6-'+index">
          {{  }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
.word_container {
  background-color: rgb(233, 233, 233);
  height: 50px;
  margin-bottom: 7px;
  border: 1px rgba(61, 61, 61, 0.183) solid;
  text-align: center;
  padding-top:8px;
  font-weight: 700;
  font-size: 20px;
}
.correct{
    background-color: green !important;
}
.missplace{
    background-color:rgb(181, 148, 3);
}
.notfound {
  background-color: rgb(169, 169, 169);
}

</style>
