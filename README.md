# 1v1 JavaFX Chess
A personal project of mine: a 1v1 chess game, built with JavaFX.

Obviously there are many flaws with this code. I started working on the frontend (the JavaFX interface) and incorporated certain vital functions with it such as setting piece positions. Only after finishing did I realize that I needed a Tree to implement checks and checkmates. This led to many refactoring issues. Also, I faced many problems due to setting the coordinates of a piece as an Integer. My code would be a lot simpler if they were Strings.

To implement checks and checkmates, it required a tree in which a single Node of the tree has all the attributes of the Game object; most importantly, it contains a board of its own, pieces of its own, and the positions of the pieces on the board. A Node’s children Nodes are all the possible variations of the board after one movement. In other words, a Node represents a move. 

Each of these children Nodes will have their own children Nodes of possible moves. When a move is played, the Node that contains the scenario in which that move is played is assigned to the currentNode attribute in the Game class. The previous currentNode is discarded.

In order to implement checks and checkmates, the Node that the player is currently on must iterate through its children and find out which ones contain the scenario that one of the Kings is captured.

This further depends on whose turn it is. If it is white’s turn and one of the grandchildren (children of the children) Nodes contain the scenario that the white King is captured, then the move that allows for that scenario to happen will not be available for the white player.

File locations have to be changed. Castling, en passant and promotions have not been implemented. You may have to add in these VM arguments, replacing the file location with the location of your lib folder:

--module-path "C:\Users\mbrid\Downloads\openjfx-11.0.2_windows-x64_bin-sdk\javafx-sdk-11.0.2\lib" --add-modules=javafx.swing,javafx.graphics,javafx.fxml,javafx.media,javafx.web --add-reads javafx.graphics=ALL-UNNAMED --add-opens javafx.controls/com.sun.javafx.charts=ALL-UNNAMED --add-opens javafx.graphics/com.sun.javafx.iio=ALL-UNNAMED --add-opens javafx.graphics/com.sun.javafx.iio.common=ALL-UNNAMED --add-opens javafx.graphics/com.sun.javafx.css=ALL-UNNAMED --add-opens javafx.base/com.sun.javafx.runtime=ALL-UNNAMED
