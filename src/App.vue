<template>    
  <div :class="isDark ? 'dark' : ''" class="dark:bg-primary">
    <div class="bg-white  dark:bg-primary">
      <nav class=" shadow-lg" >
          <div class="flex flex-row justify-around p-5">
              <p class="font-semibold text-black dark:text-white text-lg">devfinder</p>
                <div class="flex flex-row" @click="isDark = !isDark">
                  <p v-if="isDark" class="px-3 text-xs text-black dark:text-white">LIGHT</p>
                  <p v-else class="px-3 text-xs text-black dark:text-white">DARK</p>
                  <i v-if="isDark" class="far fa-sun cursor-pointer text-black dark:text-white"></i>
                  <i v-else class="far fa-moon cursor-pointer text-black dark:text-white"></i>
                </div>
            </div>
        </nav>

        <div class="flex justify-center px-4 pt-4 pb-4" >
                <div class="w-full max-w-screen-sm">
                    <h1 class="text-blue-600 text-center text-3xl pb-4 dark:text-white">Dev Tracker</h1>
                      <div class="relative text-gray-700">
                          <input v-model="queryUser" class="h-14 w-full pl-8 focus:outline-none pr-3 text-base shadow-lg placeholder-gray-600 dark:placeholder-white bg-white dark:bg-gray-500 dark:text-white rounded-lg focus:shadow-outline text-black " type="text" placeholder="Search Github username"/>
                              <div class="absolute inset-y-0 left-0 flex items-center px-2 pointer-events-none">
                                  <i class="fas fa-search w-4 h-4 fill-current text-blue-600"></i>
                              </div>
                              <div class="absolute inset-y-0 right-0 flex items-center px-2">
                                  <button @click="getUserInfo" class="rounded-full py-3 px-4  fill-current bg-blue-500 font-bold text-white focus:outline-none">Search</button>
                              </div>
                      </div>
                </div>       
        </div>
        <userInfo v-if="ipinfo" v-bind:ipinfo='ipinfo'/>
    
      </div>
           
  </div>
</template>

<script type='module'>
import userInfo from './components/userInfo.vue'
import {ref} from 'vue'


export default {
  name: 'App',
  components: {
    userInfo
  },
    data() {
    return {
      isDark: false,
    }
  },
  setup(){
      const queryUser = ref("");
        const ipinfo = ref(null)

        const { Octokit } = require("@octokit/rest");
      const octokit = new Octokit();

        const getUserInfo = async () => {
          try{
            const data = await octokit.request('GET /users/{username}', {
              username: queryUser.value})

              const result = data.data
              console.log(result)
              ipinfo.value = {
                icon_avatar: result.avatar_url,
                joined: result.created_at,
                profilename: result.name,
                namelogin: result.login,
                bio: result.bio,
                repos: result.public_repos,
                followers: result.followers,
                following: result.following,
                location: result.location,
                 blog: result.blog,
                 twitter: result.twitter_username,
                 url: result.type
              }
          }
            catch(err){
            alert(err.message)
        } 
  }
         return {queryUser, ipinfo, getUserInfo}
  }
}
</script>

<style>
  
</style>