# cs285-assignment2-solved
**TO GET THIS SOLUTION VISIT:** [CS285 Assignment2-Solved](https://mantutor.com/product/cs285-assignment2-solved/)


---

**For Custom/Order Solutions:** **Email:** mantutorcodes@gmail.com  

*We deliver quick, professional, and affordable assignment help.*

---

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;57035&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;1&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (1 vote)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;CS285 Assignment2-Solved&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">

<div class="kksr-stars">

<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>

<div class="kksr-stars-active" style="width: 138px;">
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>


<div class="kksr-legend" style="font-size: 19.2px;">
            5/5 - (1 vote)    </div>
    </div>
<h1>1 Introduction</h1>
The goal of this assignment is to experiment with policy gradient and its variants, including variance reduction tricks such as implementing reward-to-go and neural network baselines. The startercode can be found at

<a href="https://github.com/berkeleydeeprlcourse/homework_fall2020/tree/master/hw2">https://github.com/berkeleydeeprlcourse/homework_fall2020/tree/master/hw2</a>

<h1>2&nbsp; Review</h1>
<h2>2.1&nbsp; Policy gradient</h2>
Recall that the reinforcement learning objective is to learn a <em>θ</em><sup>∗ </sup>that maximizes the objective function:

<em>J</em>(<em>θ</em>) = E<em>τ</em><sub>∼<em>π</em></sub><em><sub>θ</sub></em>(<em><sub>τ</sub></em><sub>) </sub>[<em>r</em>(<em>τ</em>)]&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; (1)

where each rollout <em>τ </em>is of length <em>T</em>, as follows:

<em>T</em>−1

<em>π<sub>θ</sub></em>(<em>τ</em>) = <em>p</em>(<em>s</em><sub>0</sub><em>,a</em><sub>0</sub><em>,…,s<sub>T</sub></em>−<sub>1</sub><em>,a<sub>T</sub></em>−<sub>1</sub>) = <em>p</em>(<em>s</em><sub>0</sub>)<em>π<sub>θ</sub></em>(<em>a</em><sub>0</sub>|<em>s</em><sub>0</sub>) <sup>Y </sup><em>p</em>(<em>s<sub>t</sub></em>|<em>s<sub>t</sub></em>−<sub>1</sub><em>,a<sub>t</sub></em>−<sub>1</sub>)<em>π<sub>θ</sub></em>(<em>a<sub>t</sub></em>|<em>s<sub>t</sub></em>)

<em>t</em>=1

and

<em>T</em>−1

<em>r</em>(<em>τ</em>) = <em>r</em>(<em>s</em><sub>0</sub><em>,a</em><sub>0</sub><em>,…,s<sub>T</sub></em>−<sub>1</sub><em>,a<sub>T</sub></em>−<sub>1</sub>) = <sup>X </sup><em>r</em>(<em>s<sub>t</sub>,a<sub>t</sub></em>)<em>.</em>

<em>t</em>=0

The policy gradient approach is to directly take the gradient of this objective:

Z

∇<em><sub>θ</sub>J</em>(<em>θ</em>) = ∇<em><sub>θ&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </sub>π<sub>θ</sub></em>(<em>τ</em>)<em>r</em>(<em>τ</em>)<em>dτ&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </em>(2)

Z

=&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <em>π<sub>θ</sub></em>(<em>τ</em>)∇<em><sub>θ </sub></em>log<em>π<sub>θ</sub></em>(<em>τ</em>)<em>r</em>(<em>τ</em>)<em>dτ.&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </em>(3)

= E<em>τ</em><sub>∼<em>π</em></sub><em><sub>θ</sub></em>(<em><sub>τ</sub></em><sub>) </sub>[∇<em><sub>θ </sub></em>log<em>π<sub>θ</sub></em>(<em>τ</em>)<em>r</em>(<em>τ</em>)]&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; (4)

(5) In practice, the expectation over trajectories <em>τ </em>can be approximated from a batch of <em>N </em>sampled trajectories:

)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; (6)

<em>&nbsp;.&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </em>(7)

Here we see that the policy <em>π<sub>θ </sub></em>is a probability distribution over the action space, conditioned on the state. In the agent-environment loop, the agent samples an action <em>a<sub>t </sub></em>from <em>π<sub>θ</sub></em>(·|<em>s<sub>t</sub></em>) and the environment responds with a reward <em>r</em>(<em>s<sub>t</sub>,a<sub>t</sub></em>).

<h2>2.2&nbsp; Variance Reduction</h2>
<strong>2.2.1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Reward-to-go</strong>

One way to reduce the variance of the policy gradient is to exploit causality: the notion that the policy cannot affect rewards in the past. This yields the following modified objective, where the sum of rewards here does not include the rewards achieved prior to the time step at which the policy is being queried. This sum of rewards is a sample estimate of the <em>Q </em>function, and is referred to as the “reward-to-go.”

<em>.&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </em>(8)

<strong>2.2.2&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Discounting</strong>

Multiplying a discount factor <em>γ </em>to the rewards can be interpreted as encouraging the agent to focus more on the rewards that are closer in time, and less on the rewards that are further in the future. This can also be thought of as a means for reducing variance (because there is more variance possible when considering futures that are further into the future). We saw in lecture that the discount factor can be incorporated in two ways, as shown below.

The first way applies the discount on the rewards from full trajectory:

!

(9)

and the second way applies the discount on the “reward-to-go:”

<em>&nbsp;.&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </em>(10)

.

<strong>2.2.3&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Baseline</strong>

Another variance reduction method is to subtract a baseline (that is a constant with respect to <em>τ</em>) from the sum of rewards:

∇<em><sub>θ</sub>J</em>(<em>θ</em>) = ∇<em><sub>θ</sub></em>E<em>τ</em><sub>∼<em>π</em></sub><em><sub>θ</sub></em>(<em><sub>τ</sub></em><sub>) </sub>[<em>r</em>(<em>τ</em>) − <em>b</em>]<em>.&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </em>(11)

This leaves the policy gradient unbiased because

∇<em><sub>θ</sub></em>E<em>τ</em><sub>∼<em>π</em></sub><em><sub>θ</sub></em>(<em><sub>τ</sub></em><sub>) </sub>[<em>b</em>] = E<em>τ</em><sub>∼<em>π</em></sub><em><sub>θ</sub></em>(<em><sub>τ</sub></em><sub>) </sub>[∇<em><sub>θ </sub></em>log<em>π<sub>θ</sub></em>(<em>τ</em>) · <em>b</em>] = 0<em>.</em>

In this assignment, we will implement a value function <em>V<sub>φ</sub><sup>π </sup></em>which acts as a <em>state-dependent </em>baseline. This value function will be trained to approximate the sum of future rewards starting from a particular state:

<em>T</em>−1

<table width="634">
<tbody>
<tr>
<td width="445"><em>V<sub>φ</sub><sup>π</sup></em>(<em>s<sub>t</sub></em>) ≈ <sup>X</sup>E<em>π<sub>θ </sub></em>[<em>r</em>(<em>s<sub>t</sub></em>0<em>,a<sub>t</sub></em>0)|<em>s<sub>t</sub></em>]<em>,</em>

<em>t</em><sup>0</sup>=<em>t</em>

so the approximate policy gradient now looks like this:
</td>
<td width="189">(12)</td>
</tr>
</tbody>
</table>
<em>&nbsp;.&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </em>(13)

<h1>3&nbsp; &nbsp;Overview of Implementation</h1>
<h2>3.1&nbsp; Files</h2>
To implement policy gradients, we will be building up the code that we started in homework 1. All files needed to run your code are in the hw2 folder, but there will be some blanks you will fill with your solutions from homework 1. These locations are marked with # TODO: get this from hw1 and are found in the following files:

<ul>
<li>infrastructure/rl trainer.py</li>
<li>infrastructure/utils.py</li>
<li>policies/MLP policy.py</li>
</ul>
After bringing in the required components from the previous homework, you can begin work on the new policy gradient code. These placeholders are marked with TODO, located in the following files:

<ul>
<li>agents/pg agent.py</li>
<li>policies/MLP policy.py</li>
</ul>
The script to run the experiments is found in scripts/run hw2.py (for the local option) or scripts/run hw2.ipynb (for the Colab option).

<h2>3.2 Overview</h2>
As in the previous homework, the main training loop is implemented in infrastructure/rl trainer.py.

The policy gradient algorithm uses the following 3 steps:

<ol>
<li><strong>Sample trajectories </strong>by generating rollouts under your current policy.</li>
<li><strong>Estimate returns and compute advantages</strong>. This is executed in the train function of <strong>pg agent.py</strong></li>
<li><strong>Train/Update parameters</strong>. The computational graph for the policy and the baseline, as well as the update functions, are implemented in policies/MLP policy.py.</li>
</ol>
<h1>4 Implementing Policy Gradients</h1>
You will be implementing two different return estimators within pg agent.py. The first (“Case 1” within calculate q vals) uses the discounted cumulative return of the full trajectory and corresponds to the “vanilla” form of the policy gradient (Equation 9):

<em>T</em>−1

0

<table width="634">
<tbody>
<tr>
<td width="478"><em>r</em>(<em>τ<sub>i</sub></em>) = <sup>X </sup><em>γ<sup>t </sup>r</em>(<em>s<sub>it</sub></em>0<em>,a<sub>it</sub></em>0)<em>.</em>

<em>t</em><sup>0</sup>=0

The second (“Case 2”) uses the “reward-to-go” formulation from Equation 10:
</td>
<td width="155">(14)</td>
</tr>
<tr>
<td width="478"><em>T</em>−1

X <em>t</em><sup>0</sup>−<em>t</em>

<em>r</em>(<em>τ<sub>i</sub></em>) =&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <em>γ&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; r</em>(<em>s<sub>it</sub></em>0<em>,a<sub>it</sub></em>0)<em>.</em>
</td>
<td width="155">(15)</td>
</tr>
</tbody>
</table>
<em>t</em><sup>0</sup>=<em>t</em>

Note that these differ only by the starting point of the summation.

Implement these return estimators as well as the remaining sections marked TODO in the code. For the smallscale experiments, you may skip those sections that are run only if nn baseline is True; we will return to baselines in Section 6. (These sections are in MLPPolicyPG:update and PGAgent:estimate advantage.)

<h1>5 Small-Scale Experiments</h1>
After you have implemented all non-baseline code from Section 4, you will run two small-scale experiments to get a feel for how different settings impact the performance of policy gradient methods.

<strong>Experiment 1 (CartPole). </strong>Run multiple experiments with the PG algorithm on the discrete CartPole-v0 environment, using the following commands:

<table width="634">
<tbody>
<tr>
<td width="634">python cs285/scripts/run_hw2.py –env_name CartPole-v0 -n 100 -b 1000 \

-dsa –exp_name q1_sb_no_rtg_dsa

python cs285/scripts/run_hw2.py –env_name CartPole-v0 -n 100 -b 1000 \

-rtg -dsa –exp_name q1_sb_rtg_dsa

python cs285/scripts/run_hw2.py –env_name CartPole-v0 -n 100 -b 1000 \

-rtg –exp_name q1_sb_rtg_na

python cs285/scripts/run_hw2.py –env_name CartPole-v0 -n 100 -b 5000 \

-dsa –exp_name q1_lb_no_rtg_dsa

python cs285/scripts/run_hw2.py –env_name CartPole-v0 -n 100 -b 5000 \

-rtg -dsa –exp_name q1_lb_rtg_dsa

python cs285/scripts/run_hw2.py –env_name CartPole-v0 -n 100 -b 5000 \

-rtg –exp_name q1_lb_rtg_na
</td>
</tr>
</tbody>
</table>
What’s happening here:

<ul>
<li>-n : Number of iterations.</li>
<li>-b : Batch size (number of state-action pairs sampled while acting according to the current policy at each iteration).</li>
<li>-dsa : Flag: if present, sets standardize_advantages to False. Otherwise, by default, standardizes advantages to have a mean of zero and standard deviation of one.</li>
<li>-rtg : Flag: if present, sets reward_to_go=True. Otherwise, reward_to_go=False by default.</li>
<li>–exp_name : Name for experiment, which goes into the name for the data logging directory.</li>
</ul>
Various other command line arguments will allow you to set batch size, learning rate, network architecture, and more. You can change these as well, but keep them fixed between the 6 experiments mentioned above.

<strong>Deliverables for report:</strong>

<ul>
<li>Create two graphs:
<ul>
<li>In the first graph, compare the learning curves (average return at each iteration) for the experiments prefixed with q1_sb_. (The small batch experiments.)</li>
<li>In the second graph, compare the learning curves for the experiments prefixed with q1_lb_. (The large batch experiments.)</li>
</ul>
</li>
<li>Answer the following questions briefly:
<ul>
<li>Which value estimator has better performance without advantage-standardization: the trajectorycentric one, or the one using reward-to-go?</li>
<li>Did advantage standardization help?</li>
<li>Did the batch size make an impact?</li>
</ul>
</li>
<li>Provide the exact command line configurations (or #@params settings in Colab) you used to run your experiments, including any parameters changed from their defaults.</li>
</ul>
<strong>What to Expect:</strong>

<ul>
<li>The best configuration of CartPole in both the large and small batch cases should converge to a maximum score of 200.</li>
</ul>
<strong>Experiment 2 (InvertedPendulum). </strong>Run experiments on the InvertedPendulum-v2 continuous control environment as follows:

<table width="634">
<tbody>
<tr>
<td width="634">python cs285/scripts/run_hw2.py –env_name InvertedPendulum-v2 \

–ep_len 1000 –discount 0.9 -n 100 -l 2 -s 64 -b &lt;b*&gt; -lr &lt;r*&gt; -rtg \

–exp_name q2_b&lt;b*&gt;_r&lt;r*&gt;
</td>
</tr>
</tbody>
</table>
where your task is to find the smallest batch size b* and largest learning rate r* that gets to optimum (maximum score of 1000) in less than 100 iterations. The policy performance may fluctuate around 1000; this is fine. The precision of b* and r* need only be one significant digit.

<strong>Deliverables:</strong>

<ul>
<li>Given the b* and r* you found, provide a learning curve where the policy gets to optimum (maximum score of 1000) in less than 100 iterations. (This may be for a single random seed, or averaged over multiple.)</li>
<li>Provide the exact command line configurations you used to run your experiments.</li>
</ul>
<h1>6 Implementing Neural Network Baselines</h1>
You will now implement a value function as a state-dependent neural network baseline. This will require filling in the remaining TODO sections skipped in Section 4. In particular:

<ul>
<li>This neural network will be trained in the update method of MLPPolicyPG along with the policy gradient update.</li>
<li>In pg agent.py:estimate advantage, the predictions of this network will be subtracted from the reward-to-go to yield an estimate of the advantage. This implements</li>
</ul>
<h1>7&nbsp; More Complex Experiments</h1>
<strong>Note: </strong>The following tasks take quite a bit of time to train. Please start early! For all remaining experiments, use the reward-to-go estimator.

<strong>Experiment 3 (LunarLander). </strong>You will now use your policy gradient implementation to learn a controller for LunarLanderContinuous-v2. The purpose of this problem is to test and help you debug your baseline implementation from Section 6.

Run the following command:

<table width="634">
<tbody>
<tr>
<td width="634">python cs285/scripts/run_hw2.py \

–env_name LunarLanderContinuous-v2 –ep_len 1000

–discount 0.99 -n 100 -l 2 -s 64 -b 40000 -lr 0.005 \

–reward_to_go –nn_baseline –exp_name q3_b40000_r0.005
</td>
</tr>
</tbody>
</table>
<strong>Deliverables:</strong>

<ul>
<li>Plot a learning curve for the above command. You should expect to achieve an average return of around 180 by the end of training.</li>
</ul>
<strong>Experiment 4 (HalfCheetah). </strong>You will be using your policy gradient implementation to learn a controller for the HalfCheetah-v2 benchmark environment with an episode length of 150. This is shorter than the default episode length (1000), which speeds up training significantly. Search over batch sizes b ∈ [10000<em>,</em>30000<em>,</em>50000] and learning rates r ∈ [0<em>.</em>005<em>,</em>0<em>.</em>01<em>,</em>0<em>.</em>02] to replace &lt;b&gt; and &lt;r&gt; below.

<table width="634">
<tbody>
<tr>
<td width="634">python cs285/scripts/run_hw2.py –env_name HalfCheetah-v2 –ep_len 150 \

–discount 0.95 -n 100 -l 2 -s 32 -b &lt;b&gt; -lr &lt;r&gt; -rtg –nn_baseline \

–exp_name q4_search_b&lt;b&gt;_lr&lt;r&gt;_rtg_nnbaseline
</td>
</tr>
</tbody>
</table>
<strong>Deliverables:</strong>

<ul>
<li>Provide a single plot with the learning curves for the HalfCheetah experiments that you tried. Describe in words how the batch size and learning rate affected task performance.</li>
</ul>
Once you’ve found optimal values b* and r*, use them to run the following commands (replace the terms in angle brackets):

<table width="634">
<tbody>
<tr>
<td width="634">python cs285/scripts/run_hw2.py –env_name HalfCheetah-v2 –ep_len 150 \

–discount 0.95 -n 100 -l 2 -s 32 -b &lt;b*&gt; -lr &lt;r*&gt; \

–exp_name q4_b&lt;b*&gt;_r&lt;r*&gt;

python cs285/scripts/run_hw2.py –env_name HalfCheetah-v2 –ep_len 150 \

–discount 0.95 -n 100 -l 2 -s 32 -b &lt;b*&gt; -lr &lt;r*&gt; -rtg \

–exp_name q4_b&lt;b*&gt;_r&lt;r*&gt;_rtg

python cs285/scripts/run_hw2.py –env_name HalfCheetah-v2 –ep_len 150 \

–discount 0.95 -n 100 -l 2 -s 32 -b &lt;b*&gt; -lr &lt;r*&gt; –nn_baseline \

–exp_name q4_b&lt;b*&gt;_r&lt;r*&gt;_nnbaseline

python cs285/scripts/run_hw2.py –env_name HalfCheetah-v2 –ep_len 150 \

–discount 0.95 -n 100 -l 2 -s 32 -b &lt;b*&gt; -lr &lt;r*&gt; -rtg –nn_baseline \

–exp_name q4_b&lt;b*&gt;_r&lt;r*&gt;_rtg_nnbaseline
</td>
</tr>
</tbody>
</table>
<strong>Deliverables: </strong>Provide a single plot with the learning curves for these four runs. The run with both rewardto-go and the baseline should achieve an average score close to 200.

<strong>8&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Bonus!</strong>

Choose any (or all) of the following:

<ul>
<li>A serious bottleneck in the learning, for more complex environments, is the sample collection time. In infrastructure/rl trainer.py, we only collect trajectories in a single thread, but this process can be fully parallelized across threads to get a useful speedup. Implement the parallelization and report on the difference in training time.</li>
<li>Implement GAE-<em>λ </em>for advantage estimation.<sup>1 </sup>Run experiments in a MuJoCo gym environment to explore whether this speeds up training. (Walker2d-v2 may be good for this.)</li>
<li>In PG, we collect a batch of data, estimate a single gradient, and then discard the data and move on. Can we potentially accelerate PG by taking multiple gradient descent steps with the same batch of data? Explore this option and report on your results. Set up a fair comparison between single-step PG and multi-step PG on at least one MuJoCo gym environment.</li>
</ul>
&nbsp;
