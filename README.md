# javascript-code
let userScore=0;
let compScore=0;

const choices=document.querySelectorAll(".choice");
const msg=document.querySelector("#msg");

const userScorePara=document.querySelector("#user-score");
const compScorePara=document.querySelector("#comp-score");

const genCompChoice=()=>{
    const options = ["rock","paper","scissors"];
    const  randIdx = Math.floor(Math.random()*3);
    return options[randIdx];
  

}

const drawGame=()=>{
    msg.innerText="Game was Draw,Play Again.";
    msg.style.backgroundColor="#081b31";
}
const showWinner=(userWin,userChoice,compChoice)=>{
    if(userWin){
        userScore++;
        userScorePara.innerText=userScore;
       
        msg.innerText=`You Win! your ${userChoice} beats ${compChoice}`;
        msg.style.backgroundColor="green";
    }else{
        compScore++;
        compScorePara.innerText=compScore;
        msg.innerText=`You lost! ${compChoice} beats your ${userChoice}`;
        msg.style.backgroundColor="red";
    }
}

const playGame=(userChoice)=>{
    console.log("user choice=",userChoice);
    //computer choice
    const compChoice = genCompChoice();
    console.log("comp choice =",compChoice);

    if(userChoice === compChoice){
        //drawgame
        drawGame();

    }else{
        let userWin=true;
        if(userChoice ==="rock"){
            userWin = compChoice ==="paper"?false:true;
        }else if(userChoice === "paper"){
            userWin=compChoice === "scissors"?false:true;
        }else{
            userWin=compChoice === "rock"?false:true;
        }
        showWinner(userWin,userChoice,compChoice);
    }

};


choices.forEach((choice)=>{
    choice.addEventListener("click",()=>{
        const userChoice=choice.getAttribute("id");
        playGame(userChoice);
    });
});


#html code
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="stylesheet" href="s.css">
    <title>Rock Paper Scissors Game</title>
    <body>
      <h1>Rock Paper Scissors </h1>
      <div class="choices">
        <div class="choice" id="rock">
          <img src="https://github.com/shradha-khapra/JavaScriptSeries/blob/main/StonePaperScissors/images/rock.png?raw=true">

        </div>

        <div class="choice" id="paper">
          <img src="https://github.com/shradha-khapra/JavaScriptSeries/blob/main/StonePaperScissors/images/paper.png?raw=true">

        </div>

        <div class="choice" id="scissors">
          <img src="https://github.com/shradha-khapra/JavaScriptSeries/blob/main/StonePaperScissors/images/scissors.png?raw=true">

        </div>
      </div>


      <div class="score-board">
        <div class="score">
          <p id="user-score">0</p>
          <p>You</p>
        </div>

        <div class="score">
          <p id="comp-score">0</p>
          <p>Comp</p>
        </div>

      </div>

      <div class="msg-container">
        <p id="msg">Play your move</p>
      </div>
      <script src="new.js"></script>
    </body>
    
  
</html>

#css code
*{
    margin:0;
    padding:0;
    text-align: center;
}
h1{
    background-color: #081b31;
    color:#fff;
    height:5rem;
    line-height:5rem;
}
.choice{
    height:165px;
    width:165px;
    border-radius:50%;
    display:flex;
    justify-content:center;
    align-items: center;
}

.choice:hover{
    cursor:pointer;
   background-color: #081b31;
}
img{
    height:150px;
    width:150px;
    object-fit:cover;
    border-radius:50%;
}

.choices{
    display:flex;
    justify-content:center;
    align-items:center;
    gap:3rem;
    margin-top:5rem;
}
.score-board{
    display:flex;
    justify-content: center;
    align-items: center;
    font-size: 2rem;
    margin-top: 3rem;
    gap:5rem;
}
#user-score,#comp-score{
    
    font-size:4rem;
}
.msg-container{
    margin-top:5rem;
}
#msg{
    background-color: #081b31;
    color: #fff;
    height:5rem;
    font-size: 2rem;
    margin-top: 2rem;
    display:inline;
    padding:1rem;
    border-radius:1rem;
}
