<template>
    <div>
        <button @click="createCookie">Create a Cookie</button>
        <button @click="deleteCookie">Delete Cookie</button>
        <button @click="getCookie">Get Cookie</button>
        <!-- if you know the API has unique identifiers, you can use them eg user.id-->
        <div v-for="user in users" :key="user.id">
            <h1>{{user.first_name}} {{user.last_name}}</h1>
            <h2>{{user.email}}</h2>
            <!-- the back slash is for combining the dynamic variable and text ? -->
            <img :src="user.avatar" :alt="user.first_name+'\'s avatar'">
        </div>
    </div>
</template>

<script>
// have to import axios to use it
import axios from 'axios';
import cookies from 'vue-cookies';

    export default {
        name : "AxiosComp",
        data() {
            return {
                users: []
            }
        },
        methods: {
            createCookie() {
                cookies.set(`testCookie`, `This is a test`);
            },
            deleteCookie() {
                cookies.remove(`testCookie`);
            },
            getCookie() {
                let value = cookies.get(`testCookie`);
                console.log(value);
            }
        },
        mounted () {
            axios.request({
                url: "https://reqres.in/api/users",
                method: "GET"
            }).then((response)=>{
                this.users = response.data.data;
                // this.users.push(users);
            }).catch((error)=>{
                console.log(error);
            });
        },
    }
</script>

<style scoped>

</style>