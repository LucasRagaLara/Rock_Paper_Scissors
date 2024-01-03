<template>
    <div>
        <ContainGame @update_number="update_count" />
        <HeaderUp :cont="cont" />
    </div>
</template>

<script>
import ContainGame from './ContainGame.vue';
import HeaderUp from './HeaderUp.vue';

export default {
data() {
    return {
    cont: 0
    };
},
methods: {
    update_count(cont) {
    this.cont = cont;
    }
},
components: {
    ContainGame,
    HeaderUp
}
};
</script>