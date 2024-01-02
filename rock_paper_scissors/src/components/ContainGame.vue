<template>
    <div class="game">
        <img src="../assets/bg-triangle.svg" alt="" class="to_back">
            <div class="images_game">
                <div class="game1">
                    <div class="game1-interior">
                        <img src="../assets/icon-paper.svg">
                    </div>
                </div>
                <div class="game2">
                    <div class="game2-interior">
                        <img src="../assets/icon-scissors.svg">
                    </div>
                </div>
                <div class="game3">
                    <div class="game3-interior">
                        <img src="../assets/icon-rock.svg">
                    </div>
                </div>
            </div>
    </div>
</template>

<script>
export default {
    name: 'ContainGame'
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="sass">
.game
    display: flex
    align-items: center
    justify-content: center
    width: 30%
    height: 400px
    .images_game
        position: absolute
        .game1, .game2, .game3
            position: absolute
            content: ""
            height: 150px
            width: 150px
            background-image: linear-gradient(to right, hsl(230, 89%, 62%), hsl(230, 89%, 65%))
            border-radius: 100%
            top: -200px
            right: 50px
        .game1-interior, .game2-interior, .game3-interior
            position: relative
            height: 110px
            width: 110px
            top: 14%
            left: 13%
            background-color: #fff
            z-index: 4
            border-radius: 50%
            display: flex
            align-items: center
            justify-content: center
            box-shadow: inset 0 10px 15px -10px rgba(0, 0, 0, 0.5), inset 0 -10px 15px -10px rgba(0, 0, 0, 0.5)
            img
                width: 50%
                .game1
        .game2
            background-image: linear-gradient(to right, hsl(39, 89%, 49%), hsl(40, 84%, 53%))
            top: -200px
            right: -200px
        .game3
            background-image: linear-gradient(to right, hsl(349, 71%, 52%), hsl(349, 70%, 56%))
            top: 0px
            left: -75px
</style>