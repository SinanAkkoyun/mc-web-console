<template>
<!--
<div class="player">
  <div style="position: absolute; width: 100%; height: 100%;top: 0; left: 0; display: flex; flex-direction: row; flex-wrap: none; align-items: flex-end;">
    <div class="head">
      <img class="headimg" :src="`https://cravatar.eu/helmavatar/${mc_name}/190.png`">
    </div>
    <div class="healthbar">
      <div class="healthbar-section">
        <img class="heart" v-for="index in 5" :key="index" :src="getHeartImg(index, 0)">
      </div>
      <div class="healthbar-section">
        <img class="heart" v-for="index in 5" :key="index" :src="getHeartImg(index, 1)">
      </div>
    </div>
  </div>
  <div class="playerinfo" style="width: 100%;">
    <div>
      <div class="mcnamecontainer" style="position: relative; opacity: 0;"><div class="mcname" style="min-width:204px;">{{ mc_name }}</div></div>
        <div class="mcname" style="position: absolute">{{ mc_name }}</div>
      </div>
      <div class="head"></div>
    </div>
</div>
-->
<div class="player">
  <div class="head" :style="head">
    <img class="headimg" :style="headimg" :src="`https://cravatar.eu/helmavatar/${mc_name}/190.png`">
  </div>
  <div class="playerinfo">
    <div class="mcnamecontainer" style="position: relative; opacity: 0;"><div class="mcname" :style="[{'min-width': `{204 * this.scale}px`}, mcname]">{{ mc_name }}</div></div>
    <div class="mcname" :style="mcname" style="position: absolute">{{ mc_name }}</div>

    <div class="healthbar" :style="healthbar">
      <div class="healthbar-section"><img class="heart" :style="heart" v-for="index in 5" :key="index" :src="getHeartImg(index, 0)"></div>
      <div class="healthbar-section"><img class="heart" :style="heart" v-for="index in 5" :key="index" :src="getHeartImg(index, 1)"></div>
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: 'PlayerWidget',
  props: {
    mc_name: String,
    health: Number,
    scale: {
      type: Number,
      default: 1
    }
  },
  methods: {
    getHeartImg (index, row) {
      const pos = index + row * 5 // +1 because of index

      if (pos <= Math.floor(this.health / 2)) {
        return require('@/assets/minecraft/healthbar/heart_full_10.png')
      } else if (pos <= Math.ceil(this.health / 2)) {
        return require('@/assets/minecraft/healthbar/heart_half_10.png')
      } else {
        return require('@/assets/minecraft/healthbar/heart_empty_10.png')
      }
    }
  },
  computed: {
    head () {
      return {
        height: `${64 * this.scale}px`,
        width: `${64 * this.scale}px`
      }
    },
    headimg () {
      return {
        'border-radius': `${6 * this.scale}px`
      }
    },
    mcname () {
      return {
        'font-size': `${24 * this.scale}px`,
        'max-height': `${38 * this.scale}px`,
        'border-radius': `${6 * this.scale}px`,
        'padding-left': `${6 * this.scale}px`,
        'padding-right': `${6 * this.scale}px`
      }
    },
    healthbar () {
      return {
        'margin-top': `${2 * this.scale}px`
      }
    },
    heart () {
      return {
        'margin-right': `${-2.5 * this.scale}px`,
        'border-radius': '0px',
        width: `${24 * this.scale}px`,
        height: `${24 * this.scale}px`
      }
    }
  }
}

</script>

<style scoped>
@font-face { font-family: Minecraft; src: url('~@/assets/fonts/Minecraft.ttf'); }
.player {
  display: flex;
  flex-direction: row;
  margin: 8px;
  position: relative;
}
.head {
  width: 64px;
  height: 64px;
  flex: none;
  margin-right: 8px;
}
.headimg {
  width: 100%;
  height: 100%;
}
.playerinfo {
  flex: auto;
  display: flex;
  flex-direction: column;
}
.mcnamecontainer {
  /*display: flex;
  justify-content: flex-start;*/
  float: right;
}
.mcname {
  flex: none;
  font-family: Minecraft;
  font-smooth: never;
  -webkit-font-smoothing : none;
  font-size: 24px;
  max-height: 38px;
  border-radius: 6px;
  padding-left: 6px;
  padding-right: 6px;
  background-color:#0a0a0ac4;
  color:#ffffff;
}
.healthbar {
  flex: none;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: left;
  align-items: bottom;
  margin-top: 2px;
}
.healthbar-section {
  flex: none;
  display: flex;
  flex-direction: row;
  flex-wrap: none;
}
.heart {
  flex: none;
  margin-right: -2.5px;
  border-radius: 0px;
  width: 24px;
  height: 24px;
  image-rendering: -webkit-optimize-contrast;
}
</style>

<!--
<style scoped>
@font-face { font-family: Minecraft; src: url('~@/assets/fonts/Minecraft.ttf'); }
.player {
  /*flex: none;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: flex-start;*/
  flex: none;
  margin: 8px;
  position: relative;
  background-color: lightgreen;
}
.head {
  width: 64px;
  height: 64px;
  margin-right: 8px;
  flex: none;
}
.headimg {
  border-radius: 6px;
  width: 100%; height: 100%;
}
.playerinfo {
  display: flex;
  flex-direction: row-reverse;
  justify-content: left;
  flex-wrap: wrap;
  /*margin-left: 8px;*/
  gap: 3px;
}
.mcnamecontainer {
  /*display: flex;
  justify-content: flex-start;*/
  float: right;
}
.mcname {
  font-family: Minecraft;
  font-smooth: never;
  -webkit-font-smoothing : none;
  /*font-size:24px;*/
  font-size:24px;
  max-height: 38px;
  border-radius: 6px;
  padding-left:6px;padding-right:6px;background-color:#0a0a0ac4;color:#ffffff;
}
.healthbar {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: left;
  margin-left: 4px;
}
.healthbar-section {
  flex: none;
  display: flex;
  flex-direction: row;
  flex-wrap: none;
}
.heart {
  flex: none;
  margin-right: -2.5px;
  border-radius: 0px;
  width: 24px;
  height: 24px;
  image-rendering: -webkit-optimize-contrast;
}
</style>
-->
