# Traffic-Aware Route Optimization using Genetic Algorithm and Ant Colony Optimization

## Overview

A C++ implementation of a hybrid optimization approach combining **Genetic Algorithm (GA)** and **Ant Colony Optimization (ACO)** to solve a Traffic-Aware Travelling Salesman Problem (TSP).

The project aims to find efficient routes between 10 cities by considering both geographical distance and traffic conditions. Instead of optimizing distance alone, it introduces traffic-weighted route costs to evaluate and compare different travel paths.

The hybrid approach uses Genetic Algorithms to evolve candidate routes and Ant Colony Optimization concepts to refine routes using pheromone-based information.

## Key Features

- **Hybrid Optimization:** Combines Genetic Algorithm and Ant Colony Optimization in a single optimization pipeline.
- **Traffic-Aware Route Evaluation:** Evaluates routes using both distance and traffic multipliers.
- **Population-Based Search:** Generates and evolves a population of candidate routes across multiple generations.
- **Order Crossover:** Combines parent routes while maintaining valid city permutations.
- **Mutation:** Introduces random swaps to maintain population diversity.
- **Pheromone-Based Refinement:** Uses pheromone information and heuristic desirability to refine candidate routes.
- **Pheromone Evaporation:** Reduces previous pheromone values to balance historical information and new discoveries.
- **Route Comparison:** Displays the best traffic-weighted route alongside the shortest-distance route.

## Algorithms Used

### 1. Genetic Algorithm (GA)

Genetic Algorithm is an evolutionary optimization technique inspired by natural selection.

In this project, GA is responsible for exploring different city sequences and evolving candidate routes over multiple generations.

**Implementation steps:**

1. **Population Initialization:** Generates 90 randomized candidate routes, each containing all 10 cities.
2. **Parent Selection:** Randomly selects two parent routes from the current population.
3. **Crossover:** Applies an order-preserving crossover operation to combine genetic information from both parents.
4. **Mutation:** Randomly swaps two city positions with a probability of 0.1.
5. **Fitness Evaluation:** Evaluates candidate routes using the traffic-weighted route cost.
6. **Generation Update:** Replaces the current population with the newly generated population.

### 2. Ant Colony Optimization (ACO)

Ant Colony Optimization is a nature-inspired optimization technique based on the foraging behavior of ants.

The project incorporates ACO concepts to refine candidate routes using pheromone values and heuristic desirability.

**Implementation steps:**

1. **Pheromone Initialization:** Initializes pheromone values for city-to-city transitions.
2. **Route Refinement:** Evaluates consecutive city transitions using pheromone strength and traffic-adjusted distance.
3. **Heuristic Evaluation:** Considers the inverse of traffic-weighted distance when evaluating route desirability.
4. **Pheromone Evaporation:** Reduces existing pheromone values using an evaporation rate of 0.5.
5. **Pheromone Update:** Adds pheromone contributions based on the quality of generated routes.

### 3. Hybrid GA + ACO Approach

The two optimization techniques work together in each generation:

- GA generates new candidate routes through selection, crossover, and mutation.
- ACO-based refinement adjusts candidate routes using pheromone and heuristic information.
- Pheromone values are updated based on the resulting population.
- The process repeats for 100 generations.

This combines population-based evolutionary exploration with pheromone-guided route refinement.

## Traffic-Aware Cost Function

The project evaluates each route using a combination of distance and traffic multipliers.

For a route containing consecutive cities \(c_0,c_1,\ldots,c_{n-1}\), the objective function is:

\[
C(R)=\sum_{i=0}^{n-2}
d(c_i,c_{i+1})\times t(c_i,c_{i+1})
\]

Where:

- \(d(u,v)\) = distance between cities \(u\) and \(v\).
- \(t(u,v)\) = traffic multiplier between cities \(u\) and \(v\).
- \(C(R)\) = total traffic-weighted route cost.

A higher traffic multiplier increases the cost of travelling through that connection.

The implementation also calculates the geographical distance without traffic multipliers to compare distance-only and traffic-aware route selection.

## ACO Parameters

The optimization uses the following predefined parameters:

| Parameter | Value | Description |
|---|---:|---|
| Alpha (α) | 1.0 | Pheromone importance |
| Beta (β) | 5.0 | Heuristic importance |
| Evaporation Rate | 0.5 | Pheromone evaporation |
| Q | 100.0 | Pheromone contribution constant |

## Genetic Algorithm Parameters

| Parameter | Value |
|---|---:|
| Number of Cities | 10 |
| Population Size | 90 |
| Maximum Generations | 100 |
| Mutation Rate | 0.1 |

## Technologies Used

- **Language:** C++
- **Standard Libraries:** STL, Vector, Algorithm, Random, Math, I/O Manipulation
- **Algorithms:** Genetic Algorithm, Ant Colony Optimization
- **Concepts:** Combinatorial Optimization, Graphs, Heuristic Search, Probabilistic Optimization

## Output

The program displays optimization results after every generation, including:

- Best traffic-weighted route.
- Shortest geographical-distance route.
- Corresponding route sequences.
- Route cost comparisons.

At the end of the execution, the final results are displayed in a formatted console table.

## Getting Started

### Prerequisites

- C++ compiler supporting C++11 or later.
- GCC, Clang, or another compatible compiler.

### Compilation

Save the source code as `main.cpp` and compile using:

```bash
g++ -std=c++11 -O2 main.cpp -o route_optimizer
```

### Execution

On Linux/macOS:

```bash
./route_optimizer
```

On Windows:

```bash
route_optimizer.exe
```

## Learning Outcomes

- Understanding evolutionary optimization through Genetic Algorithms.
- Applying Ant Colony Optimization concepts to route refinement.
- Designing multi-factor objective functions for optimization problems.
- Working with probabilistic selection and randomized search.
- Understanding pheromone evaporation and heuristic-based decisions.
- Implementing hybrid optimization techniques in C++.

## Author

**Ayush Gusain**

- GitHub: [Ayush1W1312](https://github.com/Ayush1W1312)
- LinkedIn: [Ayush Gusain](https://linkedin.com/in/ayush-gusain-090bb632a)
