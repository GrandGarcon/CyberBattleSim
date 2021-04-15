# CyberBattleSim + : Beyond the hype.

# Credits

this project is the clone and improvised version of microsoft researchers , you can get more information regarding their findings in the following blog

> April 8th, 2021: See the [announcement](https://www.microsoft.com/security/blog/2021/04/08/gamifying-machine-learning-for-stronger-security-and-ai-models/) on the Microsoft Security Blog.
> and their repository README for the initial reference .

also there are numerous other repositories available in this field [1](https://github.com/nickromandini/reinforcement-learning-cybersecurity) , [2]()

# Abstract

Currently CyberBattleSim really is an interesting spark for the researchers in the field for experimenting the use of RL for policy making of better cybersecurity posture analysis . generally this has been considered out of reach problem due to the sheer complexicity of encoding the the states (From the network primitives hosting the TCP/IP stack to the cloud instances providing numerous tech stack and security policies like VPC & WAF / zero trust networks / endpoint detection and response etc) , defining the possible goal policies for real life enterprise networks has been mammoth tasks , specially given that you adversary is also perfected his art of running APT campaigns.

but currently , recent progress in making services which provide agent
based security , best examples like [sqreen](https://github.com/sqreen/go-agent/tree/master) and the wide suite of verticals ( ci pipelines to run automated tests , checking the CTI features to understand the diffrent results ) has provided an wide ontology in understanding the nature of adversary (whether being an actor or an automated malware underneath with the E2E infrastructure for the whole cybersecurity attack chain ).

Also unlike the previous assumption of using an physical simulator with very limited number of topologies , the simulation will include the tests on the following Enviornments :

1.  [gns3](https://www.gns3.com/) , an basic routing simulation tool for showing the propagation of the network packets in the LAN configurations . trying to detect possiblity of checking the malicious created network packet( using pyscapy) transferring till the firewall simulation.

2.[openstack](https://www.openstack.org/) : An open source application for creating cloud networking envioenment (defining simulation of real time cloud platforms like AWS).

The goal of the attacker is to take ownership of a portion of the network by exploiting
vulnerabilities that are planted in the computer nodes.
While the attacker attempts to spread throughout the network,
a defender agent watches the network activity and tries to detect
any attack taking place and mitigate the impact on the system
by evicting the attacker.

## TODO : defining the strategy of the adversary agent and defending agent .

We provide a basic stochastic defender that detects
and mitigates ongoing attacks based on pre-defined probabilities of success.
We implement mitigation by re-imaging the infected nodes, a process
abstractly modeled as an operation spanning over multiple simulation steps.

To compare the performance of the agents we look at two metrics: the number of simulation steps taken to
attain their goal and the cumulative rewards over simulation steps across training epochs.

## Project goals

As told in the parent project , this will be an stepping stone for creating agents that might be working in real time network scenarios . my main aim is to work on the whole simulation enviornment from realistic tools , then getting the required knowledge ontology for each of the agents (based on initially certain types of stateless network attacks from nist cve detection , etc ). this will be an major aim to promote transparency regarding the possible state of the art of these technologies

The simulation we provide is admittedly simplistic, but this has advantages. Its highly abstract nature prohibits direct application to real-world systems thus providing a safeguard against potential nefarious use of automated agents trained with it.
At the same time, its simplicity allows us to focus on specific security aspects we aim to study and quickly experiment with recent machine learning and AI algorithms.

For instance, the current implementation focuses on
the lateral movement cyber-attacks techniques, with the hope of understanding how network topology and configuration affects them. With this goal in mind, we felt that modeling actual network traffic was not necessary. This is just one example of a significant limitation in our system that future contributions might want to address.

On the algorithmic side, we provide some basic agents as starting points, but we
would be curious to find out how state-of-the art reinforcement learning algorithms compare to them. We found that the large action space
intrinsic to any computer system is a particular challenge for
Reinforcement Learning, in contrast to other applications such as video games or robot control. Training agents that can store and retrieve credentials is another challenge faced when applying RL techniques
where agents typically do not feature internal memory.
These are other areas of research where the simulation could be used for benchmarking purposes.

Other areas of interest include the responsible and ethical use of autonomous
cyber-security systems: How to design an enterprise network that gives an intrinsic
advantage to defender agents? How to conduct safe research aimed at defending enterprises against autonomous cyber-attacks while preventing nefarious use of such technology?

## Documentation

Read the [Quick introduction](/docs/quickintro.md) to the project.

## Build status

| Type         | Branch | Status                                                                                                                                          |
| ------------ | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| CI           | master | ![.github/workflows/ci.yml](https://github.com/microsoft/CyberBattleSim/workflows/.github/workflows/ci.yml/badge.svg)                           |
| Docker image | master | ![.github/workflows/build-container.yml](https://github.com/microsoft/CyberBattleSim/workflows/.github/workflows/build-container.yml/badge.svg) |

## Benchmark

See [Benchmark](/docs/benchmark.md).

## Setting up a dev environment

It is strongly recommended to work under a Linux environment, either directly or via WSL on Windows.
Running Python on Windows directly should work but is not supported anymore.

Start by checking out the repository:

```bash
git clone https://github.com/microsoft/CyberBattleSim.git
```

### TODO: add the support for the docker image for the model.

### On Linux or WSL

The instructions were tested on a Linux Ubuntu distribution (both native and via WSL). Run the following command to set-up your dev environment and install all the required dependencies (apt and pip packages):

```bash
./init.sh
```

The script installs python3.8 if not present. If you are running a version of Ubuntu older than 20 it will automatically add an additional apt repository to install python3.8.

The script will create a [virtual Python environment](https://docs.python.org/3/library/venv.html) under a `venv` subdirectory, you can then
run Python with `venv/bin/python`.

> Note: If you prefer Python from a global installation instead of a virtual environment then you can skip the creation of the virtual envrionment by running the script with `./init.sh -n`. This will instead install all the Python packages on a system-wide installation of Python 3.8.

## Check your environment

TODO

## Jupyter and [enso](https://enso.org/) documentations.

either you can practice with the already deployed jupyter documentation , along with another amazing data science oriented IDE named Enso , which allows to preprocess and get interesting insights of the network logs wrt the diffrent types of attacks.

- 'Capture The Flag' toy environment notebooks:

  - [Random agent](notebooks/toyctf-random.ipynb)
  - [Interactive session for a human player](notebooks/toyctf-blank.ipynb)
  - [Interactive session - fully solved](notebooks/toyctf-solved.ipynb)

- Chain environment notebooks:

  - [Random agent](notebooks/chainnetwork-random.ipynb)

- Other environments:
  - [Interactive session with a randomly generated environment](notebooks/randomnetwork.ipynb)
  - [Random agent playing on randomly generated networks](notebooks/c2_interactive_interface.ipynb)

The following `.py` notebooks are best viewed in VSCode or in Jupyter with the [Jupytext extension](https://jupytext.readthedocs.io/en/latest/install.html)
and can easily be converted to `.ipynb` format if needed:

- Chain environments benchmarks:

  - [Benchmark of all baseline agents](cyberbattle/agents/baseline/notebooks/notebook_all_agents_benchmark.py)
  - [All baseline agents against a basic defender](cyberbattle/agents/baseline/notebooks/notebook_withdefender.py)
  - [DeepQL](cyberbattle/agents/baseline/notebooks/notebook_dql.py)
  - [Epsilon greedy](cyberbattle/agents/baseline/notebooks/notebook_randlookups.py)
  - [Tabular Q Learning](cyberbattle/agents/baseline/notebooks/notebook_tabularq.py)

- Capture the Flag benchmark:
  - [DeepQL](cyberbattle/agents/baseline/notebooks/notebook_ctf_dql.py)

## How to instantiate the enviornment ?

TODO

## Contributing

This project welcomes contributions and suggestions. Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

### Ideas for contributions

Apart from the [wiki for more ideas](https://github.com/microsoft/CyberBattleGym/wiki/Possible-contributions). from the microsoft . interested devs can :star: the respository along with giving more information

## Citing this project

```bibtex
@misc{msft:cyberbattlesim,
  Author = {Microsoft Defender Research Team.}
  Note = {Created by Christian Seifert, Michael Betser, William Blum, James Bono, Kate Farris, Emily Goren, Justin Grana, Kristian Holsheimer, Brandon Marken, Joshua Neil, Nicole Nichols, Jugal Parikh, Haoran Wei.},
  Publisher = {GitHub},
  Howpublished = {\url{https://github.com/microsoft/cyberbattlesim}},
  Title = {CyberBattleSim},
  Year = {2021}
}
```

## Note on privacy

This project does not include any PII ( i.e event / network logs from actual enterprise / cloud network ) and IT SHOULD BE ENSURED FOR DEPLOYING THIS ON REAL TIME USE CASE , PLEASE TAKE INTO CONSIDERATION THE LEGAL REMEDIES INTO ACCOUNT AND DONT BREAK THE CYBER LAWS.

## Trademarks

All the references to the microsoft logos and tm of the terms belong to [Microsoft's Trademark & Brand Guidelines](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general). but for the long term will remove their references
