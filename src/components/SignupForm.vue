<template>
  <form >
    <label >Email:</label>
    <input type="email" required v-model="email">
    <label >Password:</label>
    <input type="password" required v-model="password">
    <label >Role:</label>
    <select v-model="role">
        <option value="developer">Web Developer</option>
        <option value="designer">Web Designer</option>
    </select>
    <label >Skills</label>
    <input type="text" v-model="tempskill" @keyup.alt="addSkill">
    <div v-for="skill in skills" :key="skill" class="pill">
       <span  @click="deleteSkill(skill)">{{ skill }}</span>
    </div>
    <div class="terms">
       
       <input type="checkbox" v-model="checkbox" required> 
       <label >termsAndConditions</label>
    </div>
    <div class="submit">
        <button>Submit</button>
    </div>
  </form>

</template>

<script>
export default {
    data(){
        return{
            email:'',
            password:'',
            role:'developer',
            checkbox:false,
            tempskill:'',
            skills:[]

        }
    },
    methods:{
        addSkill(e)
        {
            if (e.key===','&&this.tempskill) {
                if (!this.skills.includes(this.tempskill)) {
                     this.skills.push(this.tempskill)
                    
                }
                else
                {
                    alert('duplicate data')
                }
                 this.tempskill = ''
            }
        },
        deleteSkill(skill)
        {
            this.skills = this.skills.filter((item)=>{
               return skill!=item
            })
        }
    }

}
</script>

<style>
 form{
    max-width: 420px;
    margin: 30px auto;
    background: white;
    text-align: left;
    padding: 40px;
    border-radius: 10px;
 }
 label{
    color:#aaa;
    display: inline-block;
    margin: 25px 0 15px;
    font-size: 0.6em;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
 }
 input,select{
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid #ddd;
    color:#555
 }
 input[type="checkbox"]
 {
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0;
    position: relative;
    top: 2px;
 }

.pill {
    display: inline-block;
    margin: 20px 10px 0 0;
    padding: 6px 12px;
    background: #eee;
    border-radius: 20px;
    font-size: 12px;
    letter-spacing: 1px;
    font-weight: bold;
    color: #777;
    cursor: pointer;
  }
  button {
    background: #0b6dff;
    border: 0;
    padding: 10px 20px;
    margin-top: 20px;
    color: white;
    border-radius: 20px;
}
.submit {
    text-align: center;
}

</style>