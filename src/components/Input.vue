<template>
    <div class="container">
        <div class="input">
            <label class="input-item" for="name">User Name</label>
            <input class="input-item" type="text" id="name" placeholder="Enter User Name" v-model="name">
            <input class="input-item" type="submit" value="Add User" @click="addUser">
            <span class="input-item" id="success-msg"></span>
        </div>
        <div class="toggle" v-if="toggle">
            <Alert />
        </div>
    </div>
</template>

<script>
import axios from 'axios'
import Alert from './Alert.vue'

export default {
    name: 'Input',
    components:{
        Alert,
    },
    data(){
        return{
            name:null,
            toggle:null
        }
    },
    methods:{
        async addUser(){
            let req = await axios.get(`https://63050cb694b8c58fd72aeb28.mockapi.io/user?name=${this.name}`)
            if (req.data.length == 0){
                let res = await axios.post('https://63050cb694b8c58fd72aeb28.mockapi.io/user',{
                    name:this.name
                })
                document.getElementById("success-msg").innerHTML = 'User has been added successfully'
                setTimeout(() => document.getElementById("success-msg").innerHTML = '',1500)
                setTimeout(() => this.toggle = false, 2000);
            }
            else{
                this.toggle = true
                setTimeout(() => document.getElementById("success-msg").innerHTML = '',1500)
                setTimeout(() => this.toggle = false, 2000);
            }
        }
    }
}
</script>

<style scoped>
.input{
    display:flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}
.input span{
    color: #FF5A59;
}
.input-item{
    margin: 10px 0;
}
.input label{
    font-size: 30px;
    color: white;
}
.input input[type="text"]{
    padding: 10px;
    border: 2px solid #FF5A59;
    border-radius: 6px;
    color: white;
}
.input input[type="text"]:focus{
    outline: none;
}
.input input[type="submit"]{
    padding: 10px;
    border:2px solid #FF5A59;
    border-radius: 6px;
    color: white;
    opacity: 0;
    transition: 0.3s;
}
.input input[type="submit"]:hover{
    background-color: #FF5A59;
    transform: scale(1.2);
    transition: 0.3s;
}
input:not(:placeholder-shown) + input[type="submit"]{
    opacity: 1;
}
.toggle{
    color: white;
}
</style>