<template>
  <div class="stats-content">
      <div class="increase stat">
          <h1 class="headline">Incoming</h1>
          <hr class="headline-hr"><br>
          <div class="item i-i" v-for='increase of finances.increase'>
              {{increase.cause}} - {{increase.money.toLocaleString()}} $
            </div>
      </div>
      <button class="exit-btn" @click='$emit("exitFromStats")'>Exit</button>
      <div class="decrease stat">
        <h1 class="headline">Outgoing</h1>
          <hr class="headline-hr"><br>
          <h3 class="item i-d" v-for='decrease of finances.decrease'>{{decrease.cause}} - {{decrease.money.toLocaleString()}} $</h3>
      </div>
  </div>
</template>

<script>

export default {
    props : [ 'finances' ]
}

</script>

<style lang = 'scss' scoped>

.stats-content {
    width: 100vw;
    height: 100vh;
    background: #eee;
}

.stat {
    text-align: center;
    width: 50vw;
    height: 100vh;
}

.increase {
    float: left;
}

.decrease {
    float: right;
}

.exit-btn {
    width: 100px;
    height: 100px;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background: transparent;
    border-radius: 50%;
    text-transform: uppercase;
    font-weight: 100;
    transition: all .4s;
    font-size: 1.3em;
    letter-spacing: 2px;
    cursor: pointer;
}

.exit-btn:hover {
    background: #333;
    color: #fff;
}

.headline {
    font-size: 3em;
    margin-top: 20px;
    text-transform: uppercase;
    font-weight: 100;
    font-family: 'Helvetica Neue';
}

.headline-hr {
    width: 500px;
    border: none;
    border-bottom: 1px solid #000;
}

.item {
    font-family: 'Helvetica Neue';
    font-size: 2em;
    font-weight: 100;
    text-transform: uppercase;
}

.i-i {
    color: rgb(29, 105, 70);
}

.i-d {
    color: rgb(211, 80, 80);
}

</style>