<template>
  <div class="stats-content">
      <button class="exit-btn" @click='$emit("exitFromStats")'>Exit</button>
  </div>
</template>

<script>

export default {
    
}

</script>

<style lang = 'scss' scoped>

.stats-content {
    width: 100vw;
    height: 100vh;
    background: #eee;
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
</style>