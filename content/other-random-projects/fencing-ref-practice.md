---
title: "Fencing Ref Practice"
date: 2023-03-18T21:45:33-0400
draft: true
showToc: false
---
## Very work in progress
## Click the button then speak/signal the actions
You can practice translating words to hand signals, hand signals to words coming soon&#8482;

{{<rawhtml>}}
<button id="regen" onclick="document.getElementById('words').textContent=generateSequence()" style="all: revert">
        New sequence
    </button>
    <div id="words">
        
    </div>

    <script>
    function side(row){
        if(row==0){
            return "none"
        } else if (row<0){
            return "left"
        } else {
            return "right"
        }
    }
    function oppside(row){
        if(row==0){
            return "none"
        } else if (row<0){
            return "right"
        } else {
            return "left"
        }
    }
    function generateSequence(){
        let num_actions = Math.floor(Math.random() * 3)
        let sequence = `engarde ready fence halt`
        let first_offensive_random = Math.floor(Math.random() * 7)
        let row = 0 // -1 is left, 0 is none, 1 is right
        if(first_offensive_random < 3){
            sequence += " attack-left"
            row = -1
        } else if (first_offensive_random < 6) {
            sequence += " attack-right"
            row = 1
        } else {
            sequence += " simul"
            return sequence
        }
        if(num_actions > 1){
            for(let i=0; i < num_actions-1; i++){
                let first_defensive_random = Math.floor(Math.random() * 2)
                if(first_defensive_random == 0){
                    // attack is parried
                    sequence += ` parried-${oppside(row)}`
                    row = -row
                    sequence += ` riposte-${side(row)}`
                } else {
                    // attack is no
                    sequence += ` no-${oppside(row)}`
                    row = -row
                
                    let second_offensive_random = Math.floor(Math.random() * 2)
                    if(second_offensive_random == 0){
                        // is counterattack
                        sequence += ` counter-${side(row)}`
                    } else {
                        // is remise by first fencer
                        row = -row
                        sequence += ` remise-${side(row)}`
                    }
                }

                let second_defensive_random = Math.floor(Math.random() * 2)
                if(second_defensive_random == 0){
                    // attack is parried
                    sequence += ` parried-${oppside(row)}`
                    row = -row
                    sequence += ` riposte-${side(row)}`
                } else {
                    // attack is no
                    sequence += ` no-${oppside(row)}`
                    row = -row

                    let second_offensive_random = Math.floor(Math.random() * 2)
                    if(second_offensive_random == 0){
                        // is counterattack
                        sequence += ` counter-${side(row)}`
                    } else {
                        // is remise by first fencer
                        row = -row
                        sequence += ` remise-${side(row)}`
                    }
                }
            }
        }
        // last one geranteed to be final
        let first_defensive_random = Math.floor(Math.random() * (num_actions > 0 ? 4 : 2))
        if(first_defensive_random == 0){
            // attack arrives
            sequence += ` arrives-${oppside(row)} point-${side(row)}`
            return sequence
        } else if(first_defensive_random == 1){
            // attack is off-target
            sequence += ` offtarget-${oppside(row)}`
            return sequence
        } else if(first_defensive_random == 2){
            // attack is parried
            sequence += ` parried-${oppside(row)}`
            row = -row
            sequence += ` riposte-${side(row)}`
        } else {
            // attack is no
            sequence += ` no-${oppside(row)}`
            row = -row
        
            let second_offensive_random = Math.floor(Math.random() * 2)
            if(second_offensive_random == 0){
                // is counterattack
                sequence += ` counter-${side(row)}`
            } else {
                // is remise by first fencer
                row = -row
                sequence += ` remise-${side(row)}`
            }
        }

        let second_defensive_random = Math.floor(Math.random() * 2)
        if(second_defensive_random == 0){
            // attack arrives
            sequence += ` arrives-${oppside(row)} point-${side(row)}`
            return sequence
        } else if(second_defensive_random == 1){
            // attack is off-target
            sequence += ` offtarget-${oppside(row)}`
            return sequence
        }
        return "AA SEQ FAILED"
    }
    </script>
{{</rawhtml>}}