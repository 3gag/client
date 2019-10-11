<template>
  
<main-page></main-page>
  
</template>

<script>
import mainPage from './components/mainPage'
import pictureform from './components/pictureForm'
export default {
    data:function() {
      return{
        pictures: []
      }
        
    },
    methods: {
      
    },
    components: {
      mainPage,pictureform
    }  
}
</script>

<style>

</style>