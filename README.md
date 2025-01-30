# rv32emu-rbtree-optimization

![linux-map vs jemalloc-map](./img/bench-plot.png)

## About this project

This project aims to enhance the performance of [rv32emu](https://github.com/sysprog21/rv32emu) by addressing issue [#29](https://github.com/sysprog21/rv32emu/issues/29).

The original implementation of rv32emu utilizes a Linux-like red-black tree, providing a C++ std::map-like interface. As part of this project, the red-black tree implementation has been modified from jemalloc, resulting in improved performance for map insertion, find, and delete operations.

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

Clone to your local directory

```shell
git clone https://github.com/EagleTw/rv32emu-rbtree-optimization
```

Run cmake

```
cmake .
```

Compile and create executables

```
make
```

## Usage

Run bench

``` shell
./bench.sh
```

## Roadmap

* [x] Clone jemalloc rb.h
* [x] Integrate map interface to match C++ std::map
* [x] Create test for correctness
* [x] Create bench plot
* [x] Computational time and memory benchmark
* [x] PR
