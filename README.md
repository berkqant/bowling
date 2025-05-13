# bowling
A basic bowling score calculator using JavaScript logic to simulate real scoring rules, built during my internship.
let player1Score = 0;
let player2Score = 0;

function Bowling() {
    let player1Rolls = [];
    let player2Rolls = [];

    for (let frame = 1; frame <= 10; frame++) {
        console.log(`Frame ${frame}`);


        let player1Roll1 = parseInt(prompt(`Player 1 Frame ${frame}, Roll 1:`));
        if (player1Roll1 === 10) {
            
            player1Rolls.push(player1Roll1, 0); 
            console.log("Player 1 strike!");
        } else {
            let player1Roll2 = parseInt(prompt(`Player 1 Frame ${frame}, Roll 2:`));
            player1Rolls.push(player1Roll1, player1Roll2);
        }

        
        let player2Roll1 = parseInt(prompt(`Player 2 Frame ${frame}, Roll 1:`));
        if (player2Roll1 === 10) {
            
            player2Rolls.push(player2Roll1, 0); 
            console.log("Player 2 strike!");
        } else {
            let player2Roll2 = parseInt(prompt(`Player 2 Frame ${frame}, Roll 2:`));
            player2Rolls.push(player2Roll1, player2Roll2);
        }
    }

    for (let frame = 1; frame <= 10; frame++) {
        let player1FrameScore = player1Rolls[(frame - 1) * 2] + player1Rolls[(frame - 1) * 2 + 1];
        let player2FrameScore = player2Rolls[(frame - 1) * 2] + player2Rolls[(frame - 1) * 2 + 1];

        if (frame < 10) {
            
            if (player1Rolls[(frame - 1) * 2] === 10) {
                
                player1FrameScore += player1Rolls[frame * 2] + player1Rolls[frame * 2 + 1];
            } else if (player1FrameScore === 10) {
                
                player1FrameScore += player1Rolls[frame * 2];
            }

            
            if (player2Rolls[(frame - 1) * 2] === 10) {
                
                player2FrameScore += player2Rolls[frame * 2] + player2Rolls[frame * 2 + 1];
            } else if (player2FrameScore === 10) {
                
                player2FrameScore += player2Rolls[frame * 2];
            }
        }

        player1Score += player1FrameScore;
        player2Score += player2FrameScore;

        console.log(`Frame ${frame}: Player 1 score: ${player1FrameScore}, Player 2 score: ${player2FrameScore}`);
    }

    
    if (player1Rolls[18] + player1Rolls[19] >= 10) {
        let player1Roll3 = parseInt(prompt("Player 1 additional roll:"));
        player1Score += player1Roll3;
        console.log("Player 1 additional roll points: " + player1Roll3);
    }

    if (player2Rolls[18] + player2Rolls[19] >= 10) {
        let player2Roll3 = parseInt(prompt("Player 2 additional roll:"));
        player2Score += player2Roll3;
        console.log("Player 2 additional roll points: " + player2Roll3);
    }

    console.log(`Player 1 total score: ${player1Score}`);
    console.log(`Player 2 total score: ${player2Score}`);

    if (player1Score > player2Score) {
        console.log("Player 1 wins!");
    } else if (player2Score > player1Score) {
        console.log("Player 2 wins!");
    } else {
        console.log("It's a tie");
    }
}

Bowling();
