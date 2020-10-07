# RL[1]——introduction to RL and value-based method

kay 2020.10.7 
<a name="Cpuzj"></a>
### 
<a name="az6uF"></a>
### [【第一讲视频地址】](https://www.bilibili.com/video/BV1Hz4y1Q7UQ)[【第一讲课件地址】](https://rlchina.org/lectures/lecture1.pdf)
<a name="0ORJp"></a>
# RL的介绍

   - RL是很多学科的交叉领域
   - RL是机器学习三大分支其中之一
      - RL与其他机器学习领域的区别
         - 没有supervisor signal，只有reward signal，通过试错的方式与环境交互并学习
         - 回馈信号有延迟delay，有时在游戏结束时才有一个结果
         - 处理的是与时间相关的数据（监督学习处理的是iid数据-独立同分布independent and identically distributed）
         - agent的动作会影响收到的数据
   - High level的RL
      - 给定一个state，agent决定作出一个动作，动作作用在环境上，环境会发出一个reward，并转移到下一个状态
      - 目标：最大化累积奖励回报maximiza the cumulative reward
      - 原因：所有的目标都可以描述为期望累积回报的最大化（所有事务都会有一个目标）
   - RL包含的模块
      - policy：行为函数，根据状态s来输出动作a
      - value function：衡量一个state/action的好坏
      - model：环境模型（已知或未知）
   - RL算法的分类
      - Value based：只学习value function
         - no policy & value function
      - Policy based：直接学习从state到action的方程
         - policy & no value function
      - Actor critic：既学习value function也学习从s到a的方程
         - Policy & value function
      - Model free ：学习环境的模型并同时学习policy或value function
         - Policy and /or value function & no model
      - Model based：不学习环境的模型并同时学习policy或value function
         - Policy and/or value function & model
<a name="a2r0G"></a>
# MDP（Markov Decision Processes）

   - 作用：描述了RL的学习环境，环境是全观察的问题均被定义为MDP
   - 基本上所有的RL问题都可描述为MDP
      - 最优控制
      - 部分可观测问题
      - 多臂老虎机（设想,一个赌徒面前有N个老虎机,事先他不知道每台老虎机的真实盈利情况,他如何根据每次玩老虎机的结果来选择下次拉哪台或者是否停止赌博,来最大化自己的从头到尾的收益.）
   - MDP中的所有状态都具有马尔可夫的性质
      - P[S<sub>t+1</sub>|S<sub>t</sub>]=P[S<sub>t+1</sub>|S<sub>1</sub>,S<sub>2</sub>,...,S<sub>t+1</sub>]
      - 当前的状态包含了用于决策未来的所有统计量
   - MDP是一个五元组<S,A,F,R,&lambda;>
