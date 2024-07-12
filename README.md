# Multi-Agent Escape Room: Learning to Cooperate with Sparse Rewards

This project implements a challenging multi-agent reinforcement learning environment in Unity using ML-Agents. Two agents must collaborate to press two buttons simultaneously, replicating a cooperative "escape room" scenario. This environment facilitates experimentation with complex reward structures and learning paradigms.

**Environment Description**

The escape room environment consists of two agents and several key features:

*  **Limited Observability:**  Agents have partial observability; they can only sense their surroundings using forward-facing raycast sensors. These sensors detect walls, other agents, and the buttons. [!img src="./results/EscapeRoom.png" alt="Escape Room Environment"]

*  **Cooperative Reward Structure:**  The reward scheme incentivizes collaboration between the agents. Agents receive a positive reward for the first time they step on a button, and a larger reward when they escape by simultaneously pressing both buttons. Negative rewards are incurred for colliding with walls and for extended time spent in the environment. A visual representation of the reward structure can be found below.

[!img src="./results/EscapeRewards.png" alt="Escape Room Reward Structure"]

*  **MA-POCA for Credit Assignment:**  The project utilizes ML-Agents' implementation of Multi-Agent POsthumous Credit Assignment (MA-POCA) to address credit assignment challenges in dynamic multi-agent settings. This algorithm is particularly suitable because the number of agents may fluctuate during training (e.g., agent termination).

**Challenges and Future Work**

Initial experiments revealed that the agents struggled to learn the task effectively given the state space and reward configuration. This highlights the challenges associated with sparse rewards and limited communication between agents. To address these limitations, I implemented a modified reward system that provides the agents with a small, continuous reward while they remain on a button, encouraging them to stay there longer, giving the other agent time to navigate to the other button. Below is a sample of the agents training with this configuration. 

[!img src="./results/EscapeAgentsTraining.mp4" alt="Escape Room Agent Training"]

While the agents weren't able to learn to navigate to the goal locations in my initial tests, they did appear to understand the cooperation aspect of the challenge. Both agents moved towards each other often and tended to stay together. I plan to experiment further to improve on these results. Specifically, here are some potential areas for future exploration:

* **Enhanced State Representation:** Providing agents with their own positional information might improve their ability to form relationships between objects in the environment.

* **Recurrent Neural Networks (RNNs) for Memory:** Utilizing RNNs could provide the agents with a form of memory to store past actions, potentially mitigating the limitations imposed by sparse rewards. However, LSTMs, a common RNN module, may not be ideal for the continuous action space in this environment.

* **Discrete Action Space:** Transforming the environment into a discrete action space using a grid-based system could accelerate learning by reducing the size of the state and action space.

* **Rewarding Movement Towards Buttons:**  An additional reward for moving towards the buttons might incentivize collaboration, but this should be balanced with the time penalty to avoid confusion. 

* **Curriculum Learning:**  Breaking down the escape objective into smaller subtasks through curriculum learning could prove beneficial. This might involve starting with a smaller environment and gradually increasing the complexity.


By exploring these avenues, I aim to develop a more robust solution where the agents can effectively learn to cooperate and escape the environment.
