<template>
  <div class="app-content">

<transition name = 'flip' mode="out-in">
        <header-app @openAuthor='openAuthor' @showStats = 'showStats' v-if='state == "start"' @changeState = 'changeState' :money = 'sMoney'  ></header-app>
        <finances @exitFromTransaction = 'exitFromTransaction' :type = 'type'  v-else-if='state == "operation"' @hasBeenOperated = 'hasBeenOperated'></finances>
        <stats @exitFromStats = 'exitFromStats' :finances = 'Finances' v-else-if='state === "stats"'></stats>
        <author @exitFromStats = 'exitFromStats' v-else-if='state === "author"'></author>
</transition>

  </div>
</template>

<script>
// Import Components
Vue.component('header-app', require('./header.vue').default );
Vue.component('finances', require('./finances.vue').default );
Vue.component('stats', require('./stats.vue').default );
Vue.component('author', require('./author.vue').default );

// Export Default
export default {

    // Application Data
    data(){
        return {
            state: 'start',
            MONEY: 8342,
            
            type: '',

            Finances: {
                increase : [],
                decrease : [],
            }
        }
    },

    computed: {
        sMoney () {

            let money = this.MONEY;

            for ( let i of this.Finances.increase ) {
                money += parseFloat(i.money);
            } for ( let i of this.Finances.decrease ) {
                money -= parseFloat( i.money );
            }

            return money;
        }
    },

    methods: {
        changeState ( type ) {
            this.type = type;
            this.state = 'operation';
        },

        hasBeenOperated ( finances ) {
            this.state = 'start';
            if ( finances.type === 'add' ) {
                this.Finances.increase.push({
                    money : finances.sum,
                    cause : finances.cause,
                })
            } else {
                this.Finances.decrease.push({
                    money : finances.sum,
                    cause : finances.cause
                })
            }
        },

        showStats () {
            this.state = 'stats';
        },

        exitFromStats () {
            this.state = 'start';
        },

        openAuthor () {
            this.state = 'author';
        },

        exitFromTransaction () {
            this.state = 'start';
        }
    }

}

</script>

<style lang = 'scss' scoped>

.app-content {
    width: 100vw;
    height: 100vh;
    background: #eee;
}


.flip-enter-active {
    animation: flipIn .3s;
}

.flip-leave-active {
    animation: flipOut .3s; 
}


@keyframes flipIn {
    from {
        opacity: 0;
    } to {
        opacity: 1;
    }
}

@keyframes flipOut {
    from {
        opacity: 1;
    } to {
        opacity: 0;  
    }
}

</style>