<template>
  <div class="finances-body">
      <div class="controls">
          <input type="number" class="control" id="sum" placeholder="Spend 300$"><br>
      <input type="text" class="control"  id="cause" placeholder="For food !"><br>

      <button class="append" @click="addFinance">Append</button>
      <button class="append" @click='$emit("exitFromTransaction")'>Decline</button>
      </div>
  </div>
</template>

<script>

// Export Default
export default {

    props: ['type'],

    // Application Data
    data(){
        return {

            Finances : {
                increase: [],
                decrease: [],
            }

        }
    },

    methods: {
        addFinance ( type ) {

            let sum = document.getElementById('sum').value,
                cause = document.getElementById('cause').value;

            // LITTLE VALIDATION
            if ( sum === '' && cause === '' ) {
                alert('Please, type sum and cause ! ');
                return false;
            } else if ( sum === '' && cause != '' ) {
                alert ( 'Type, sum !' )
                return false;
            } else if ( sum != '' && cause === '' ) {
                alert( 'Please, type cause !' );
                return false;
            }

            // MAIN EVENT
            if ( this.type === 'add' ) {

                this.$emit( 'hasBeenOperated', {
                    sum: sum,
                    cause: cause,
                    type: 'add'
                });

            } else {

                this.$emit( 'hasBeenOperated', {
                    sum: sum,
                    cause: cause,
                    type: 'subtract'
                });
                
            }

        }
    }

}

</script>

<style lang = 'scss' scoped>

.finances-body {
    width: 100vw;
    height: 100vh;
    background: linear-gradient(45deg, rgba(64, 126, 241, 0.4), rgba(81, 240, 205, 0.582)), url('../assets/img/transaction-bg.jpg');
    position: absolute;
    background-size: cover;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    text-align: center;
    padding: 30px;
}

.control {
    width: 500px;
    opacity: .5;
    height: 100px;
    border-radius: 20px;
    margin-top: 30px;
    font-family: 'Helvetica Neue';
    font-weight: 100;
    padding-left: 20px;
    box-sizing: border-box;
    font-size: 2em;
    text-align: center;
    background: rgba(255,255,255, 1);
    transition: all .3s;
}

.control:focus {
    transform: scale(.9);
    background: #fff;
    color: #000;
    opacity: 1;
}

.controls {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}

.append {
    width: 200px;
    height: 80px;
    background: transparent;
    border: 1px solid #fff;
    color: #fff;
    text-transform: uppercase;
    font-weight: 100;
    font-size: 1.4em;
    margin-top: 50px;
    transition: all .4s;
    cursor: pointer;
    margin: 10px;
    margin-top: 40px;
}

.append:hover {
    transform: scale(.9);
    background: #fff;
    color: #000;
}

</style>