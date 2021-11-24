<template>
<indonesia/>
<global/>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import indonesia from '@/components/indonesia.vue'
import global from '@/components/global.vue'

export default {
  name: 'Home',
  components: {
    HelloWorld,
    indonesia,
    global
  }
}
</script>
