<template>
    <tr class="schedule__row">
        <td>{{person.NSL}}</td>
        <td style="text-align: center;">{{person.position}}</td>
        <td style="text-align: center;"><div :style="background"></div></td>
    </tr>
  </template>
  
  <script>

  export default {
    props:{
        person:{
            type: Object,
            required: true,
        }
    },
    data(){
        return{
           background: `background: url(${this.person.photo}) 0 0 / 100% no-repeat`
        }
    }
  }
  </script>