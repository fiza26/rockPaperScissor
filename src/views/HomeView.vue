<script>
export default {
  data() {
    return {
      choices: ['rock', 'paper', 'scissor'],
      userChoice: null,
      loading: false,
      computerChoice: null,
      result: null,
    }
  },
  methods: {
    play(userChoice) {
      this.userChoice = userChoice;
      this.loading = true;
      this.computerChoice = this.choices[Math.floor(Math.random() * 3)];
      this.calculateResult();  

      setTimeout(() => {
          this.loading = false;
        }, 1000);
      console.log(userChoice)
    },
    calculateResult() {
      if (this.userChoice === this. computerChoice) {
        this.result = "It's a tie!";
      } else if ((this.userChoice === 'rock' && this.computerChoice === 'scissor') || (this.userChoice === 'paper' && this.computerChoice === 'rock') || (this.userChoice === 'scissor' && this.computerChoice === 'paper')
      ) {
        this.result = 'You win!';
      } else {
        this.result = 'You lose!';
      }
    },
    restart() {
      this.userChoice = null;
      this.computerChoice = null;
      this.result = null;
    }
  }
}
</script>

<template>
  <main>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Poppins&display=swap" rel="stylesheet">
   
    <div class="container">
    <div class="circle"></div>
    <div class="circle-two"></div>
    <div class="circle-three"></div>
    <div class="box">
      <div class="content">
          <h2>ROCK SCISSOR PAPER</h2>
          <hr>
          <div class="choice" v-show="!userChoice">
              <div @click="play('rock')"><img src="https://i.pinimg.com/originals/97/9e/a3/979ea3d4122df7b5c0d051a4af59953f.png" alt=""></div>
              <div @click="play('paper')"><img src="https://static.vecteezy.com/system/resources/previews/009/340/337/original/white-crumpled-paper-balls-for-design-element-png.png" alt=""></div>
              <div @click="play('scissor')"><img src="https://images.vexels.com/media/users/3/177006/isolated/lists/aa415072f3348a3c78b663a307f8ac41-scissors-flat.png" alt=""></div>
          </div>
          <div class="loading" v-show="userChoice && loading === true"> 
            <div><img src="https://pngimg.com/uploads/fist/fist_PNG12.png" alt=""><p>You</p></div>
            <p>VS</p>
            <div><img src="https://pngimg.com/uploads/fist/fist_PNG12.png" alt=""><p>Computer</p></div>
          </div>
          <div class="result" v-show="result !== null && loading === false">
              <section>
              <h2>You Win!</h2>
              </section>
            <section>
              <div>{{ userChoice }}</div>
              <div><p>VS</p></div>
              <div>{{ computerChoice }}</div>
            </section>
            <button @click="restart">Restart</button>
          </div>
      </div>
    </div>
  </div>

  </main>
</template>

<style scoped>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    color: white;
    font-family: 'Poppins', sans-serif;
  }
  .container {
    margin: 10px;
  }
  .box {
    max-width: 550px;
    min-height: 370px;
    background: rgba(255, 255, 255, 0.25);
    backdrop-filter: blur(20px);
    border: 2px solid rgba(255, 255, 255, 0.18);
    border-radius: 40px;
    z-index: 1;
    margin: 100px auto;
  }
  .content {
    margin: 20px 50px;
    text-align: center;
  }
  .choice {
    display: flex;
    justify-content: center;
    margin-top: 70px;
  }
  .choice div {
    width: 150px;
    padding: 10px;
    margin-right: 10px;
    margin-left: 10px;
    cursor: pointer;
    border: 2px solid #fff;
    border-radius: 15px;
    transition: ease-in-out 0.3s;
    animation-name: choice-animation;
    animation-duration: 1s;
    animation-fill-mode: forwards;
  }
  .choice div:hover {
    transform: scale(1.2);
  }
  @keyframes choice-animation {
    0% {
      position: relative;
      bottom: -50px;
    }
    50% {
      position: relative;
      bottom: 50px;
    }
    60% {
      position: relative;
      bottom: 10px;
    }
    70% {
      position: relative;
      bottom: 50px;
    }
    100% {
      position: relative;
      bottom: 0px;
    }
  }
  .choice img {
    width: 100px;
    height: 100px;
  }
  .loading {
    display: flex;
    justify-content: space-around;
    margin-top: 70px;
    align-items: center;
  }
  .loading div {
    width: 150px;
    padding: 10px;
    margin-right: 10px;
    margin-left: 10px;
    cursor: pointer;
    border: 2px solid #fff;
    border-radius: 15px;
    transition: ease-in-out 0.3s;
    animation-name: choice-animation;
    animation-duration: 1s;
    animation-fill-mode: forwards;
  }
  .loading div img {
    width: 100px;
    height: 100px;
  }
  .result {
    display: flex;
    justify-content: space-around;
    flex-direction: column;
    align-items: center;
    margin-top: 70px;
  }
  .result section {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    margin-bottom: 10px;
  }
  .result div {
    width: 120px;
    padding: 10px;
    margin-top: 10px;
    margin-bottom: 10px;
    margin-right: 10px;
    margin-left: 10px;
    cursor: pointer;
    border: 2px solid #fff;
    border-radius: 15px;
    transition: ease-in-out 0.3s;
  }
  button {
    font-family: 'Poppins', sans-serif;
    width: 50%;
    height: 30px;
    border: none;
    color: black;
    border-radius: 15px;
    cursor: pointer;
  }
  
  .circle{
    position: absolute;
    width: 300px;
    height: 300px;
    transform: translate(20rem, 3rem);
    z-index: 0;
    border-radius: 50%;
    background: linear-gradient(to right,  #0062a3, #29ABE2);
    transition: ease-in-out 1s;
    animation-name: circle-animation;
    animation-duration: 1s;
    animation-fill-mode: forwards;
}
  .circle:hover {
    width: 500px;
    height: 500px;
  }

.circle-two{
    position: absolute;
    width: 300px;
    height: 300px;
    z-index: 0;
    border-radius: 50%;
    background: linear-gradient(to right, #F15, #F15A2A);
    transform: translate(50rem, -4rem);
    transition: ease-in-out 1s;
    animation-name: circle-animation-2;
    animation-duration: 1s;
    animation-fill-mode: forwards;
}
.circle-two:hover {
  width: 500px;
  height: 500px;
}
.circle-three {
    position: absolute;
    width: 300px;
    height: 300px;
    z-index: 0;
    border-radius: 50%;
    background: linear-gradient(to right, orange, #F15A2A);
    transform: translate(33rem, -4rem);
    transition: ease-in-out 3s;
    animation-name: circle-animation-3;
    animation-duration: 1s;
    animation-fill-mode: forwards;
}
.circle-three:hover {
  width: 500px;
  height: 500px;
  transform: scale(5);
}
@keyframes circle-animation {
  0% {
    transform: translate(-100rem, 0rem);
  }
  100% {
    transform: translate(20rem, 3rem);
  }
}
@keyframes circle-animation-2 {
  0% {
    transform: translate(100rem, 0rem);
  }
  100% {
    transform: translate(50rem, -4rem);
  }
}
@keyframes circle-animation-3 {
  0% {
    transform: translate(0rem, 100rem);
  }
  100% {
    transform: translate(33rem, -4rem);
  }
}

@media (max-width: 1024px) {
  .choice {
    display: flex;
    flex-wrap: wrap;
    margin: 10px;
  }
  .choice div {
    margin-bottom: 10px;
  }
  .circle, .circle-two, .circle-three {
    display: none;
  }
}
</style>