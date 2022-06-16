# RPS

This challenge provides us with a rock, paper, scissors game program to get our flag from. Thankfully we get the source code to look through.

## Solution

It look like we need to beat the computer 5 times to get the flag.

If we check the source code we find:

```
char* hands[3] = {"rock", "paper", "scissors"};
char* loses[3] = {"paper", "scissors", "rock"};
```

```
if (strstr(player_turn, loses[computer_turn])) {
    puts("You win! Play again?");
    return true;
  } else {
    puts("Seems like you didn't win this time. Play again?");
    return false;
  }
```

The important thing is that ```(strstr(player_turn, loses[computer_turn]))```

This is basically going to check if the given computers guess is found within the given players guess.

So we can exploit this by using a guess that contains all possible computer guesses such as ```rockpaperscissors```.

If we enter that for 5 rounds of the game we get out flag!

```
picoCTF{50M3_3X7R3M3_1UCK_B69E01B8}
```
