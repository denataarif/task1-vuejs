<script>
  export default{
    data(){
      return{
        experience:[
        {
            id: 1,
            start: "Oktober 2021",
            end:"Januari 2022",
            position:"Graphic Designer",
            company:"PT. Ocademy Cipta Prestasi",
            description: "Neque porro quisquam est qui dolorem ipsum quia dolor sit amet, consectetur, adipisci velit...",
            show_description:false
          },
          {
            id: 2,
            start: "Februari 2022",
            end:"Juli 2022",
            position:"Frontend Javascript",
            company:"Binar Academy",
            description: "Neque porro quisquam est qui dolorem ipsum quia dolor sit amet, consectetur, adipisci velit...",
            show_description:false
          },
          {
            id: 3,
            start: "April 2022",
            end:"Mei 2022",
            position:"Waiters",
            company:"Sejiwa Coffee",
            description: "Neque porro quisquam est qui dolorem ipsum quia dolor sit amet, consectetur, adipisci velit...",
            show_description:false
          },  
        ],
        skills:[
          {
            id:1,
            skill:"React.js",
            presentase: 79,
          },
          {
            id:2,
            skill:"vue.js",
            presentase: 10,
          },
          {
            id:3,
            skill:"Python",
            presentase: 50,
          }
      ],
      contact:{
        nama: "",
        email: "",
        note: "", 
      }
      }
    },
    methods:{
      setShow_desc(data){
        data.show_description = !data.show_description
      },
      popUp(){
        alert(
          "Terimakasih"+ " " + this.contact.nama + " " + "dengan" + " " + this.contact.email + " " + "mengirim note " +  " " + this.contact.note
        );
        this.$refs.form.reset();
      },
    }
  }
</script>

<template>
  <div class="container">
    <h1>Resume</h1>
  <h2>Denata Arif Nur Muhamad</h2>
  <P>Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.</P>
  <section class="first">
    <h3>Experience</h3>
    <ol>
      <li v-for="exp in experience" :key="exp.id" @click="setShow_desc(exp)">
        {{exp.start}} - {{exp.end}} - {{exp.position}} - {{exp.company}}
        <p v-if="exp.show_description">
        {{exp.description}}
      </p>
      </li>
    </ol>
  </section>
  <section class="second">
    <h3>Skills</h3>
    <!-- <div class="skill" v-for="skl in skills">
      <p>{{skl.id}}. {{skl.skill}}</p>
      <div class="bar">
          <div class="presentase" :style="{'width': skl.presentase + '%'}"></div>
      </div>
    </div> -->
    <ol>
      <li class="skill" v-for="skl in skills">
        {{skl.skill}} {{skl.presentase}}
        <div class="bar">
          <div class="presentase" :style="{'width': skl.presentase + '%'}"></div>
        </div>
      </li>
    </ol>
  </section>
  <section class="third">
    <h3>Contact Me</h3>
    <form @submit.prevent="popUp()" ref="form">
      <p>Nama</p>
      <input type="text" placeholder="Nama" v-model="contact.nama"/>
      <p>Email</p>
      <input type="email" placeholder="Email" v-model="contact.email"/>
      <p>Note</p>
      <textarea placeholder="Note" v-model="contact.note"></textarea>
      <br/>
      <button class="btn">Submit</button>
    </form>
  </section>
  </div>
</template>

<style>
  .container{
    width: 50%;
    margin: auto;
  }
  .bar {
    background-color: #11ffff;
    width: 100%;
    height: 25px;
    border-radius: 5px;
  }
  .presentase {
    height: 100%;
    border-radius: 5px;
    background-color: darksalmon;
  }
  .third{
    margin-top: 25px;
    padding: 10px;
    background-color: darksalmon;
    border-radius: 5px;
  }
  .third input{
    width: 100%;
    height: 25px;
    border-radius: 5px;
  }
  .third textarea{
    width: 100%;
    height: 30px;
    margin-bottom: 10px;
    border-radius: 5px;
  }
  .btn{
    border-radius: 4px;
    border: none;
    background-color: #11ffff;
    padding: 10px;
  }
</style>
