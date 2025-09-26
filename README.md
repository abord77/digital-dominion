# Digital Dominion - The Strategy Game

Digital Dominion is a two-player strategy game where players assume the roles of computer hackers, controlling a set of links which are either viruses or data. The objective is to either download four pieces of data or make the opponent download four viruses.

## Table of Contents

- [Technical Details](#technical-details)
- [Installation](#installation)
- [Gameplay](#gameplay)
- [Features](#features)
- [Screenshots](#screenshots)
- [How to Play](#how-to-play)
- [Commands](#commands)
- [Command Line Arguments](#command-line-arguments)
- [License](#license)

## Technical Details

### Programming Language and Libraries

- **C++**: The game is primarily developed in C++, leveraging its object-oriented capabilities for structured and efficient game design.
- **Graphics Library**: For the graphical interface, X11 is used, providing a robust platform for rendering the game elements and managing user interactions.

### Design Patterns and Architecture

- **Observer Pattern**: Used for updating the graphical and text-based displays in response to changes in the game state.
- **Factory Method**: This pattern is utilized for creating different types of links (viruses and data) and abilities, allowing for easy extension and management.
- **Model-View-Controller (MVC)**: MVC architecture separates the game logic (model) from the user interface (view), controlled by the game controller.

### Game Mechanics Implementation

- **Board Management**: The game board is represented as a 2D grid, managing the placement and movement of links.
- **Turn-Based System**: We implemented a turn-based mechanism where each player has a set of actions they can perform per turn, including moving links and using abilities.
- **Ability System**: Abilities are modular and can be easily extended. Each ability class inherits from a common base, defining specific effects on the game state.

### Graphical User Interface

- **Beautifully Crafted Game Assets**: Our front-end was custom built and wireframed in **Photoshop** before being implemented.

## Installation

To install the game, follow these steps:

```bash
git https://github.com/abord77/digital-dominion.git
cd DigitalDominion
# Follow platform-specific instructions to compile and run the game
```

## Gameplay

Digital Dominion is played on an 8x8 board, with each player starting with 8 links - a mix of viruses and data. Players take turns to move their links and use special abilities, aiming to either download data or make their opponent download viruses. The game ends when a player achieves one of these objectives.

## Features

- **Turn-Based Strategy**: Engage in a strategic battle of wits with turn-based gameplay.
- **Graphical & Text-Based UI**: Play the game with a sleek graphical interface or a classic text-based view.
- **Multiple Abilities**: Utilize various abilities like Firewall, Download, and Polarize to gain an edge.
- **Extensible Design**: Easily add new abilities and features to the game.

## How to Play

Digital Dominion is a strategy game that involves careful planning, strategic movement, and the use of special abilities. The game is played on an 8x8 grid, resembling a chessboard, with two players each controlling eight links. Here's a detailed guide on how to play the game:

### Setup

1. **Board Setup**: The game board is an 8x8 grid with the middle two squares on the first and last row designated as server ports.
2. **Choosing Links**: Each player starts with 8 links - a mix of viruses and data, each having a strength between 1 and 4. Arrange your links on the first and last row of the board, avoiding placing them on the server ports.
3. **Selecting Abilities**: Each player chooses five abilities from options like Link Boost, Firewall, Download, Scan, Polarize, Wall, and Backup. These abilities can be used strategically during the game.

### Game Turn

The game proceeds in turns, with each player taking one turn at a time.

1. **Move a Link**: On your turn, move one of your links one space in a cardinal direction (north, south, east, or west). You cannot move a link onto one of your own links or server ports. Moving a link will end your turn.
2. **Battle**: If you move your link onto a space occupied by an opponent's link, a battle ensues. The link with the higher strength wins, and the loser's link is downloaded by the winner. In a tie, the attacking player wins.
3. **Download**: Moving a link off the opponent's side of the board or into their server ports results in downloading that link.
4. **Use an Ability**: You may use one of your abilities per turn, before moving a link. Abilities can change the game state significantly, like revealing link types or changing a link's allegiance.

### Abilities Explained

Each ability adds a unique strategic element to the game. Here’s a breakdown:

#### Link Boost

- **Effect**: Enhances a link's mobility for one turn.
- **Usage**: Activate before moving a link.
- **Strategic Tip**: Ideal for quick positioning.

#### Firewall

- **Effect**: Targets a square to reveal and potentially download opponent viruses.
- **Usage**: Place strategically on the board.
- **Strategic Tip**: Use to guard key areas.

#### Download

- **Effect**: Instantly downloads an opponent’s link.
- **Usage**: Select an opponent's link.
- **Strategic Tip**: Target high-strength data links.

#### Polarize

- **Effect**: Changes a link's type (data to virus or vice versa).
- **Usage**: Activate on a revealed link.
- **Strategic Tip**: Useful for deception or conversion.

#### Scan

- **Effect**: Reveals the type and strength of a link.
- **Usage**: Target an unrevealed link.
- **Strategic Tip**: Gain intelligence for strategy.

#### Wall

- **Effect**: Creates an impassable square.
- **Usage**: Activate to block paths or protect positions.
- **Strategic Tip**: Funnel opponent movements or create safe zones.

#### Backup

- **Effect**: Reverses a link's last move.
- **Usage**: Activate after a link moves.
- **Strategic Tip**: Correct mistakes or tactically retreat.

#### MoveTwice

- **Effect**: Allows two link moves to be made.
- **Usage**: Activate at the start of the your turn before moving a link.
- **Strategic Tip**: Make big moves, bigger compounded with link boost.

### Winning the Game

The game ends when either:

- A player successfully downloads four data links, winning the game.
- A player is forced to download four virus links, resulting in their loss.

### Strategic Elements

- **Link Types**: Keep in mind the types of links (virus or data) you're moving. Misleading your opponent can be a key strategy.
- **Abilities**: Use abilities wisely. They are limited and can turn the tide of the game.
- **Positioning**: Be strategic about the positioning of your links, especially when it comes to protecting your server ports and planning attacks.

## Commands

Players can interact with the game using the following command line commands:

- `move <link> <direction>`: Moves the specified link in the given direction (`up`, `down`, `left`, `right`).
- `abilities`: Displays the ability cards available to the player.
- `ability <N>`: Uses the ability card with ID N. May require additional information like a target or a board square.
- `board`: Displays the current state of the board.
- `sequence <file>`: Executes a sequence of commands from a specified file.
- `quit`: Exits the game.

## Command Line Arguments

When launching Digital Dominion, you can customize your game setup using various command line arguments. Here’s a guide to using these options:

- **`-ability1 <order>`**: Specifies the abilities for player 1. This is a list of the 5 abilities player 1 will use, given by a string consisting of the first letter of each ability. For example, `-ability1 LFDSP` for Link boost, Firewall, Download, Scan, Polarize in that order.

- **`-ability2 <order>`**: Similar to `-ability1`, but for player 2.

- **`-link1 <placement-file>`**: Specifies the placement of links for player 1. The contents of `<placement-file>` should list what each link should be for player 1, in order from `a` to `h`. For example, a file containing `V1 D4 V3 V2 D3 V4 D2 D1` sets up the links in the specified order.

- **`-link2 <placement-file>`**: As above, but for player 2.

- **`-graphics`**: Enables the graphical interface for the game. If this option is not specified, the game defaults to a text-based interface.
- **`-extraGraphics`**: Enables more graphical features.

Example usage:

```bash
./digitaldominion -ability1 LFDSP -ability2 DSPLF -link1 player1.txt -link2 player2.txt -graphics
```

This command launches the game with specified abilities and link placements for both players and enables the graphical interface.
