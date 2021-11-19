<template>
  <div class="home">
    <div>Sinan's Web panel</div>
    <div style="margin-top: 32px; display: flex; flex-direction: row; align-items: flex-start; justify-content: space-around; height: 100%;">
      <vue-command></vue-command>
      <div class="players">
        <PlayerWidget mc_name="Console_Bot" health=15></PlayerWidget>
        <PlayerWidget mc_name="Darkli_" health=20></PlayerWidget>
        <PlayerWidget mc_name="Louis_DS" health=6></PlayerWidget>
        <PlayerWidget mc_name="nesrinn" health=19></PlayerWidget>
        <PlayerWidget mc_name="fridaymelli" health=3></PlayerWidget>
        <PlayerWidget mc_name="leetato" health=20></PlayerWidget>
        <PlayerWidget mc_name="amely07" health=16></PlayerWidget>
        <PlayerWidget mc_name="scare_wolf" health=18></PlayerWidget>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import PlayerWidget from '@/components/minecraft/PlayerWidget.vue'
import VueCommand from '@/components/console/VueCommand'

export default {
  name: 'Home',
  components: {
    PlayerWidget,
    VueCommand
  }
}
</script>

<style scoped lang="scss">
$height: 700px;
$margin: 16px;
.players {
  display: flex;
  flex-direction: column;
  overflow-y: auto;
  max-height: $height;
  margin-right: $margin;
  /* max height is equal to console height */
  flex: auto;
}
.vue-command {
  flex: auto;
  min-width: 600px;
  height: $height;
  margin-left: 2rem;
  margin-right: $margin;
}
</style>
