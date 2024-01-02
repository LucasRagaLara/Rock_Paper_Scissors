<template>
    <header id="menu">
        <div class="letters_menu">
            <ul class="letters">
                <li>ROCK</li>
                <li>PAPER</li>
                <li>SCISSORS</li>
                <!-- <img src="../src/assets/logo.svg" alt=""> -->
            </ul>
            <div class="box_score">
                <h5>SCORE</h5>
                <span>0</span>
            </div>
        </div>
    </header>
</template>

<script>
export default {
    name: 'HeaderUp'
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="sass">
#menu
    display: flex
    align-items: center
    justify-content: center
    padding-top: 3%
    .letters_menu
        color: #fff
        border: solid hsl(217, 16%, 45%)
        border-radius: 15px
        width: 50%
        display: flex
        align-items: center
        padding: 1% 2%
        .letters
            width: 80%
        .box_score
            background-color: #fff
            border-radius: 5px
            width: 125px
            padding-top: 1%
            height: 100px
            display: flex
            flex-direction: column
            align-items: center
            justify-content: center
            h5
                color: hsl(229, 64%, 46%)
                font-weight: 600
                letter-spacing: 0.1rem
            span
                color: #585468
                font-size: 50px
                font-weight: bold
        ul
            list-style: none
            li
                font-size: 32px
                font-weight: bold
                line-height: 1.5rem
</style>