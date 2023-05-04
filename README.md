Download Link: https://assignmentchef.com/product/solved-cs550-assignment-3
<br>



Part I

<ol>

 <li>Backgammon rolls are between 2 and 12. Find the probability for each pair of numbers.  That is without distinguishing between (5,6) and (6,5).</li>

 <li>Explain in your own words the role of chance nodes in stochastic minimax search and how they relate to classic minimax search.</li>

 <li>The CheckerBoard class in the programming assignment below cannot detect stalemates that occur when the board is in the same configuration three different times. How could one modify the class to detect this efficiently?  (No implementation is required, just well laid out plan that could be implemented by any skilled computer scientist.)</li>

</ol>




Part II:  Programming Assignment




You are to write a program that plays checkers.  The following are provided for you on Blackboard in a zip archive:

<ul>

 <li>py – Contains the checkerboard class that we have discussed in class.</li>

 <li>py – An abstract Strategy class that should be extended to implement your utility function. It contains the following methods:

  <ul>

   <li>Takes arguments player, game, and maxplies.  player is ‘r’ or ‘b’, game is a CheckerBoard class (not instance, used to access class methods), and maxplies is the tree depth to which the cutoff function should be applied.</li>

   <li>Takes a CheckerBoard and determines the strength related to player.  For example a strong red board should return a high score if the constructor was invoked with ‘r’, and a low score with ‘b’.  Note that this is not implemented in the abstract class.</li>

   <li>Takes a checkerboard and determines the best move with respect to alpha-beta search for the player associated with the class instance.  This must also implemented in the derived class.</li>

  </ul></li>

 <li>py – A concrete strategy class derived from AbstractStrategy that lets humans play. Uses the charIO module that is also provided.</li>

</ul>

There are also several other support classes in the zip file including rules for playing checkers.  Note that a discussion group has been created that will permit you to share compiled strategies with your classmates.




You are to implement class Strategy in the file ai.py.  Strategy is a concrete class derived from AbstractStrategy and should follow its interface.  You will need to design an alphabeta search and evaluation function.  The evaluation function is part of Strategy, but the alpha-beta search is a separate class that must be contained within ai.py.   Your alphabeta search should be a class with the following signature:




class <strong>AlphaBetaSearch</strong>:     <em>“””AlphaBetaSearch</em>

<em>    Conduct alpha beta searches from a given state.</em>

<em>    </em>

<em>    Example usage:</em>

<em>    # Given an instance of a class derived from AbstractStrategy, set up class</em>

<em>    # to determine next move, maximizing utility with respect to red player </em>

<em>    # and <u>minimiizing</u> with respect to black player.  Search 3 plies.</em> <em>    search = AlphaBetaSearch(strategy, ‘r’, ‘b’, 3)</em>

<em>    </em>

<em>    # To find the move, run the <u>alphabeta</u> method</em> <em>    best_move = search.alphabeta(some_checker_board)</em>

<em>    “””</em>           def <strong>__init__</strong>(<em>self</em>, strategy, maxplayer, minplayer, maxplies=3,                   verbose=False):

<em>“”””AlphaBetaSearch – Initialize a class capable of <u>alphabeta</u> search</em> <em>        strategy – implementation of AbstractStrategy class</em> <em>        <u>maxplayer</u> – name of player that will maximize the utility function</em> <em>        <u>minplayer</u> – name of player that will minimize the utility function</em> <em>        <u>maxplies</u>– Maximum ply depth to search</em> <em>        verbose – Output debugging information</em>

<em>        “””</em>                 def <strong>alphabeta</strong>(<em>self</em>, state):

<em>“””<u>alphbeta</u>(state) – Run an <u>alphabeta</u> search from the current          state.  Returns best action. </em>

<em>“”” </em>

<em> </em>

<em>    # define other helper methods as needed</em>




You will also need to implement a game playing function in <strong>checkers.py</strong> with the following signature:

def Game(red=human.Strategy, black=ai.Strategy, init=None,      maxplies=8, verbose=False)




The red and black variables should be instantiated to strategy classes (not instances of classes).  That is, to play as human red player and a computer black player with 5 turn lookahead (2*5 plies), you would call Game(red=Human.Strategy, black=ai.Strategy, maxplies=5).  The init argument allows one to pass in a specific checkerboard which is interesting for examining the strength of one’s board utility function without playing a full game.




Within Game, you can create instances of your strategy, e.g.:

redplayer = red(‘r’, checkerboard.CheckerBoard, maxplies)




and then take turns calling play on the different strategies with the evolving game board.




Hints:  This is a rather complicated program and it is easy to make mistakes.

<ul>

 <li>Design for testability and make sure that small components of your algorithm are working. For example, when testing alpha-beta search, work with shallow</li>

</ul>

searches from a board whose configuration you know and add statements that show  you what is happening when a verbose flag is set to True.  There are a number of predefined board configurations in boardlibrary.  See the unit tests in checkerboard.py for an example of accessing them. You are free to add to these.

<ul>

 <li>When designing a utility function, test it on board configurations. An example can be seen in boardlibary.boards[“StrategyTest1”] which sets up a board where you can see if your utility function is doing well.</li>

</ul>








