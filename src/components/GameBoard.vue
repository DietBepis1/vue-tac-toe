<template>
    <div class="board">
        <ul v-for="item in boardSize" v-bind:key='item'>
            <BoardTile v-bind:item='item' v-bind:activePlayer='activePlayer' v-on:change-active-player="$emit('change-active-player', item)"/>
        </ul>
    </div>
</template>

<script>
import BoardTile from './BoardTile.vue';

export default {
    name: "GameBoard",
    components: {
        BoardTile
    },
    props: ['boardSize', 'activePlayer']
}

</script>

<style scoped>
    @import '../styles/GameBoard.css';
</style>