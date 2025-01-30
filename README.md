# rv32emu-rbtree-optimization

![linux-map vs jemalloc-map](./img/bench-plot.png)

## Overview

This project focuses on benchmarking and optimizing the red-black tree-based map used in rv32emu. The goal is to improve performance, memory efficiency, and execution speed through profiling, algorithmic refinements, and potential jemalloc-style enhancements.

This project aims to enhance the performance of [rv32emu](https://github.com/sysprog21/rv32emu) by addressing issue [#29](https://github.com/sysprog21/rv32emu/issues/29).

## Features

- 🚀 Benchmarking & Profiling: Measure insert, delete, and lookup performance.
- 🔧 Optimizations: Improve memory usage and execution speed.
- ⚡ Integration with rv32emu: Enhance existing map structures.
- 📊 Comparative Analysis: Test against alternative data structures.

## Results

The following data represents the average time of 20 experiments, each involving the insertion, finding, and deletion of 10 million randomly generated nodes in a random order. The experiments were conducted on an Apple M1 Pro (10-core) processor.

### Computation time improvement

10,000,000 random operations

| Type        | Insert (ns) |  Find (ns) | Remove (ns) |
| ----------- | ----------: | ---------: | ----------: |
| original    | 824,515,450 | 21,132,350 | 925,074,950 |
| proposed    | 535,518,250 | 10,032,300 | 602,755,100 |
| improvement |    **35 %** |   **52 %** |    **35 %** |

10,000,000 seqential operations

| Type        | Insert (ns) |  Find (ns) | Remove (ns) |
| ----------- | ----------: | ---------: | ----------: |
| original    | 306,238,550 | 91,349,500 | 201,321,050 |
| proposed    | 129,634,150 | 50,770,350 | 284,513,100 |
| improvement |    **57 %** |   **44 %** |    **-41%** |

### Memery improvement

| Type        | Total heap (B) | Useful heal (B) | Extra heap (B) |
| ----------- | -------------: | --------------: | -------------: |
| original    |      7,294,976 |       3,124,664 |      3,645,304 |
| proposed    |      6,241,680 |       2,597,592 |      3,117,096 |
| improvement |       **14 %** |        **17 %** |              - |

## Getting Started

### Prerequisite

C/Cpp

* CMake
* Make

Python

* matplot
* pandas
* numpy

### Installation

Clone the repository and build the project:

```shell
git clone https://github.com/EagleTw/rv32emu-rbtree-optimization
cd rv32emu-rbtree-optimization
cmake
make
```

### Running Benchmarks

Execute the benchmark suite with:

``` shell
./bench.sh
```

Modify parameters in `config.h` to adjust benchmarking scenarios.

## License

This project is licensed under the MIT License.

## Acknowledgments

Special thanks to the rv32emu developers and the jemalloc community for inspiration on memory-efficient red-black tree implementations.

