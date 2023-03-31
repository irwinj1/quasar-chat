<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn color="primary" v-if="route.path.includes('/chat')"  icon="arrow_back" label="On Left" />

        <q-toolbar-title class="absolute-center">
          {{ title }}
        </q-toolbar-title>

        
      </q-toolbar>
    </q-header>

   

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { route } from 'quasar/wrappers';
import { computed, defineComponent, ref } from 'vue'
import { useRoute } from 'vue-router';



export default defineComponent({
  name: 'MainLayout',

  

  setup () {
    let route = useRoute();
   
    const title = computed(()=>{
      
      let currentPath =useRoute()
     
      if (currentPath.path == '/') return 'SmackChat'
      else if(currentPath.path == '/chat') return 'Chat'
      else if(currentPath.path == 'auth') return 'Login'
    })
    
    return {
      title,
      route
    }
  }
})
</script>
