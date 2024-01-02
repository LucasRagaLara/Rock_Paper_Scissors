<template>
    <div class="main_popup">
        <div id="PopUp" :class="zoom_in_out" class="animate__animated">
            <div class="header_rules">
                <h1>RULES</h1>
                <div class="box_image">
                    <img src="../assets/icon-close.svg" @click="ClosePopUp">
                </div>
            </div>
            <div class="image_rules">
                <img src="../assets/image-rules.svg">
            </div>
        </div>
        <div class="boton_foot">
            <button @click="OpenClosePopUp">RULES</button>
        </div>
    </div>
</template>
<script>
export default {
    name: 'PopUpRules',
    data (){
        return {
            zoom_in_out: 'animate__zoomIn'
        }
    },
    methods: {
        ClosePopUp(){
            this.zoom_in_out = 'animate__zoomOut';
        },
        OpenClosePopUp(){
            if (this.zoom_in_out == 'animate__zoomIn'){
                this.zoom_in_out = 'animate__zoomOut';
            }else if (this.zoom_in_out == 'animate__zoomOut'){
                this.zoom_in_out = 'animate__zoomIn'
            }
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="sass">
.main_popup
    display: flex
    flex-direction: column
    width: 100%
    align-items: center
    justify-content: center
#PopUp
    background-color: #fff
    display: flex
    flex-direction: column
    width: 30%
    border-radius: 15px
    .header_rules
        display: flex
        width: 100%
        height: 100px
        align-items: center
        justify-content: center
        padding: 0 7%
        h1
            color: #404366
            width: 85%
        .box_image
            display: flex
            justify-content: end
            width: 15%
            img
                width: 20px
                transition: ease-in-out
                transition-duration: 0.2s
                height: 20px
                &:hover
                    transform: scale(1.4)
    .image_rules
        display: flex
        align-items: center
        width: 100%
        justify-content: center
        margin-bottom: 5%
        img
            width: 65%
.boton_foot
    display: flex
    align-items: end 
    justify-content: end
    position: absolute
    bottom: -150px
    right: 50px
    button
        font-size: 18px
        color: #fff
        outline: none
        padding: 4%
        border: solid 1px #fff
        width: 140px
        height: 40px
        border-radius: 10px
        background: none
</style>