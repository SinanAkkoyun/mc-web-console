<template>
  <div class="home">
    <div class="interface">
      <v-slider/>
      <VueTerminal class="term"
                intro="Minecraft Server Console!"
                console-sign=">"
                allow-arbitrary
                radius="12px"
                @command="onCliCommand"></VueTerminal>
      <div class="players">
        <PlayerWidget mc_name="Console_Bot" health=15 scale=0.5></PlayerWidget>
        <PlayerWidget mc_name="Darkli_"     health=20 scale=0.5></PlayerWidget>
        <PlayerWidget mc_name="Louis_DS"    health=6  scale=0.5></PlayerWidget>
        <PlayerWidget mc_name="nesrinn"     health=19 scale=0.5></PlayerWidget>
        <PlayerWidget mc_name="fridaymelli" health=3  scale=0.5></PlayerWidget>
        <PlayerWidget mc_name="leetato" health=20     scale=0.5></PlayerWidget>
        <PlayerWidget mc_name="amely07" health=16     scale=0.5></PlayerWidget>
        <PlayerWidget mc_name="Console_Bot" health=15 scale=0.5></PlayerWidget>
        <PlayerWidget mc_name="Darkli_" health=20     scale=0.5></PlayerWidget>
        <PlayerWidget mc_name="Louis_DS" health=6     scale=0.5></PlayerWidget>
        <PlayerWidget mc_name="nesrinn" health=19     scale=0.5></PlayerWidget>
        <PlayerWidget mc_name="fridaymelli" health=3  scale=0.5></PlayerWidget>
        <PlayerWidget mc_name="leetato" health=20     scale=0.5></PlayerWidget>
        <PlayerWidget mc_name="amely07" health=16     scale=0.5></PlayerWidget>
        <PlayerWidget mc_name="Console_Bot" health=15 scale=0.5></PlayerWidget>
        <PlayerWidget mc_name="Darkli_" health=20     scale=0.5></PlayerWidget>
        <PlayerWidget mc_name="Louis_DS" health=6     scale=0.5></PlayerWidget>
        <PlayerWidget mc_name="nesrinn" health=19     scale=0.5></PlayerWidget>
        <PlayerWidget mc_name="fridaymelli" health=3  scale=0.5></PlayerWidget>
        <PlayerWidget mc_name="leetato" health=20     scale=0.5></PlayerWidget>
        <PlayerWidget mc_name="amely07" health=16     scale=0.5></PlayerWidget>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import PlayerWidget from '@/components/minecraft/PlayerWidget.vue'
import VueTerminal from '@/components/console/VueTerminal.vue'

export default {
  name: 'Home',
  components: {
    PlayerWidget,
    VueTerminal
  },
  data () {
    return {
      ex1: { label: 'color', val: 25, color: 'orange darken-3' }
    }
  },
  methods: {
    onCliCommand (data, resolve, reject) {
      // typed command is available in data.text
      // don't forget to resolve or reject the Promise
      setTimeout(() => {
      }, 1)
      resolve('Lel')
    },
    sliderInput (e) {
      this.sliderValue = e
      return this.sliderValue
    }
  }
}
</script>

<style scoped
    MinecraftConsole lang="scss">
.interface {
  margin: 32px;
  display: flex;
  flex-direction: row;
  align-items: flex-start;
  justify-content: right;
  flex-wrap: wrap;
}
.players {
  flex: none;
  display: inline-grid;
  flex-direction: column;
}
.term {
  flex: auto;
  min-width: 300px;
  height: 800px;
  margin-right: 2rem;
}
.prompt {
  border-radius: 12px;
}
</style>
