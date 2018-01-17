/* eslint-disable */
 // eslint-disable-next-line
<template>
    <div>
    <span v-hide v-html="welcomeMessage"></span>
    <form v-hide>
    <input name="player" placeholder="Entrez le nom du joueur" v-border:red />
    <button type="submit" >Joueur</button>
    </form>
    </div>
</template>
<script>
export default {
 name: 'joueur',
  
 created: function() {
     this.player = 'adel'
     this.welcomeMessage = this.player ? `Bonjour <span class="player">${this.player} !</span>` : ''
 },
 directives: {
     border: function(el, binding) {
         el.style.borderColor = binding.arg
     },
     hide: function(el,binding,vnode){
         let isForm = vnode.tag==="form" 
         let player = vnode.context.player
         if(isForm){
             el.style.display= player? "none" : "block"
         } else{
              el.style.display= player? "block" : "none"
         }
     }
 }
}
</script>
<style scoped>
.player form{
    display: none
}
.playerForm span{
    display: none
}
</style>