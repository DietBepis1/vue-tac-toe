<template>
    <div>
        <li class='tile'>
            <button class='tile__btn' v-on:click='markTile(activePlayer, item)'>
                {{tileIsClicked}}
            </button>
        </li>
    </div>
</template>

<script>
export default {
    name: 'BoardTile',
    props: ['item', 'activePlayer'],
    data() {
        return {
            tileIsClicked: ''
        }
    },
    methods: {
        markTile(activePlayer, item) {
            
            if(!this.tileIsClicked){
                this.tileIsClicked = activePlayer;
                this.$emit('change-active-player', item);
            }
            
        }
    }
}
</script>

<style scoped>
    @import '../styles/BoardTile.css';
</style>