# ChessBot
##Best Move Prediction Using Elite Chess Games (2200+ elo)

I trained the model on a dataset of 50,000 training games, labeled using the players’ next moves. I let the model train for 16 epochs, as the test accuracy started to stagnate. The model was tested on a small set of 2,000 test games. Here are the results after 16 epochs of training:

##Model Architecture:
The model takes a 8 x 8 x 12 tensor as input. This is a stack of 12 8x8 chess boards, with each board having one of the six types of chess pieces, and one of the two players. 
This input layer is run through 5 convolutional layers and one dense layer.
Each of these intermediate layers are followed by a batch normalization layer and have a 20% chance to be nullified using a dropout function.
Finally, the model predicts one of 64x64 possible moves - a 2D tensor where the X axis is the board square with the piece to move and the Y axis is the board square where the piece is moved to. The model flattens this 2D tensor into a 4096x1 tensor and applies a softmax function. The entry with the largest value is the move that the model predicts to be the best.
The model was trained using categorical cross entropy.

##Why This Architecture?
This 8 x 8 x 12 input separates the pieces, allowing the model to learn different patterns for each piece type and player.
Convolutional layers are the best layer to use for recognizing spatial patterns and relationships. The positions of pieces on the chess board determine the game, so the model is built almost entirely on these layers.

Batch normalization stabilizes the gradients and the outputs of the convolutional layers. This generally prevents any drastic gradient updates, improves training time, and reduces overfitting.
Dropout is applied to every hidden layer, encouraging the model to learn deeper patterns and not rely on a single, shallow pattern.
The output is given as a large vector, where each entry is a value between 0 and 1. This vector is large enough to include all possible moves on the board.
Cross entropy loss is great for training models with a classification task because it pushes the model to minimize poor classifications and maximize the correct one.
