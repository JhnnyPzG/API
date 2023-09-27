<template>
  <div id="personaje">
    <List/>
  </div>
</template>


<script>
import List from '../components/Lista'

export default {
  name: 'Index',
  components: {
    List
  }
}
</script>

<style>
#personaje {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  height: 150%;
  margin-top: 270px;
}
</style>