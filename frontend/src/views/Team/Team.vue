<template>
    <section class="schedule">
        <div class="container">
            <div class="schedule__inner">
                <h2 class="title">Руководство и педагогический состав</h2>
                <table>
                    <thead>
                        <tr>
                            <td style="text-align: center;">ФИО</td>
                            <td  >Должность</td>
                            <td >Фото</td>
                        </tr>
                    </thead>
                    <tbody>
                        <TeamItem v-for="(person, index) in team" :key = "index" :person="person"/>
                    </tbody>
                </table>
            </div>
        </div>
    </section>
  </template>
  
  <script>
  import axios from 'axios'
  import TeamItem from '/src/components/TeamItem/TeamItem.vue'
export default {
  components:{
    TeamItem
  },
  data(){
      return{
          team: []
      }
  },
  methods:{
      async getTeam(){
          try{
              const response  = await axios.get("http://localhost:3000/team");
              this.team = response.data;
              console.log(this.team)
          }catch(error){
              console.log(error, "Произошла ошибка при попытке взятия данных из таблицы Команда");
          }
      }
  },
  mounted(){
      this.getTeam();
  }

  
}
</script>