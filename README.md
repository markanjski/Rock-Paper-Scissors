# Rock-Paper-Scissors
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <script>
    function computerPlay() {
      let rand = Math.floor(Math.random() * 3 + 1);
      if (rand == 1) return "Rock";
      else if (rand == 2) return "Paper";
      else return "Scissors";
    }

    function getNumber(str) {
      if (str.localeCompare("Rock") == 0) return 1;
      else if (str.localeCompare("Paper") == 0) return 2;
      else if (str.localeCompare("Scissors") == 0) return 3;
      else return 0;
    }

    function userInput() {
      let playerSelection = 0, string;
      while (playerSelection == 0) {
        let result = prompt("Rock, Paper or Scissors.\nEnter your pick now:");
        string = result[0].toUpperCase() + result.slice(1).toLowerCase();
        playerSelection = getNumber(string);
      }      
      return string;
    }

    function oneRound(playerSel, compSel) {
      playerSel = playerSel[0].toUpperCase() + playerSel.slice(1).toLowerCase();
      compSel = compSel[0].toUpperCase() + compSel.slice(1).toLowerCase();
      let compNum = getNumber(compSel), playNum = getNumber(playerSel);
      let result = playNum - compNum;
      if(result == -1 || result == 2){
        console.log(`You Lose! ${compSel} beats ${playerSel}`);
        return -1;
      }
      else if(result == 1 || result == -2){
        console.log(`You Won! ${playerSel} beats ${compSel}`);
        return 1;
      }
      else{
        console.log(`I's a Tie! You both chose ${playerSel}`);
        return 0;
      }
      console.log(playNum, compNum);
    }

    function game() {
      let playerScr = 0, compScr = 0, tempScore;
      for(let i = 0; i < 5; i++){
        tempScore = oneRound(userInput(), computerPlay());
        if(tempScore == 1) playerScr++;
        else if(tempScore == -1) compScr++; 
      }
      return `\n***************************\n*** THE FINAL SCORE IS: ***\n***  YOU ${playerScr} : ${compScr} COMPUTER ***\n***************************`;
    }

    console.log(game());
    
  </script>
</head>
<body>
</body>
</html>
