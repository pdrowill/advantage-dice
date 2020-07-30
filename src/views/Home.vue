<template>
  <div class="home">
    <DiceRoller msg="Dice Roller"/>
  </div>
</template>

<script>
// @ is an alias to /src
import DiceRoller from '@/components/DiceRoller.vue'

export default {
  name: 'Home',
  components: {
    DiceRoller
  }
}
</script>
