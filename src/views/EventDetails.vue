<template>
<div v-if="event">
    <h2>{{event.title}}</h2>
    <span>{{event.time}} on {{event.date}}  @ {{event.location}}</span>
    <p>{{event.description}}</p>
    </div>
</template>
<script>
import  EventServices  from '../services/EventServices.js';

export default {
  
  props:['id'],
  data(){
      return {
          event :null
      }
  },
  created(){
      EventServices.getEvent(this.id).then(response=>this.event= response.data)
      .catch(error =>{
          console.log(error)
      })
  }
};
</script>
