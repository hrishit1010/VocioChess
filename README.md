# VocioChess
# Pygame Chess with AI and Voice Controls

This program is a complete chess game built with Python and Pygame. It allows a user to play against a friend (hotseat) or a computer AI.

## Features

* **GUI:** A full graphical user interface powered by Pygame that displays the board and pieces.
* **Multiple Control Schemes:**
    * **Drag and Drop:** Click and drag pieces to their destination.
    * **Click-Click:** Click a piece to select it, then click the destination square.
    * **Voice Movement:** Use speech recognition to select a piece and its destination.
* **AI Opponent:** A challenging AI that uses a sophisticated search algorithm to find the best move.
* **Game Logic:** Implements all standard chess rules, including:
    * Castling
    * En Passant
    * Pawn Promotion (defaults to Queen)
    * Check, Checkmate, and Stalemate detection
    * Draw by 50-move rule and three-fold repetition.
* **Customizable Game:**
    * Play as White or Black against the AI.
    * Select AI difficulty level (Easy, Medium, Hard).
    * Enable or disable board flipping in 2-player mode.

## AI Engine Explained

The AI evaluates all possible moves up to a certain depth using a **Negamax search algorithm**. The board is given a numerical score: a high positive score favors White, and a low negative score favors Black. The AI assumes optimal play from both sides.

To manage the massive number of possible board positions, the AI uses several optimization techniques:

1.  **Alpha-Beta Pruning:** A search optimization that significantly reduces the number of nodes evaluated in the search tree. It "prunes" branches that are guaranteed to not lead to a better result than one already found.
2.  **Transposition Table:** A dictionary (hash map) that stores the evaluations of previously seen board positions. If the AI encounters the same position through a different sequence of moves, it retrieves the stored score instead of re-calculating it.
3.  **Opening Book:** A pre-computed dictionary of common opening positions and strong "book moves" for those positions. If the current board state is in the book, the AI plays a random move from the suggested list, skipping the search process entirely.

### Board Evaluation Function

The AI's decision-making is driven by its evaluation function, which scores the board based on several factors:

* **Material:** The primary factor. Each piece has a point value (e.g., Queen=9, Rook=5). The AI calculates the total material score for both sides.
* **Piece-Square Tables:** Each piece type (Pawn, Knight, King, etc.) has a table that assigns a score to every square on the board. This encourages the AI to place pieces on strong, central, or safe squares.
* **Pawn Structure:** The AI applies penalties for poor pawn structures, including:
    * **Doubled Pawns:** Pawns on the same file.
    * **Isolated Pawns:** Pawns with no friendly pawns on adjacent files.
    * **Blocked Pawns:** Pawns that cannot advance.
* **Checkmate:** A checkmate position is given an extremely high (or low) score to ensure the AI prioritizes it (or avoids it) above all else.

## Dependencies

* `pygame`: For the game library, GUI, and sound.
* `copy`: For deep copying game states.
* `pickle`: For saving and loading the opening book.
* `random`: For selecting moves from the opening book.
* `collections` (`defaultdict`, `Counter`): For data structures and efficient counting.
* `threading`: To allow the AI to "think" without freezing the GUI.
* `time`: For managing game timing.
* `speech_recognition`: For the voice control feature.
*
<img width="946" height="995" alt="image" src="https://github.com/user-attachments/assets/198ca743-e284-445b-a921-72a87fa9f8e2" />
<img width="961" height="1006" alt="image" src="https://github.com/user-attachments/assets/c1ef8313-8fe8-4d1a-a977-121a64b9f4d3" />
<img width="939" height="961" alt="image" src="https://github.com/user-attachments/assets/8e2a3f56-3c93-4004-8166-a2fa3e071a1a" />
<img width="937" height="993" alt="image" src="https://github.com/user-attachments/assets/9615d72c-95b6-4e0c-af82-b5455a33e4e1" />


