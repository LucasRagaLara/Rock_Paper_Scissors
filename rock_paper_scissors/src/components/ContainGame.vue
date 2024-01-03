<template>
    <div class="box_game">
        <div class="game animate__animated" :class="zoom_in_out" ref="OpenCloseNav" @animationend="finaltransition">
            <img src="../assets/bg-triangle.svg" alt="" class="to_back">
                <div class="images_game">
                    <div class="game1" @click="selectPaper">
                        <div class="game1-interior">
                            <img src="../assets/icon-paper.svg">
                        </div>
                    </div>
                    <div class="game2" @click="selectScissors">
                        <div class="game2-interior">
                            <img src="../assets/icon-scissors.svg">
                        </div>
                    </div>
                    <div class="game3" @click="selectRock">
                        <div class="game3-interior">
                            <img src="../assets/icon-rock.svg">
                        </div>
                    </div>
                </div>
        </div>
    </div>
    <div id="picked" ref="pick">
        <h3 class="you_picked">You picked</h3>
        <h3 class="the_machine_picked">The Computer picked</h3>
        <div class="images_game game-picked">
            <div :class="userSuperiorClass" class="game1_user">
                <div :class="`${userInteriorClass}-interior`">
                    <img :src="userImage" alt="user choice">
                </div>
            </div>
        </div>
        <div class="images_game game-picked">
            <div :class="machineSuperiorClass" class="game1_machine">
                <div :class="`${machineInteriorClass}-interior`">
                    <img :src="machineImage">
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: 'ContainGame',
    data (){
        return{
            user_select: '',
            machine_select: '',
            zoom_in_out: '',
            userSuperiorClass: "",
            userInteriorClass: "",
            userImage: "",
            machineSuperiorClass: "",
            machineInteriorClass: "",
            machineImage: ""
        }
    },
    methods: {
        selectPaper(){
            console.log("Has seleccionado papel")
            let showpicks = this.$refs.pick;
            if (this.zoom_in_out === ''){
                this.zoom_in_out = 'animate__zoomOut';
                showpicks.style.display = 'flex';
            }
            this.userSuperiorClass = "game1";
            this.userInteriorClass = "game1";
            this.userImage = require("../assets/icon-paper.svg");
            this.select_user = 'paper';
            setTimeout(() => {
                this.selectMachine()
            }, 2000)
            setTimeout(() => {
                this.winnerIs()
            }, 2000)
        },
        selectScissors(){
            console.log("Has seleccionado tijeras");
            let showpicks = this.$refs.pick;
            if (this.zoom_in_out === ''){
                this.zoom_in_out = 'animate__zoomOut';
                showpicks.style.display = 'flex';
            }
            this.userSuperiorClass = "game2";
            this.userInteriorClass = "game2";
            this.userImage = require("../assets/icon-scissors.svg");
            this.select_user = 'scissors';
            setTimeout(() => {
                this.selectMachine()
            }, 2000)
            setTimeout(() => {
                this.winnerIs()
            }, 2000)
        },
        selectRock(){
            console.log("Has seleccionado roca");
            let showpicks = this.$refs.pick;
            if (this.zoom_in_out === ''){
                this.zoom_in_out = 'animate__zoomOut';
                showpicks.style.display = 'flex';
            }
            this.userSuperiorClass = "game3";
            this.userInteriorClass = "game3";
            this.userImage = require("../assets/icon-rock.svg");
            this.select_user = 'rock';
            setTimeout(() => {
                this.selectMachine()
            }, 2000)
            setTimeout(() => {
                this.winnerIs()
            }, 2000)
        },
        selectMachine(){
            let machineOptions = ["rock", "paper", "scissors"];
            let randomIndex = Math.floor(Math.random() * machineOptions.length);
            let machineChoice = machineOptions[randomIndex];
            if (machineChoice == "rock"){
                let showpicks = this.$refs.pick;
                if (this.zoom_in_out === ''){
                    this.zoom_in_out = 'animate__zoomOut';
                    showpicks.style.display = 'flex';
                }
                this.machineSuperiorClass = "game3";
                this.machineInteriorClass = "game3";
                this.machineImage = require("../assets/icon-rock.svg");
                this.select_machine = 'rock';
            } else if(machineChoice == "scissors") {
                let showpicks = this.$refs.pick;
                if (this.zoom_in_out === ''){
                    this.zoom_in_out = 'animate__zoomOut';
                    showpicks.style.display = 'flex';
                }
                this.machineSuperiorClass = "game2";
                this.machineInteriorClass = "game2";
                this.machineImage = require("../assets/icon-scissors.svg");
                this.select_machine = 'scissors';
            }else if(machineChoice == "paper") {
                let showpicks = this.$refs.pick;
                if (this.zoom_in_out === ''){
                    this.zoom_in_out = 'animate__zoomOut';
                    showpicks.style.display = 'flex';
                }
                this.machineSuperiorClass = "game1";
                this.machineInteriorClass = "game1";
                this.machineImage = require("../assets/icon-paper.svg");
                this.select_machine = 'paper';
            }
            // lo mismo para el resto
        },
        finaltransition(){
            let OpenCloseNav = this.$refs.OpenCloseNav;
            if (this.zoom_in_out === 'animate__zoomOut'){
                OpenCloseNav.style.display = 'none';
            }else{
                OpenCloseNav.style.display = 'flex';
            }
        },
        winnerIs(){
            let select_user = this.select_user
            let machine_user = this.select_machine
            if (select_user == "paper"){
                if (machine_user == "rock"){
                    console.log("winner is USER")
                }else if (machine_user == "scissors"){
                    console.log("Winner is MACHINE")
                }else {
                    console.log("EMPATE")
                }
            } else if(select_user == "rock"){
                if (machine_user == "scissors"){
                    console.log("winner is USER")
                }else if (machine_user == "paper"){
                    console.log("Winner is MACHINE")
                }else {
                    console.log("EMPATE")
                }
            }else if(select_user == "scissors"){
                if (machine_user == "paper"){
                    console.log("winner is USER")
                }else if (machine_user == "rock"){
                    console.log("Winner is MACHINE")
                }else {
                    console.log("EMPATE")
                }
            }
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="sass">
#picked
    display: none
    align-items: center
    width: 100%
    justify-content: center
    color: #fff
    .you_picked, .the_machine_picked
        width: 30%
        display: flex
        align-items: center
        margin-top: 5%
        position: absolute
        top: 9.375rem
        justify-content: center
        letter-spacing: 0.1rem
    .the_machine_picked
        right: 18.75rem
    .you_picked
        left: 17.1875rem
.game-picked
    width: 30%
    display: flex
    align-items: center
    margin-top: 5%
    position: absolute
    top: 200px
    justify-content: center
    .game1, .game2, .game3
        top: 0px
        bottom: 0px
        left: 0px
        right: 0px
        cursor: inherit
        transition: none
        &:hover
            transform: none
    .game1_user
        top: 1.75rem !important
        left: -6.4rem !important
    .game1_machine
        top: 1.75rem !important
        left: 24rem !important
.box_game
    display: flex
    align-items: center
    justify-content: center
    margin-top: 2%
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
    cursor: pointer
    content: ""
    height: 150px
    width: 150px
    background-image: linear-gradient(to right, hsl(230, 89%, 62%), hsl(230, 89%, 65%))
    border-radius: 100%
    top: -200px
    right: 50px
    transition: ease-in-out
    transition-duration: 0.2s
    &:hover
        transform: scale(1.1)
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
.game2
    background-image: linear-gradient(to right, hsl(39, 89%, 49%), hsl(40, 84%, 53%))
    top: -200px
    right: -200px
    &:hover
        transform: scale(1.1)
.game3
    background-image: linear-gradient(to right, hsl(349, 71%, 52%), hsl(349, 70%, 56%))
    top: 0px
    left: -75px
    &:hover
        transform: scale(1.1)
</style>