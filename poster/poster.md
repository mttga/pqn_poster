
<!-- HEADER -->

</head>

<div style="height: 90pt;"></div>

<div class="header" style="border-bottom: 2px solid #a9b4c2; border-radius: 20px 20px 20px 20px; margin-top:20px; text-align: center; align-items: center; justify-content: center; margin-bottom:-5px; width: 100%;">
    <div>
        <h1 style="color: #2b3469; font-weight: 700; font-size:35px;">Simplifying Deep Temporal Difference Learning</h1>
        <h3 style="color: #2C4A67; margin-top: 0pt; margin-bottom: 0.2em;">Matteo Gallici*<sup>1</sup>, Mattie Fellows*<sup>2</sup>, Benjamin Ellis<sup>2</sup>, Bartomeu Pou<sup>1</sup>, Ivan Masmitja<sup>3</sup>, Jakob Foerster<sup>2</sup>, Mario Martin<sup>1</sup></h2>
        <h3 style="color:  #5763a6; margin-top: -2pt;"><sup>1</sup>Universitat Politècnica de Catalunya, <sup>2</sup>University of Oxford, <sup>3</sup>Institut de Ciències del Mar (ICM-CSIC)</h3>
        <h3 style="color:  #5763a6; margin-top: 0pt;">ICLR 2025</h3>
    </div>
</div>

--split--

<!-- FIRST COLUMN-->


<!-- MOTIVATION-->

<div class="header" style="background-color: #2b3469; border-color:#2b3469;">
  <h1 style="color: #e1e5fb;">Motivation</h1>
</div>


<div class="container">


  <div class="section" style="display: flex; margin-top:-10px">
    <div class="section-content">
      <h2>Vectorisation and Normalisation for a modern Q-Learning Baseline</h2>
      <ul>
        <li>Replay Buffers and Target networks make Q-Learning slow and complex.</i></li>
        <li>Standard Q-Learning does not benefit from vectorisation. The main baseline for vectorised-RL is PPO.</li>
        <li>Finding: <strong>Network Normalisation and Vectorised Exploration</strong> are just enough for Deep Q-Network to learn efficently <strong>without replay buffers and target networks</strong>.</li>
      </ul>
    </div>
    <div class="section-content" style="flex: 1.5;">
      <div class="image-container">
        <div class="image-column" style="margin-right:20px">
            <img src="../images/schemas/online.svg">
            <p>Online QLearning</p>
        </div>
        <div class="image-column" style="margin-left:20px">
            <img src="../images/schemas/dqn.svg">
            <p>DQN</p>
        </div>
      </div>
      <div class="image-container" style="margin-right:20px">
        <div class="image-column">
            <img src="../images/schemas/distributed.svg">
            <p>Distributed DQN</p>
        </div>
        <div class="image-column" style="margin-left:20px">
            <img src="../images/schemas/pqn.svg">
            <p>PQN</p>
        </div>
      </div>
    </div>
  </div>

  
</div>


<!-- Thoeretical Analysis -->

<div class="header" style="background-color: #2b3469; border-color:#a9b4c2;">
  <h1 style="color: #e1e5fb;">Theoretical Analisys of Network Normalisation in TD Learning</h1>
</div>

<div class="container" style="background-color: #2b3469; color: #e1e5fb; border-color:#a9b4c2">
  <ul style="margin-top: -25px">
      <li>Text.</li>
      <li>Inline Math: \(Q(\lambda)\)</li>
  </ul>
  <!-- Just some random math -->
  <p>
    $$
    \begin{eqnarray}
    \mathbf{O}_t^a = 
    \begin{bmatrix}
    ent_1
    \\ \vdots \\ 
    ent_k
    \end{bmatrix}_t^a =
    \begin{bmatrix}
    f_{1,1} & \cdots & f_{1,z} \\
    \vdots & \ddots & \vdots \\ 
    f_{k,1} & \cdots & f_{k,z}
    \end{bmatrix}
    _t^a
    \end{eqnarray}
    $$
  </p>
</div>


<!-- Method: PQN -->


<div class="header">
  <h1>Method: Parallelised Q-Network (PQN)</h1>
</div>

<div class="container">
  <img src="../images/algo.svg" class="centered-image" style="width: 70%;">
  <table class="styled-table" style="color:#2b3469; width: 90%;">
    <thead>
      <tr style="background-color:#e6e9fc; color:#2b3469">
        <th>&nbsp;</th>
        <th>DQN</th>
        <th>Distr. DQN</th>
        <th>PPO</th>
        <th>PQN</th>
      </tr>
    </thead>
    <tbody>
      <tr style="background-color:white">
        <td style="padding: 5px; font-weight: bold">Implementation</td>
        <td style="padding: 5px">Easy</td>
        <td style="padding: 5px">Difficult</td>
        <td style="padding: 5px">Medium</td>
        <td style="padding: 5px"><b>Very Easy</b></td>
      </tr>
      <tr style="background-color:#f3f3f3">
        <td style="padding: 5px; font-weight: bold">Memory Requirement</td>
        <td style="padding: 5px">High</td>
        <td style="padding: 5px">Very High</td>
        <td style="padding: 5px"><b>Low</b></td>
        <td style="padding: 5px"><b>Low</b></td>
      </tr>
      <tr style="background-color:white">
        <td style="padding: 5px; font-weight: bold">Training Speed</td>
        <td style="padding: 5px">Slow</td>
        <td style="padding: 5px"><b>Fast</b></td>
        <td style="padding: 5px"><b>Fast</b></td>
        <td style="padding: 5px"><b>Fast</b></td>
      </tr>
      <tr style="background-color:#f3f3f3">
        <td style="padding: 5px; font-weight: bold">Sample Efficient</td>
        <td style="padding: 5px"><b>Yes</b></td>
        <td style="padding: 5px">No</td>
        <td style="padding: 5px"><b>Yes</b></td>
        <td style="padding: 5px"><b>Yes</b></td>
      </tr>
      <tr style="background-color:white">
        <td style="padding: 5px; font-weight: bold">Compatibility with RNNs</td>
        <td style="padding: 5px">Medium</td>
        <td style="padding: 5px">Medium</td>
        <td style="padding: 5px"><b>High</b></td>
        <td style="padding: 5px"><b>High</b></td>
      </tr>
      <tr style="background-color:#f3f3f3">
        <td style="padding: 5px; font-weight: bold">Compatibility w. end-to-end GPU Training</td>
        <td style="padding: 5px">Low</td>
        <td style="padding: 5px">Low</td>
        <td style="padding: 5px"><b>High</b></td>
        <td style="padding: 5px"><b>High</b></td>
      </tr>
      <tr style="background-color:white">
        <td style="padding: 5px; font-weight: bold">Amount of Hyper-Parameters</td>
        <td style="padding: 5px">Medium</td>
        <td style="padding: 5px">High</td>
        <td style="padding: 5px">Medium</td>
        <td style="padding: 5px"><b>Low</b></td>
      </tr>
      <tr style="background-color:#f3f3f3">
        <td style="padding: 5px; font-weight: bold">Convergence</td>
        <td style="padding: 5px">No</td>
        <td style="padding: 5px">No</td>
        <td style="padding: 5px">No</td>
        <td style="padding: 5px"><b>Yes</b></td>
      </tr>
    </tbody>
  </table>
</div>


--split--

<!-- SECOND COLUMN-->

<!-- Experiments-->

<div class="header" style="background-color: #0000;">
  <h1>Experiments</h1>
</div>

<div class="container" style="background-color: #0000;">


  <h2 style="margin-top:-10px">Atari</h2>
  <div class="image-container">
      <div class="image-column">
          <img src="../images/experiments/atari-10.png">
          <p>Atari-10 Score</p>
      </div>
      <div class="image-column">
          <img src="../images/experiments/atari-57_median.png">
          <p>Atari-57 Median Score</p>
      </div>
      <div class="image-column">
          <img src="../images/experiments/atari-57_tau.png">
          <p>Atari-57 Perfomrnace Score</p>
      </div>
      <div class="image-column">
          <img src="../images/experiments/atari-57_speed.png">
          <p>Atari-57 Training Speed</p>
      </div>
  </div>


  <h2 style="margin-top:-10px">Craftax and JaxMarl</h2>
  <div class="image-container">
      <div class="image-column">
          <img src="../images/experiments/craftax_rnn.png">
          <p>Craftax</p>
      </div>
      <div class="image-column">
          <img src="../images/experiments/smax_iqm.png">
          <p>Smax</p>
      </div>
      <div class="image-column">
          <img src="../images/experiments/overcooked_iqm.png">
          <p>Overcooked</p>
      </div>
      <div class="image-column">
          <img src="../images/experiments/hanabi.png">
          <p>Hanabi</p>
      </div>
  </div>

  <h2 style="margin-top:-10px">Ablations</h2>
  <div class="image-container">
      <div class="image-column">
          <img src="../images/experiments/bairds.png">
          <p>Baird's Counter-Example</p>
      </div>
      <div class="image-column">
          <img src="../images/experiments/deepsea_40.png">
          <p>DeepSea (depth 40)</p>
      </div>
      <div class="image-column">
          <img src="../images/experiments/atari-off-policy.png">
          <p>Learning from almost-random policy.</p>
      </div>
      <div class="image-column">
          <img src="../images/experiments/atari-normalization.png">
          <p>Normalisation in Atari</p>
      </div>
  </div>
  <div class="image-container">
      <div class="image-column">
          <img src="../images/experiments/craftax-normalization.png">
          <p>Normalisation in Craftax</p>
      </div>
      <div class="image-column">
          <img src="../images/experiments/craftax_buffer.png">
          <p>GPU-Replay Buffer in Craftax</p>
      </div>
      <div class="image-column">
          <img src="../images/experiments/minatar_iqm.png">
          <p>Number of Environments (MinAtar)</p>
      </div>
      <div class="image-column">
          <img src="../images/experiments/atari-lambda.png">
          <p>Effect of \(Q(\lambda)\) in Atari-10</p>
      </div>
  </div>

</div>

<!-- LOGOS-->


<div class="header" style="text-align: center; background-color: #2b3469; border-color: #2b3469; color: #e1e5fb; padding-top:50px; margin-bottom: 0;">
  <img src="../images/github_qr.svg" style="width:250px" alt="Github QR Code">
  <p><a href="https://github.com/mttga/purejaxql" target="_blank" style="color:#e1e5fb">github.com/mttga//github.com/mttga/purejaxql</a></p>
</div>

<div class="container" style="text-align: center; background-color: #e6e9fc; padding-top:30px; padding-bottom:47px">
  <div class="section-image"> 
      <div class="image-column" style="margin:10px">
        <img src="../images/oxford_logo.svg" style="max-width: 120px;">
      </div>
      <div class="image-column" style="margin:10px">
        <img src="../images/Logo_UPC.svg" style="max-width:90px;">
      </div>
      <div class="image-column" style="margin:30px">
        <img src="../images/BSC-blue.svg">
      </div>
      <div class="image-column" style="margin:10px">
        <img src="../images/csic_logo.svg" style="max-width: 130px;">
      </div>
    </div>
  </div>
</div>