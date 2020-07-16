<template>
  <div id="app">
    <h1 id="time">{{ curTime.toString().toHHMMSS() }}</h1>
    <div id="controls">
      <button @click="restart" id="restart">Restart</button>
      <button @click="start" id="start">Start</button>
      <button @click="stop" id="stop">Stop</button>
    </div>
  </div>
</template>

<script>
String.prototype.toHHMMSS = function() {
  var sec_num = parseInt(this, 10); // don't forget the second param
  var hours = Math.floor(sec_num / 3600);
  var minutes = Math.floor((sec_num - hours * 3600) / 60);
  var seconds = sec_num - hours * 3600 - minutes * 60;

  if (hours < 10) {
    hours = "0" + hours;
  }
  if (minutes < 10) {
    minutes = "0" + minutes;
  }
  if (seconds < 10) {
    seconds = "0" + seconds;
  }
  return hours + ":" + minutes + ":" + seconds;
};

var intvl = "";

export default {
  name: "App",
  data: function() {
    return {
      curTime: 0,
      startTime: 0,
      hasStarted: false,

      start: function() {
        if (this.hasStarted) {
          return;
        }
        this.startTime = new Date().getTime();
        this.hasStarted = true;
        console.log("Starting");
        intvl = setInterval(this.doCount, 1000, this);
      }.bind(this),

      restart: function() {
        console.log("Restarting");
        this.stop();
        this.start();
      }.bind(this),

      stop: function() {
        console.log("Stopping");
        clearInterval(intvl);
        this.curTime = 0;
        this.startTime = 0;
      }.bind(this)
    };
  },
  methods: {
    doCount: function(instance) {
      var now = new Date().getTime();
      instance.curTime = (now - instance.startTime) / 1000;
      console.log(instance.curTime);
    }
  }
};
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
  color: white;
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
