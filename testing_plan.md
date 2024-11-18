# 2048 Royale Game Test Plan

## Part 1: Unit Testing the Game Mechanics

### Description:
Unit testing ensures that individual components of the game, such as player actions and tile mechanics, are functioning correctly. These tests verify the smallest units of the game in isolation to validate their accuracy.

### Action:
- **Basic Mechanics**: Verify if tiles move as expected.
  - Test if pressing the up arrow key moves all tiles upward and correctly merges identical tiles.
  - Ensure tiles that have been moved or merged update their position accordingly.
- **Movement Restrictions**:
  - Ensure that tiles do not move beyond the grid boundary.
  - Verify that tiles do not merge more than once per move.

### Unit Test Examples:
- **Test Case**: Pressing the left arrow key moves tiles left.
  - **Test Data**: Grid contains 2 tiles, each with the value `2`.
  - **Expected Outcome**: Tiles combine into a single tile of value `4` and move to the farthest left position.

- **Test Case**: No movement available for selected key press.
  - **Test Data**: Tiles positioned at boundaries.
  - **Expected Outcome**: Grid remains unchanged.


## Part 2: Logic Testing the Game Rules and Calculations

### Description:
Logic testing verifies the game’s rules and calculations, including score updates and merging mechanics, to ensure that game elements function correctly in tandem.

### Action:
- **Score Calculation**:
  - Verify if the score increases correctly when tiles merge.
- **Tile Merging**:
  - Ensure merging two tiles results in a new tile with the combined value.
- **Winning Condition**:
  - Verify that the game ends when a player reaches the `2048` tile before their opponent.
- **Random Events**:
  - Verify that random events trigger correctly and affect gameplay as intended.

### Logic Test Examples:
- **Test Case**: Merging tiles of equal value.
  - **Test Data**: Merge two tiles with values `16` each.
  - **Expected Outcome**: The new tile is valued at `32`, and the score increases by `32` points.

- **Test Case**: Multiple merges in one move.
  - **Test Data**: Four tiles with values `4`, `4`, `8`, and `8`.
  - **Expected Outcome**: After moving left, resulting tiles are `8` and `16`, and score is updated accordingly.

- **Test Case**: Player reaches the `2048` tile.
  - **Test Data**: Player merges tiles until a `2048` tile is created.
  - **Expected Outcome**: Player wins the game, and the opponent(s) is/are notified of their loss.

- **Test Case**: Random event triggers.
  - **Test Data**: Random event "All player boards swapped" occurs during gameplay.
  - **Expected Outcome**: All player boards are swapped, and gameplay continues with the new board state.


## Part 3: Boundary Testing: Edge Cases and Limits

### Description:
Boundary testing checks how the game handles extreme situations, such as maximum and minimum tile values and reaching the grid limits.

### Action:
- **Max Tile Value**:
  - Verify the behavior when reaching the maximum tile value possible.
- **Full Grid**:
  - Ensure that the game ends properly when no moves are possible.
- **Opponent Interaction**:
  - Verify that the opponent is notified when a player reaches the `2048` tile.
- **Random Events**:
  - Verify that random events handle edge cases, such as all blocks being halved when the minimum value is `2`.

### Boundary Test Examples:
- **Test Case**: Reaching the maximum tile value.
  - **Test Data**: Continue merging until a tile of value `2048` is reached.
  - **Expected Outcome**: Player receives a "Victory" message and is awarded with coins. Opponent is notified of their loss.

- **Test Case**: Full grid with no available moves.
  - **Test Data**: The grid is fully populated with tiles of different values.
  - **Expected Outcome**: Game ends and "You lose!" message is displayed.

- **Test Case**: Random event "All block values halved".
  - **Test Data**: Grid contains tiles of value `2`.
  - **Expected Outcome**: All tile values remain at `2` (cannot be halved further), and gameplay continues.


## Part 4: Integration Testing: System Interaction

### Description:
Integration testing ensures that different parts of the game (e.g., user interface, scoring system, tile movement) work seamlessly together.

### Action:
- **Gameplay and Scoring**:
  - Verify if the block values update correctly after every move.
- **Movement and UI Interaction**:
  - Ensure the movement is reflected visually in the game grid.
- **Player vs Opponent**:
  - Ensure that the game correctly tracks both players' progress and declares the winner appropriately.
- **Random Events**:
  - Verify that random events affect both players' boards and interactions consistently.

### Integration Test Examples:
- **Test Case**: Merging tiles.
  - **Test Data**: User moves a tile to merge two tiles of value `64`.
  - **Expected Outcome**: Merged tile of value `128` is displayed.

- **Test Case**: Undo functionality.
  - **Test Data**: User performs a move and then undoes it.
  - **Expected Outcome**: Grid returns to the previous state before the move.

- **Test Case**: Player wins against opponent.
  - **Test Data**: Player reaches the `2048` tile before the opponent.
  - **Expected Outcome**: Player is declared the winner, and the opponent is notified of their loss.

- **Test Case**: Random event "Temporary inverted controls".
  - **Test Data**: Random event triggers inverted controls for both players.
  - **Expected Outcome**: Controls are inverted for a limited time, and players must adapt to continue playing.


## Part 5: Handling Bad Input and Run-Time Errors

### Description:
Testing for bad input and run-time errors helps ensure that the game can handle unexpected actions without crashing.

### Action:
- **Invalid User Input**:
  - Verify that invalid key presses are ignored.
- **Error Handling**:
  - Ensure that the game state remains consistent in case of unexpected errors.
- **Opponent Disconnection**:
  - Verify that the game handles opponent disconnection gracefully.
- **Random Event Errors**:
  - Ensure that random events do not cause unexpected errors or crashes.

### Bad Input Test Examples:
- **Test Case**: Pressing an unsupported key (e.g., `X`).
  - **Test Data**: Press the `X` key.
  - **Expected Outcome**: No change to the game grid.

- **Test Case**: Saving during an error.
  - **Test Data**: Attempt to save the game while tiles are still moving.
  - **Expected Outcome**: The game displays a "Save failed" message and remains stable.

- **Test Case**: Opponent disconnects during the game.
  - **Test Data**: Opponent disconnects while the player is making a move.
  - **Expected Outcome**: Player is notified, and the game ends.

- **Test Case**: Random event triggers during critical action.
  - **Test Data**: Random event triggers while a player is merging tiles.
  - **Expected Outcome**: Random event is executed after the current action is completed, ensuring stability.


## Part 6: Test Plan Summary Table

| Test Case                   | Test Data                                | Expected Outcome                                                                                     |
|----------------------------|-----------------------------------------|------------------------------------------------------------------------------------------------------|
| Moving Tiles Left          | Grid with two `2` tiles                 | Tiles merge into a single tile of value `4` on the leftmost side of the grid.                        |
| Merging Equal Value Tiles  | Two `16` tiles                          | Tiles merge into one `32` tile                                     |
| Reaching Max Tile Value    | Merging until value `2048` is reached   | Player is notified of "Victory", opponent is notified of their loss.                                 |
| Full Grid, No Moves        | Fully populated grid                    | Game ends with a "Game Over" message.                                                                |
| Invalid Key Press          | Pressing `X`                            | No effect on game grid.                                                                     |
| Saving During Movement     | Attempt to save while tiles move        | "Save failed" message displayed, game remains stable without crashing.                               |
| Undo Last Move             | Perform move, then undo                 | Grid reverts to the state before the move.                                                           |
| Multiple Merges in One Move| Four tiles: `4`, `4`, `8`, `8`          | Tiles merge into `8` and `16`.                                           |
| Player vs Opponent Win     | Player reaches `2048` tile first        | Player wins, opponent is notified of their loss.                                                     |
| Opponent Disconnects       | Opponent disconnects mid-game           | Player is notified, and game ends.                                                                   |
| Random Event: Board Swap   | Random event triggers                   | All player boards are swapped, and gameplay continues with new board states.                         |
| Random Event: Halve Blocks | Random event triggers                   | All block values are halved, and gameplay continues.                                                 |
| Random Event: Inverted Controls | Random event triggers             | Controls are inverted temporarily, players must adapt to continue playing.                           |
