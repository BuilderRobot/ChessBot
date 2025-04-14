In order to train the bot, you must download a dataset of chess games in FEN notation. I recommend the following dataset of high elo games:
[Lichess Elite Database](https://lichess.org/team/lichess-elite-database)

You can then label the dataset in two different ways:
- Using the current player's next move, copied from the current game in the dataset
- Using the Stockfish engine to make a prediction ([Stockfish Download](https://stockfishchess.org/))

You can train, save, and load the model using the marked functions

You can run game simulations against a random move bot 

You can connect your trained bot to the Lichess website by [creating a bot account](https://lichess.org/forum/lichess-feedback/how-to-make-a-bot-account?page=2) and running the setup functions

Have fun!
