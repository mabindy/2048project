  
\# Pseudocode for Online 2048 Game: 2048 Royale

\# Global Variables  
friendsList \= empty list  
playerGrid \= empty grid  
playerCoins \= 0  
availableSkins \= empty list

\# Add Friend  
Define addFriend(username):  
    If username is not in friendsList:  
        Add username to friendsList

\# Invite Friend to Play  
Define inviteFriend(friendUsername):  
    If friendUsername is in friendsList:  
        Open mode selector  
        If mode selected:  
            Send invitation to friendUsername

\# Start Game  
Define startGame():  
    Initialize player and opponent grids  
    Set playerReadyStatus to false  
    Display play screen

\# Set Player Ready  
Define setPlayerReady():  
    Set playerReadyStatus to true  
    If all players are ready:  
        Start match

\# Start Match  
Define startMatch():  
    While game is not over:  
        Display player grids  
        Handle player turn  
        Check for match result

\# Handle Player Turn  
Define playerTurn():  
    Get direction input from player  
    Update grid based on direction  
    Display updated grid

\# Update Grid  
Define updateGrid(direction):  
    For each tile in the grid:  
        Move tile in specified direction  
        If tile can be combined with adjacent tile:  
            Combine tiles

\# Display Updated Grid  
Define displayUpdatedGrid():  
    Refresh screen to display updated grid state

\# End Game  
Define endGame():  
    Calculate match results  
    Reward player with coins based on placement  
    Display results

\# Open Store  
Define openStore():  
    Display store screen  
    Get available skins  
    Display available skins

\# Buy Skin  
Define buySkin(skin):  
    If playerCoins are greater than or equal to skin price and player confirms purchase:  
        Add skin to availableSkins  
        Deduct skin price from playerCoins

\# Display Friends List  
Define displayFriendsList():  
    For each friend in friendsList:  
        Display friend's details

\# Main Menu Navigation  
Define mainMenu():  
    Display main menu  
    Get user choice  
    If user chooses 'Friends':  
        Display friends page  
    Else if user chooses 'Play':  
        Display main page  
    Else if user chooses 'Store':  
        Display store page

\# Initialize Grids  
Define initializeGrids():  
    Set playerGrid to empty grid  
    Set opponentGrid to empty grid

\# Handle Coins Button Click  
Define handleCoinsButtonClick():  
    Open coin purchase menu with real currency

\# Handle Menu Button Click  
Define handleMenuButtonClick():  
    Display menu options (e.g., Settings, Login/Logout, Quit)  
    Get user choice  
    If user chooses 'Settings':  
        Open settings page  
    Else if user chooses 'Login/Logout':  
        Open Login/Logout menu  
    Else if user chooses 'Quit':  
        Confirm quit action and exit game if confirmed

\# Utility Functions  
Define sendInvitation(username):  
    Send invitation to join the game to username

Define moveTile(tile, direction):  
    Move specified tile in given direction

Define combineTiles(tile1, tile2):  
    Combine tile1 and tile2, and update grid

Define getPlayerInput():  
    Get direction input from player (left, right, up, down)  
    Return direction

Define gameIsNotOver():  
    Check if the game is over for player  
    Return true or false

Define refreshScreen():  
    Refresh screen to display updated game state

Define getAvailableSkins():  
    Get available skins from store  
    Return available skins

Define calculateResults():  
    Calculate match results

Define rewardPlayer():  
    Reward player with coins based on performance

Define displayResults():  
    Display match results and player rewards  
