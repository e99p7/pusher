# Pusher

**Pusher Open AI Gymnasium (multi-articular robotic arm)**

The Pusher is a multi—jointed robotic arm very similar to a human arm. Her goal is to move the target cylinder (called the object) to a preset position using the robot's final organ (called the fingertip). The robot consists of shoulder, elbow, forearm and wrist joints.

The action represents the torques applied to the pivots.Box(-2, 2, (7,), float32)(a, b)

**The observation space consists of the following parts (in order):**

qpos (7 elements): Values of the position of the robot's body parts.

qvel (7 elements): The velocities of these individual body parts (their derivatives).

xpos (3 elements): The coordinates of the pusher's fingertip.

xpos (3 elements): Coordinates of the object being moved.

xpos (3 elements): Coordinates of the target's position.

The observation space is a space in which the following elements are present:Box(-Inf, Inf, (17,), float64)

The total reward is: reward = reward_dist + reward_ctrl + reward_near.

**Learn more https://gymnasium .farama.org/environments/mujoco/pusher/**

The SAC (Soft Actor-Critic) algorithm is ideally suited for such tasks — it works in continuous action spaces, copes well with multi-joint manipulators and finds a strategy faster than PPO. And vector environments (SubprocVecEnv or make_vec_env) allow you to collect experience from multiple copies of Pusher in parallel, which speeds up learning.

**What's going on here**

Vector environments (SubprocVecEnv) allow the agent to collect experience from 8 simulations at once in parallel. This gives an 8x speedup compared to a single environment.

SAC learns from experience with off-policy replay (1e6 step buffer).

In ~ 1 million steps, the agent usually learns how to push the cylinder in the direction of the target.

At the end, we record a video of the test episode and output it on a laptop.

---

**Pusher Open AI Gymnasium (многосуставная роботизированная рука)**

«Pusher» — это многосуставная роботизированная рука, очень похожая на человеческую. Её цель — переместить целевой цилиндр (называемый объектом ) в заданное положение с помощью конечного органа робота (называемого кончиком пальца ). 
Робот состоит из плечевого, локтевого, предплечьевого и лучезапястного суставов.

Действие представляет собой крутящие моменты, приложенные к шарнирным соединениям.Box(-2, 2, (7,), float32)(a, b)

**Пространство наблюдения состоит из следующих частей (по порядку):**

qpos (7 элементов): Значения положения частей тела робота.

qvel (7 элементов): Скорости этих отдельных частей тела (их производных).

xpos (3 элемента): Координаты кончика пальца толкателя.

xpos (3 элемента): Координаты перемещаемого объекта.

xpos (3 элемента): Координаты позиции цели.

Пространство наблюдения представляет собой пространство, в котором имеются следующие элементы:Box(-Inf, Inf, (17,), float64)

Общая награда составляет: reward = reward_dist + reward_ctrl + reward_near.

**Подробнее https://gymnasium.farama.org/environments/mujoco/pusher/**

Алгоритм SAC (Soft Actor-Critic) идеально подходит для таких задач — он работает в непрерывных пространствах действий, хорошо справляется с многосуставными манипуляторами и быстрее находит стратегию, чем PPO. 
А векторные среды (SubprocVecEnv или make_vec_env) позволяют параллельно собирать опыт из нескольких копий Pusher, что ускоряет обучение.

**Что здесь происходит**

Векторные среды (SubprocVecEnv) позволяют агенту собирать опыт сразу из 8 симуляций параллельно. Это даёт 8× ускорение по сравнению с одной средой.

SAC обучается на опыте с off-policy реплеем (буфер на 1e6 шагов).

За ~1 млн шагов агент обычно учится толкать цилиндр в направлении цели.

В конце мы записываем видео тестового эпизода и выводим в ноутбуке.
