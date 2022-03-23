<template>
  <div class="flex justify-start">
    <div class="hidden md:inline-block w-1/5 shadow relative bg-darks text-white">
      <div class="p-4 flex justify-center items-center border-b border-gray-800 space-x-1">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="h-6 w-6"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
          stroke-width="2"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            d="M7 21a4 4 0 01-4-4V5a2 2 0 012-2h4a2 2 0 012 2v12a4 4 0 01-4 4zm0 0h12a2 2 0 002-2v-4a2 2 0 00-2-2h-2.343M11 7.343l1.657-1.657a2 2 0 012.828 0l2.829 2.829a2 2 0 010 2.828l-8.486 8.485M7 17h.01"
          />
        </svg>
        <h1 class="inline-block font-bold text-xl uppercase">TaycII</h1>
      </div>
      <div class="border-gray-200 space-y-2">
        <router-link class="menu-navbar" to="/">Home</router-link>
        <router-link class="menu-navbar" to="/table">Table</router-link>
      </div>
    </div>
    <div class="w-full h-screen overflow-y-auto">
      <div class="flex justify-between items-center shadow p-4 relative">
        <button class="md:invisible">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-6 w-6"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
            stroke-width="2"
          >
            <path stroke-linecap="round" stroke-linejoin="round" d="M4 6h16M4 12h16M4 18h16" />
          </svg>
        </button>
        <button
          v-on:click="isHidden = !isHidden"
          class="flex items-center space-x-2 cursor-pointer"
        >
          <img
            class="w-8 h-8 rounded-full"
            src="https://cdn.pixabay.com/photo/2015/10/05/22/37/blank-profile-picture-973460_1280.png"
            alt="Profile"
          />
          <h1 class="inline-block">Admin</h1>
        </button>
        <div
          v-if="!isHidden"
          class="absolute right-1 top-16 bg-white shadow rounded-b-sm px-4 py-2 z-50"
        >
          <router-link class="hover:text-gray-500 hover:underline" to="/logout">Logout</router-link>
        </div>
      </div>
      <router-view />
    </div>
  </div>
</template>

<script>

export default {
  data() {
    return {
      isHidden: true
    }
  }
}

</script>
