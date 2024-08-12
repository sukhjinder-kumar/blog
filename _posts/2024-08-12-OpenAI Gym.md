---
title: OpenAI Gym
date: 2024-08-12 12:05:38 +05300
categories: [Programming, ReinforcementLearning]
tags: [programming, rl, openai_gym]     # TAG names should always be lowercase
description: In this post we will learn how to use OpenAI gym library
image:
  path: /assets/img/OpenAI_Gym/blog_image.png
  alt: LunarLander environment render (human mode)
---

## 1. Basic Usage

Reference: [Farama Gym](https://gymnasium.farama.org/content/basic_usage/)

Installation: `pip3 install gymnasium`, to install other environments `pip3 install "gymnasium[<env_name>]"` (where env_name can be 'all' or particular like 'box2d')

> **Note:** We will be using fork of OpenAI gym by Farama, as it is the one being mantained.
{: .prompt-info}

### 1.1 An Example

Below is a sample code to run the "CartPole-v1" environment.

```python
import gymnasium as gym

env = gym.make("CartPole-v1", render_mode="human")
observation, info = env.reset(seed=42)

for _ in range(100):
    action = env.action_space.sample()
    observation, reward, terminated, truncated, info = env.step(action)

    if terminated or truncated:
        observation, info = env.reset()

env.close()
```

> **Note:** Rendering window doesn't close after completion of code. Have to restart the kernel (ipynb) notebook
{: .prompt-info}

### 1.2 Explanation

- `gym.envs.registry.keys()`: returns list of environments available

- `env.make(<env_name>, render_mode="<visual_type>")`: Init environment and set render_mode for visual (select which "kind" of visual you want to see, options "human", "rgb_array", "ansi").

    > **Note:** Rendering window doesn't close after completion of code. Have to restart the kernel (ipynb) notebook. Maybe in future update of the library, this issue will be resolved.

- `env.reset()`: returns observation and info (something other than observation). Resets the environment. Can use seed to set initial state.

- `env.action_space`: returns list of actions (in form of class, inheritance of `Space` class) available in that state. `.sample()` picks randomly from it. 

- `env.observation_space`: returns list of observations (or states, in form of class, inheritance of `Space` class) available.

- `env.step(action)`: Takes the step using the action. Internally new state is arrived at, using logic of MDP. Returns observation (state or whatever is visible), reward, whether terminated (end reached) or truncated (if timestep reached, i.e. max iterations issued by user).

- `wrapped_env = wrapper(env)`, where wrappers are to be imported from `gymnasium.wrappers`. Like `FlatternObservation`, which modifies return shape (and type) of observations. Wrappes allows us to modify classes without messing with the internal code. Other wrappers are:
    
    ```py
    from gymnasium.wrappers import FlattenObservation
    print(FlattenObservation(env).observation_space.shape)
    ```

    - `TimeLimit`: Issues a truncated signal if number of iteration in one run > TimeLimit
    - `ClipAction`: Clip the action s.t it lies in action space.
    - ..etc

## 2. Advanced Usage

There are a few things that gym is able to do like creating custom environment with gym api, or creating vectorized environments ("run" environments in parallel for robust training), etc. We refer the reader, for detailed explanation and examples (/tutorials) for aforementioned, to the Farama website.
