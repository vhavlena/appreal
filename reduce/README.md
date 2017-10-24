# Approximate Reduction of NFAs

Prototype tool for approximate reduction of NFAs used in network traffic
filtering writen in Python 2.6. The tool provides the reduction of NFAs using the pruning reduction
and the self-loop reduction. The tool provides also the computation of the
probabilistic distance.

## Installation
The prototype tool is written in Python 2.7. Required Python libraries:
 - **NumPy** for linear algebra operations,
 - **PuLP** for solving (integer) linear programming problems,
 - **FAdo** for operations with finite automata,
 - **Scapy** for operations with PCAP files,
 - **SciPy** for scientific operations.

## Automata Format
NFAs are specified using the **FA format**, which is given as follows.
```
<initial state>\n
(:(<symbol in hexa> )*\n)?
(<source state> <destination state> <symbol in hexa>\n)*
(<final state>\n)*
```
An example of the content of a FA file.
```
0
:0x61 0x62
0 1 0x61
1 2 0x61
2 3 0x62
3 4 0x62
4 0 0x61
2
3
4
```

PAs are specified using a format, which given as follows. The initial
state is implicitly the state 0.
```
<source state> <destination state> <symbol in dec> <probability>\n)*
(<final state> <probability>\n)*
```
An example of the content of a file describing a PA:
```
0 0 97 0.5
0 0 98 0.4
0 0.1
```

## Experiments
For experiments fill in variables in files `prepare.sh`, `experiments-size.sh`, 
`experiments-error.sh` (name of the NFA, PA, path to [Reduce tool](http://languageinclusion.org/doku.php?id=tools)). 
Script `prepare.sh` prepare a NFA for an experiment (it is necessary to 
run this script before running any of `experiments-size.sh` and 
`experiments-error.sh`). Each run of the scripts `experiments-size.sh` and 
`experiments-error.sh` reduces one NFA with various reduction parameters.

1. Download and extract the [Reduce tool](http://languageinclusion.org/doku.php?id=tools)) into the root directory

```
[in the repository's root directory]
wget -O rabit.tar.gz 'http://languageinclusion.org/lib/exe/fetch.php?media=rabit2.4.3.tar.gz'
tar xzvf rabit.tar.gz
```

1. Set the paths in `prepare.sh` to the correct ones

```
cd reduce
[edit prepare.sh]
./prepare.sh
```

## Contributors
- Vojtěch Havlena `<ihavlena[at]fit.vutbr.cz>`