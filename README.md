# PacmanAI
Built various Pacman agents for playing the game in different scenarios

- Part 1 includes the implementation of different search agents. Algorithms implemented for search agents are the following:

  BFS, DFS, DLS, IDS, Uniform Cost Search, A* Search

  Search agents only work for grabbing pellets and do not consider the presence of adversarial agents (ghosts)

  Usage example: python .\pacman.py -l mediumMaze -p SearchAgent -a fn=ids

  where -l specifies the map layout, -p specifies the agent class, and -a specifies the arguments for that agent class declaration (fn is an argument of SearchAgent, telling it what search algorithm to use)


- Part 2 includes the implementation of agents that take into account adversaries that try to harm the player. This includes implementation of the following:

  Reflex agent (not an adversarial search agent, doesn't look ahead), Minimax agent, Expectimax agent
  
  Adversarial search agents will work with any number of ghosts and can play the game normally. The evaluation function used for minimax and expectimax is:
    - Using Manhattan distance as heuristic function
    - Initialize evaluation function as current score + reciprocal of sum of manhattan distances of all pellets from player + # of spaces w/o pellets (eaten pellets)
    - There are two general cases: when the ghosts are hunting you and when they are scared. We take both cases into account and add these to our evaluation function
    - When ghosts behave normally, add to evaluation function -> current score + sum of all manhattan distances from all ghosts + # of power pellets left on map
    - When ghosts are in vulnerable state, add to evaluation function -> 
    current score + remaining time for ghost state for all ghosts - sum of all manhattan distances from all ghosts

  Usage example: python .\pacman.py -l mediumClassic -p ExpectimaxAgent -a evalFn=better

  evalFn=better is the evaluation function being described on top. If not specified, the default evaluation function will simply be the in-game score
    

- Part 3 includes the implementation of Q-learning agents, taking advantage of reinforcement learning in order to train the Pacman agent beforehand.
These agents try to learn what the best policy is for playing a map. Given any current state on the map, they will adopt their learned policy to take a specific action.
Agents implemented here are the basic Q-learning agent, and an approximate Q-learning agent

  Usage example: python pacman.py -l mediumClassic -p ApproximateQAgent -a extractor=SimpleExtractor -x 50 -n 60

  -x specifies the number of training runs, -n specifies the number of games to play

Credit to UC Berkeley for the basic template of this project: http://ai.berkeley.edu

Modified slightly by UCSB for the purposes of their AI class