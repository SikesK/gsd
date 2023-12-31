# Goal State Divergence 

## Required Packages
### Python2.7 for the explanation generation scripts
### Python3 for grounder and parser
### Fast downward - http://www.fast-downward.org/
### VAL - https://github.com/KCL-Planning/VAL

## Greenhouse Quick Script 
### python3.8 Explainer.py -s KELSEYSEARCH -c ./gh_modifications_list.txt -m ../domain/benchmarks/water/original_domain.pddl -n ../domain/benchmarks/water/original_domain.pddl -t ../domain/benchmarks/water/domain_template.pddl -p ../domain/benchmarks/water/prob1.pddl -r ../domain/benchmarks/water/prob_template.pddl

## Driver Script Options
```
usage: Explainer.py [-h] [--approx] [--heuristic] [--ground] [-s SEARCH] -m
                    MODEL -n NMODEL -t TMODEL -p PROBLEM [-q HPROBLEM] -r
                    TPROBLEM [-f PLAN_FILE]

The driver Script for the Explanation generation

optional arguments:
  -h, --help            show this help message and exit
  --approx              Enable use of approximation (currently only supported
                        for ME).
  --heuristic           Enable use of heuristic (currently only supported for
                        ME)
  --ground              Consider model difference in grounded domain model
  -s SEARCH, --search SEARCH
                        Search to be use (ME or MCE)
  -m MODEL, --model MODEL
                        Domain file with real PDDL model of robot.
  -n NMODEL, --nmodel NMODEL
                        Domain file with human model of the robot.
  -t TMODEL, --tmodel TMODEL
                        Domain file template for the problem.
  -p PROBLEM, --problem PROBLEM
                        Problem file for robot.
  -q HPROBLEM, --hproblem HPROBLEM
                        Problem file for human.
  -r TPROBLEM, --tproblem TPROBLEM
                        Problem file template.
  -f PLAN_FILE, --plan_file PLAN_FILE
                        Plan file.

```
## Try out:
### Running ME on benchmark blocksworld problem
>> \>> python Explainer.py -s ME -m ../domain/benchmarks/blocksworld/original_domain.pddl -n ../domain/benchmarks/blocksworld/domain1.pddl -t ../domain/benchmarks/blocksworld/domain_template.pddl -p  ../domain/benchmarks/blocksworld/prob1.pddl -r ../domain/benchmarks/blocksworld/prob_template.pddl
## Note on Creating domain and problem templates
Since the system depends on generating temporary planning problems and domains, it expects the user to provide a domain and problem template. The domain template can be generated by replacing the action definitions in the original domain with the string %OPERATORS%. For the problem template, replace the initial state definition with the string %INIT% and the goal section with %goal%. Please check the benchmark files (./domain/benchmarks/) for specific examples. If you are using --ground flag also make sure to replace the predicates section in the domain file with the string %PREDICATES%.
## New grounder (derived from pyperplan parts https://bitbucket.org/malte/pyperplan)
python3  grounder_interface.py original_domain_file.pddl original_problem_file.pddl grounded_domain_file grounded_problem_file

## Please checkout the MEGA branch for running and testing MEGA algorithm. You can run MEGA algorithm by choosing the EE search.
