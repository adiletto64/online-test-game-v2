<template>
<div class="mr-3">
  <h5>Рейтинг игроков</h5>
  <div v-for="player in players">
    <div class="row">
      <div class="col-4">
        <h5 class="ml-1 mr-1">{{player.name}}</h5>
      </div>
      <div class="col-8">
        <div class="progress" style="height: 30px; margin-bottom: 10px">
          <div class="progress-bar bg-dark"
               role="progressbar"
               v-bind:style="{width: getPlayerScorePercent(player.score) + '%', height: '30px'}"
               aria-valuenow="25"
               aria-valuemin="0"
               aria-valuemax="100">
          </div>
          <h5><b>{{Math.ceil(player.score)}}</b></h5>
        </div>
      </div>
    </div>


</div>
</div>
</template>

<script lang="ts">
import {Component, Vue, Prop} from "vue-property-decorator";
import {Player} from "@/services/interfaces";

@Component
export default class LeaderShip extends Vue {
   @Prop(Array) players: Player[] = [];

   getPlayerScorePercent(score: number){
     let all: number = 0;
     this.players.forEach(function (player) {
       all += player.score;
     })
     return 100 / all * score;

   }
}
</script>

<style scoped>

</style>