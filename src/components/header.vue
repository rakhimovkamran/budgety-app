<template>
  <div class="header-content">
     <h1 class="app-heading" @click='$emit("openAuthor")'>Budgety</h1>

    <div class="controls">
        <button class="btn control btn-plus" @click = 'operate("add")' >+</button>
        <h1 class="budget-renderer control" >{{ money.toLocaleString() }} $</h1>
        <button class="btn control btn-minus" @click = 'operate("subtract")'>-</button>
    </div>

    <h1 class="app-footing" @click='$emit("showStats")'>Finance Info</h1>
  </div>
</template>

<script>

// Export Default
export default {

    props: [ 'money' ],

    // Application Data
    data(){
        return {

        }
    },

    methods: {
        operate ( type ) {
            if ( type === 'add' ) {

                this.$emit('changeState', 'add')

            } else if ( type === 'subtract' ) {

                this.$emit('changeState', 'subtract')                

            }
        }
    }

}

</script>

<style lang = 'scss' scoped>

$font: 'Helvetica Neue';

.header-content {
    width: 100vw;
    height: 100vh;
    background: linear-gradient(45deg, rgba(64, 191, 241, 0.4), rgba(81, 110, 240, 0.582)), url('../assets/img/heading-bg.jpg');
    background-size: cover;
    text-align:center;
    padding: 30px;
    color: #fff;
    text-transform: uppercase;
    font-family: $font;
}

.app-heading {
    font-weight: 100;
    font-size: 2em;
    letter-spacing: 5px;
    margin-bottom: 30px;
    cursor: pointer;
    width: 100vw;
    height: 15vh;
    font-size: 2em;
    font-weight: 100;
    position: absolute;
    top: 0;
    left: 0;
    transition: all .2s;
    line-height: 15vh;
}

.app-heading:hover {
   background: rgba(0,0,0,.5);
}

.budget-renderer {
    font-size: 4em;
    font-weight: 100;
}

.controls {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 100vw;
}

.btn {
    width: 80px;
    height: 80px;
    background: transparent;
    border-radius: 50%;
    color:#fff;
    text-transform: uppercase;
    transition: all .3s;
    margin: 20px;
    font-family: Verdana;
    cursor: pointer;
    font-size: 4em;
}

.btn:hover {
    transform: scale(.9);
}

.btn-plus:hover {
    color: rgb(60, 206, 133);
}

.btn-minus:hover {
    color: rgb(216, 96, 96);
}

.control {
    display: inline-block;
}


.app-footing {
    width: 100vw;
    height: 15vh;
    font-size: 2em;
    font-weight: 100;
    position: absolute;
    bottom: 0;
    left: 0;
    transition: all .2s;
    line-height: 15vh;
    cursor: pointer;
}

.app-footing:hover {
   background: rgba(0,0,0,.5);
}

</style>