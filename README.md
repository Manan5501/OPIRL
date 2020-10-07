# *OPOLO*: *O*ff-*Po*licy *L*earning from *O*bservations

Research code to accompany the paper: *Off-Policy Imitation Learning from Observations*.

#### Supported Algorithms: ####
- OPOLO (the proposed algorithm in the paper).
- Discriminator Actor Critic (DAC): [paper](https://arxiv.org/abs/1809.02925) and [official code](https://github.com/google-research/google-research/tree/master/dac).  
- Generative Adversarial Imitation Learning (GAIL): [paper](https://papers.nips.cc/paper/6391-generative-adversarial-imitation-learning.pdf) and [official code](https://github.com/openai/imitation).
- Behavior Cloning from Observations (BCO): [paper](https://www.ijcai.org/Proceedings/2018/0687.pdf) and [official code](https://github.com/jerrylin1121/BCO).
- Generative Adversarial Imitation from Observation (GAIfO): [paper](https://arxiv.org/pdf/1807.06158.pdf) and [code (from other repositories )](https://github.com/keiohta/tf2rl).
- DACfO (proposed as a baseline in the paper).

### Installation:
All code is built on the [stable-baseline framework](https://github.com/hill-a/stable-baselines). 
##### Prerequisites
- Python(>=3.5), Cmake, and OpenMPI. 
    - Please install prerequisite by following [this](https://github.com/hill-a/stable-baselines#prerequisites) guideline. 
- Mujoco:
    - Please follow [this](https://github.com/openai/mujoco-py) official instruction.
### Install using pip:
<pre><code>cd opolo
pip install -e .
</code></pre>
### Training *OPOLO*:
- Example: run OPOLO on the HalfCheetah-v2 task, using 4 expert trajectories, seed = 1:
<pre><code>cd opolo-code/opolo-baselines/run
python train_agent.py --env HalfCheetah-v2 --seed 1 --algo opolo  --task td3-opolo-idm-decay-reg --n-episodes 4 --log-dir <your-absolute-log-path>  --n-timesteps -1  
</code></pre>
- The <code>task</code> tag must contain strings of <code>idm</code>, <code>decay</code>, and <code>reg</code>:
    - <code>idm</code>: use inverse-action model.
    - <code>reg</code>: use forward KL-divergence as regularization. 
    - <code>decay</code>: reduce the effects of the regularization over time. 

### Training Other baselines:
- Run **DAC** on the Hopper-v2 task, using 4 expert trajectories, seed = 3:
<pre><code>cd opolo-code/opolo-baselines/run
python train_agent.py --env Hopper-v2 --seed 3 --algo td3dac --log-dir <your-absolute-log-path> --task td3-dac --n-timesteps -1  --n-episodes 4 
</code></pre>

- Run **DACfO** on the Walker2d-v2 task, using 10 expert trajectories, seed = 1:
<pre><code>cd opolo-code/opolo-baselines/run
python train_agent.py --env Walker2d-v2 --seed 1 --algo td3dacfo --log-dir <your-absolute-log-path> --task td3-dacfo --n-timesteps -1 --n-episodes 10
</code></pre>
#### Reminders:

- Expert Trajecotries can be found at:
<pre><code>opolo-code/opolo-baselines/expert_logs</code></pre>
- Hyper-parameter settings can be found at:
<pre><code>opolo-code/opolo-baselines/hyperparams/</code></pre>


#### TO DO:
- GAIL, GAIfO
- BCO
- evaluation 
- pretrain
- plot
