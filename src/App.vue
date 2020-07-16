<template>
  <div id="app">
    <h1 id="time">00:00</h1>
    <div id="controls">
      <button id="restart">Restart</button>
      <button id="start">Start</button>
      <button id="stop">Stop</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data: function() {

  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

#time {
  font-size: 6em;
  letter-spacing: 0.5em;
}
#controls {
  margin-left: -45px;
}

#controls button {
  margin: 10px;
  border: none;
  width: 80px;
  border-radius: 4px;
  padding: 8px;
  color:white
}

#controls #restart {
  background-color: rgb(61, 61, 145);
}
#controls #restart:hover {
  background-color: rgb(32, 32, 94);
  transition: 0.1s;
}
#controls #restart:active {
  background-color: rgba(32, 32, 94, 0.63);
  transition: 0.1s ease-out;
}


#controls #start {
  background-color: rgb(61, 145, 99);
}
#controls #start:hover {
  background-color: rgb(29, 88, 56);
  transition: 0.1s;
}
#controls #start:active {
  background-color: rgb(29, 88, 56, 0.63);
  transition: 0.1s ease-out;
}

#controls #stop {
  background-color: rgb(207, 27, 36);
}
#controls #stop:hover {
  background-color: rgb(129, 39, 43);
  transition: 0.1s;
}
#controls #stop:active {
  background-color: rgb(129, 39, 43, 0.63);
  transition: 0.1s ease-out;
}

</style>
