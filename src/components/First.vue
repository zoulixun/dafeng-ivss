<template>
    <div class="first">
    <FirstTop></FirstTop>
    <FirstBottom></FirstBottom>
    </div>
</template>

<script>
import FirstTop from '@/components/FirstTop'
import FirstBottom from '@/components/FirstBottom'
export default {
  name: 'First',
  components:{
    FirstTop,
    FirstBottom  
  },
  data () {
    return {
      
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
*{
    margin: 0;
    padding: 0;
}
.first{
    width: 100%;
    text-align: center;
    margin-top: 1%;
}
</style>
