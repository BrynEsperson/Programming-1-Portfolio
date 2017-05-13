# Programming 1 Portfolio
## Nastassja Motro 2017
### With Bryn Esperson and Tessa Vu

## Our Game

We have decided to create a Chess Game using the Java Language.
This program is just supposed to replicate the design of a chess game like one you would find on an app on your phone or on the computer. It's not as fancy with as many special effects as some other games but it still has many cool features.

## Basic Rules

Chess is a two player game. One person controls one set of peices (black pieces) and the other player controls the opposite set of pieces (white pieces). Players cannot switch set of pieces midgame. The goal of the game is to get the other player's King into checkmate.

### Check, Checkmate, and Stalemate

* check - When the King of a player can be taken by a piece of the opponent, one says that the King is in check. It is not allowed to make a move, such that ones King is in check after the move.

* checkmate - When a player is in check, and he cannot make a move such that after the move, the King is not in check, then he is mated. The player that is mated loses teh game, and the player that mates him wins the game.

* stalemate - When a player cannot make any legal move, but he is not in check, then the player is said to be stalemated. In a case of a stalemate, the game is a draw.

## Starter
The game starts off with a main menu screen. We decided to create a theme based game. The theme is Marvel vs. DC with Marvel being the white designated set of pieces and DC being the black designated set of pieces. As soon as the game is opened, the starter menu will pop open.

Code:

```javascript
PImage startmenu;
PFont title;
PFont description;
int screenX, screenY, stage;

void setup() {
  size(1920, 1080);
  screenX = round(width);
  screenY = round(height);
  size(screenX, screenY);
  startmenu = loadImage("Versus.png");
  image(startmenu, 0, 0, screenX, screenY);
  title = createFont("Anurati-Regular", 80, true);
  description = createFont("Anurati-Regular", 30, true);
}

void draw() {
  textAlight(CENTER);
  textFont(title);
  text("CHESS: DC v. MARVEL", width/2, 400);
  textFont(description);
  text("PRESS ANY KEY TO START THE GAME", width/2, 450);
  }
``` 

### This is what the start menu would look like:

![alt text](https://nastassjamotro.github.io/Programming-1-Portfolio/Versus.png "Logo Title Text 1")

### When the actual playing screen loads it would look something like this:
  The first is an example of the mockup using the actual pictures of the character. But the game will actually utilize the logos of each of the charactes.
  

![alt text](https://nastassjamotro.github.io/Programming-1-Portfolio/figuresmockup.png "Logo Title Text 1")

  But the game will actually utilize the logos of each of the characters.
  
![alt text](https://nastassjamotro.github.io/Programming-1-Portfolio/logosmockup.png "Logo Title Text 1")

### The Characters on the DC side are:

* Martian Manhunter - as the king

* Wonder Woman - as the queen

* SuperGirl - as the bishop

* Batman - as the knight

* Superman - as the rook

* Flash - as the pawn

### The Characters on the Marvel side are:

* Captain America - as the king

* Captain Marvel - as the queen

* Black Widow - as the bishop

* Wolverine - as the knight

* Iron Man - as the rook

* Hawkeye - as the pawn

## Here are the rules for the pieces:

* King - The King moves only one square in any direction: horizontally, vertically, or diagonally. The King can do a special move called castling but it may only be done with the use of the rook. The King is the most important piece of the game, and moves must be made in such a way that the king is never in check. If in check, the king must move and not any other piece.

* Queen - The Queen has combined moves of the rook and bishop so i.e. it can move horizontally, diagonally, and vertically.

* Bishop - The Bishop moves diagonally and only on the color it starts off on. It may not jump over pieces.

* Knight - The Knight makes a move that consists of first one step in a horizontal or vertical direction, and then one step diagonally in an outward direction.

* Rook - The Rook moves in a straight line, wheter it's horizontal movement or vertical. It cannot move diagonally.

* Pawn - The Pawn moves differently regarding whether it moves to an empty square or wheter it takes a piece of the opponent. When a Pawn does not take, it moves one square forward. When the Pawn has not moved at all, i.e., the Pawn is still at the second row (from the owning player's view), the Pawn may make a double step straight forward. When taking, a pawn goes one square diagonally forward.

### Special Moves:

* Castling - Under certain, special rules, a King and Rook can move simultaniously in a castling move. The following conditions must be met:

1. The King that makes the castling move has not yet moved in the game.
2. The Rook that makes the castling move has not yet moved in the game.
 3. The King is not in check.
4. The King does not move over a square that is attacked by an enemy piece during the castling move, i.e., when castling, there may not be an enemy piece that can move (in case of Pawns: by diagonal movement) to a square that is moved over by the King.
5. The King does not move to a square that is attacked by an enemy piece during the castling move, i.e., you may not castle and end the move with the King in check.
6. All squares between the Rook and King before the castling move are empty.
7. The King and Rook must occupy the same rank (or row).
8. When castling, the King moves two squares towards the Rook, and the Rook moves over the King to the next square.

Code for King Piece with Castling Move:

```javascript
public class King extends Piece {
  public booelan moved;
  public boolean castle;
  public King(boolean available, int x, int y) {
    suepr(available, x, y);
    this.moved = false;
    this.castle = false;
  }
  
  @Override
  public boolean isValid(Board board, int fromX, int fromY, int toX, int toY) {
    if(super.isValid(board, fromX, fromY, toX, toY) == false) {
      return false;
    }
    if(Math.abs(toX - fromX) > 1 || Math.abs(toY - fromY) > 1) {
      if (moved) {
        return false;
      }
      return false;
    }
  }
}

if(fromY - toY == 2 && fromX == toX) {
  if(board[fromX][fromY + 1] != null || board{toX][toY + 2] != null) {
    castle = false;
    return false;
  }
} else if (fromY - toY == 3 && fromX == toX) {
  if(board[toX][fromY - 1] != null || board[toX][fromY - 2] != null || board[toX][fromY - 3] != null) {
    castle = false;
    return false;
  }
} else {
  castle = false;
  return false;
}
castle = true;
//moved = true;
return true;
```

You can use the [editor on GitHub](https://github.com/nastassjamotro/Programming-1-Portfolio/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/nastassjamotro/Programming-1-Portfolio/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
