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
            <div class="circle_min circle_min1_left animate__animated" :class="fade_in" v-show="show_left">
            </div>
            <div class="circle_min circle_min2_left animate__animated" :class="fade_in" v-show="show_left">
            </div>
            <div class="circle_min circle_min3_left animate__animated" :class="fade_in" v-show="show_left">
            </div>
            <div :class="userSuperiorClass" class="game1_user">
                <div :class="`${userInteriorClass}-interior`">
                    <img :src="userImage" alt="user choice">
                </div>
            </div>
        </div>
        <div class="play_again animate__animated" v-show="show_play_again" :class="zoom_in_down">
            <div class="winner_is">
                <h1>{{ winner_lose }}</h1>
                <button @click="play_again">PLAY AGAIN</button>
            </div>
        </div>
        <div class="images_game game-picked">
            <div class="circle_min circle_min1_right animate__animated" :class="fade_in" v-show="show_right">
            </div>
            <div class="circle_min circle_min2_right animate__animated" :class="fade_in" v-show="show_right">
            </div>
            <div class="circle_min circle_min3_right animate__animated" :class="fade_in" v-show="show_right">
            </div>
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
            cont: 0,
            winner_lose: '',
            fade_in: '',
            zoom_in_down: '',
            show_right: false,
            show_left: false,
            show_play_again: false,
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
            let select_user = this.select_user;
            let machine_user = this.select_machine;
            let result;
            if (select_user === machine_user) {
                result = "EMPATE";
                this.winner_lose = "IT'S A DRAW";
            } else if (
                (select_user === "paper" && machine_user === "rock") ||
                (select_user === "rock" && machine_user === "scissors") ||
                (select_user === "scissors" && machine_user === "paper")
            ) {
                result = "Winner is USER";
                this.cont += 1;
                this.fade_in = "animate__fadeIn";
                this.show_left = true;
                console.log('Valor de cont antes de emitir el evento:', this.cont);
                this.winner_lose = "YOU WIN";
            } else {
                result = "Winner is MACHINE";
                this.fade_in = "animate__fadeIn";
                this.show_right = true;
                this.winner_lose = "YOU LOSE";
            }
            console.log(result);
            setTimeout(()=> {
                this.show_play_again = true
                this.zoom_in_down = 'animate__zoomInDown';
            }, 2000)
            this.$emit('update_number', this.cont);
        },
        play_again(){
            let showpicks = this.$refs.pick;
            showpicks.style.display = 'none';
            let OpenCloseNav = this.$refs.OpenCloseNav;
            OpenCloseNav.style.display = 'flex';
            this.user_select = '';
            this.machine_select = '';
            this.zoom_in_out = '';
            this.winner_lose = '';
            this.fade_in = '';
            this.zoom_in_down = '';
            this.show_right = false;
            this.show_left = false;
            this.show_play_again = false;
            this.userSuperiorClass = "";
            this.userInteriorClass = "";
            this.userImage = "";
            this.machineSuperiorClass = "";
            this.machineInteriorClass = "";
            this.machineImage = "";
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
    .circle_min
        border: none
        border-radius: 100%
        width: 225px
        height: 225px
        position: absolute
    .circle_min1_left
        background-color: hsla(217, 16%, 45%, 0.14)
        top: -0.6rem !important
        left: -8.8rem !important
    .circle_min2_left
        background-color: hsla(217, 16%, 45%, 0.10)
        width: 300px
        height: 300px
        top: -3.1rem !important
        left: -11.2rem !important
    .circle_min3_left
        background-color: hsla(217, 16%, 45%, 0.06)
        width: 375px
        height: 375px
        top: -5.3rem !important
        left: -13.7rem !important
    .circle_min1_right
        background-color: hsla(217, 16%, 45%, 0.14)
        top: -0.6rem !important
        left: 21.7rem !important
    .circle_min2_right
        background-color: hsla(217, 16%, 45%, 0.10)
        width: 300px
        height: 300px
        top: -2.9rem !important
        left: 19.3rem !important
    .circle_min3_right
        background-color: hsla(217, 16%, 45%, 0.06)
        width: 375px
        height: 375px
        top: -5.2rem !important
        left: 17rem !important
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
.play_again
    display: flex
    align-items: center
    justify-content: center
    flex-direction: column
    position: absolute
    top: 20rem
    .winner_is
        display: flex
        align-items: center
        justify-content: center
        flex-direction: column
        h1
            font-size: 2.4rem
            letter-spacing: 0.1rem
            margin-bottom: 2%
        button
            margin-top: 5%
            border: none
            background: #fff
            color: hsl(229, 25%, 31%)
            width: 8.5rem
            height: 2rem
            border-radius: 5px
            font-weight: 600
            letter-spacing: 0.1rem
            transition: ease-in-out
            transition-duration: 0.2s
            cursor: pointer
            &:hover
                transform: scale(1.1)
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