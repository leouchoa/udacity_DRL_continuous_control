# udacity_DRL_continuous_control
Codes for the project Continuous Control submission.

## About the Project

The goal of the project is to train an agent to maintain a double-jointed arm at target locations for as many time steps as possible, as we can see from the animation bellow.

![Double-jointed arm moving at target locations.](reacher.gif)

To do that a reinforcement learning agent was trained. Specifically it was trained using a Deep Neural Network, with a technique called DDPG, similar as was presented in the original [DDPG](https://arxiv.org/pdf/1509.02971v6) paper.

## What is Reinforcement Learning

From [deepsense.ai](https://deepsense.ai/what-is-reinforcement-learning-the-complete-guide/), we have that 

> Reinforcement learning is the training of machine learning models to make a sequence of decisions. The agent learns to achieve a goal in an uncertain, potentially complex environment. In reinforcement learning, an artificial intelligence faces a game-like situation. The computer employs trial and error to come up with a solution to the problem. To get the machine to do what the programmer wants, the artificial intelligence gets either rewards or penalties for the actions it performs. Its goal is to maximize the total reward.
Although the designer sets the reward policy–that is, the rules of the game–he gives the model no hints or suggestions for how to solve the game. It’s up to the model to figure out how to perform the task to maximize the reward, starting from totally random trials and finishing with sophisticated tactics and superhuman skills. By leveraging the power of search and many trials, reinforcement learning is currently the most effective way to hint machine’s creativity. In contrast to human beings, artificial intelligence can gather experience from thousands of parallel gameplays if a reinforcement learning algorithm is run on a sufficiently powerful computer infrastructure.

## Task Goals and Details

The environment is a **Unity Machine Learning Agents (ML-Agents)**, which is an open-source Unity plugin that enables games and simulations to serve as environments for training intelligent agents. The observation space consists of 33 variables corresponding to position, rotation, velocity, and angular velocities of the arm. Each action is a vector with four numbers, corresponding to torque applicable to two joints. Every entry in the action vector should be a number between -1 and 1.

**How to complete the task**: A reward of +0.1 is provided for each step that the agent's hand is in the goal location. So in order to solve the environment, the agent must get an average score of +30 over 100 consecutive episodes. If the selected environment is the second, then the new score to be reached is now the average score of the 20 environment agents per time step.

## Environment Set Up

The project environment we're working on with is the [reacher](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Learning-Environment-Examples.md#reacher) environment. 

**Note:** The Unity ML-Agent team frequently releases updated versions of their environment. I'm are using the v0.4 interface. To avoid any confusion, please use the workspace provided here or work with v0.4 locally.

### Step 1 Clone the DRLND Repository

Clone the [DRLND Repository](https://github.com/udacity/deep-reinforcement-learning#dependencies) to set up your Python environment. These instructions can be found in README.md at the root of the repository. By following these instructions, you will install PyTorch, the ML-Agents toolkit, and a few more Python packages required to complete the project.

### Step 2: Download the Unity Environment

For this project, you will not need to install Unity - this is because we have already built the environment for you, and you can download it from one of the links below. You need only select the environment that matches your operating system:

For version one, select one of:

- Linux: click [here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Linux.zip)
- Mac OSX: click [here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher.app.zip)
- Windows (32-bit): click [here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Windows_x86.zip)
- Windows (64-bit): click [here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Windows_x86_64.zip)

For version two (multiple environments), select one of:

- Linux: click [here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Linux.zip)
- Mac OSX: click [here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher.app.zip)
- Windows (32-bit): click [here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86.zip)
- Windows (64-bit): click [here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86_64.zip)


Then, place the file in the `p2_continuous-control/` folder in the DRLND GitHub repository, and unzip (or decompress) the file.

(For Windows users) Check out [this link](https://support.microsoft.com/en-us/help/827218/how-to-determine-whether-a-computer-is-running-a-32-bit-version-or-64) if you need help with determining if your computer is running a 32-bit version or 64-bit version of the Windows operating system.

(For AWS) If you'd like to train the agent on AWS (and have not [enabled a virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md)), then please use [this link](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Linux_NoVis.zip) (version 1) or [this link](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Linux_NoVis.zip) (version 2) to obtain the "headless" version of the environment. You will not be able to watch the agent without enabling a virtual screen, but you will be able to train the agent. (*To watch the agent, you should follow the instructions to [enabled a virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md), and then download the environment for the Linux operating system above.*)

If you are interested in learning to build your own Unity environments after completing the project, you are encouraged to follow the instructions [here](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Getting-Started-with-Balance-Ball.md), which walk you through all of the details of building an environment from a Unity scene. 

## Instructions to Run the Code

After your environment is set up, to run the code and train the agent:

- Open up the `Reacher.ipynb` jupyter notebook.
- Run all the cells (note that the the gpu usage is enable if you have one configured)

Note that in the repository there are two other files, named `ddpg_agent_second_env.py` and  `model_second_env.py`. Those files are heavily inspired in the code provided by the udacity course (pendulum solution) and adapted to match the reacher environment specification needs (namely, action and state spaces).

