<template>
   <div> <!--content wrapper-->
                <main class=" px-6 top-50 lg:top-70 m-5 lg:left-2.5 lg:m-7 lg:px-12 mb-4 p-2 lg:p-4 bg-white dark:bg-gray-500 shadow-lg rounded">
             <div class="flex flex-col">
                <img :src="ipinfo.icon_avatar" class="w-20 h-35 lg:w-32 items-center rounded-full " alt="icon avatar">
            </div>

            <div class="flex flex-col md:justify-end">
                <p class="text-gray-400">Created {{ipinfo.joined}}</p>
            </div>

            <div class="flex flex-col">
                <h2 class="text-black dark:text-white text-4xl lg:text-6xl font-semibold">{{ipinfo.profilename}}</h2>
                <p class="lg:text-2xl sm:text-sm text-blue-700">{{ipinfo.namelogin}}</p>
                <p class="text-gray-500 dark:text-white">{{ipinfo.bio}}</p>
            </div>

            <div class="container mt-5">
                <div class="grid grid-cols-3 font-semibold rounded p-3 lg:p-4 bg-gray-100 dark:bg-primary">
                    <div class="text-center ">
                        <h3 class="text-gray-500">Repos</h3>
                        <p class="text-black dark:text-white">{{ipinfo.repos}}</p>
                    </div>
                    <div class="text-center text-white">
                        <h3 class="text-gray-500">Followers</h3>
                        <p class="text-black dark:text-white">{{ipinfo.followers}}</p>
                    </div>
                    <div class="text-center text-white">
                        <h3 class="text-gray-500">Following</h3>
                        <p class="text-black dark:text-white">{{ipinfo.following}}</p>
                    </div>
                </div>
            </div>

                <div class="grid lg:grid-cols-3 gap-4 mt-5 font-bold text-gray-500 dark:text-white">
                    <div class="flex">
                        <i class="fas fa-map-marker-alt w-4 h-4 fill-current"></i><p class="ml-3">{{ipinfo.location}}</p>     
                    </div>
                    <div class="flex ">
                        <i class="fas fa-link"></i> <a href="" class="ml-3 cursor-pointer">{{ipinfo.blog}}</a>
                    </div>
                    <div class="flex ">
                        <i class="fab fa-twitter "></i> <a href="" class="ml-3">{{ipinfo.twitter}}</a>
                    </div>

                    <div class="flex ">
                       <i class="fas fa-building"></i><a href="" class="ml-3 cursor-pointer">{{ipinfo.url}}</a>
                    </div>
                </div>

        </main>

            <div class="flex justify-center">
              <p class="text-black dark:text-white font-bold">Designed and Implemented by</p> 
              <a href="https://github.com/SammieKei40" target="_blank" class="text-blue-400 ml-1">Sammie Kei</a>
        </div>
    </div>
</template>

<script>
export default {
    props: ['ipinfo']
}
</script>

<style>

</style>