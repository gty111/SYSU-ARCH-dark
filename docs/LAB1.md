---
layout: default
title: I.Familiar with GEM5
nav_order: 3
---

# I Familiar with GEM5
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}
---

{: .outline}
> At this part, you will learn installation and use of GEM5

Freely read something about GEM5 on its [web page](https://www.gem5.org/).

## [Build GEM5(click me)](https://www.gem5.org/documentation/general_docs/building)

Recommend using [Docker](https://www.docker.com/)

### Install Docker

For windows, [install wsl](https://docs.microsoft.com/zh-cn/windows/wsl/install) first by using

```
wsl --install 
```

then [download Docker Desktop for Windows](https://docs.docker.com/desktop/install/windows-install/) and install.

{: .highlight}
> `wsl` is windows subsystem for linux. You can do most of the things you can do on Linux on WSL.
> 
> To integrate docker with wsl through `setting=>Resources=>WSL Integration`

For other systems, reference [this](https://docs.docker.com/desktop/).

### Build GEM5 with Docker

First,obtain GEM5 image

```
docker pull gcr.io/gem5-test/ubuntu-20.04_all-dependencies:v22-0
```

{: .highlight}
> Due to some reason, you may fail to pull that image, you can change `gcr.io` to `gcr.lank8s.cn`

Then, launch the container

```
docker run -itd -v <gem5 directiory>:/gem5 <image>
```

{: .highlight}
> using `docker images` to get info about `<image>`
> 
> using `git clone -b v22.0.0.2 https://github.com/gem5/gem5.git` to get gem5

Then,connect to the container

```
docker exec -it <container> /bin/bash
```

{: .highlight}
> using `docker ps` to get info about `<container>`

{: .question}
> `Question 1`: What is the meaning of `-itd -v ...` in `docker run -itd -v <gem5 directiory>:/gem5 <image>` ? What is the difference between `docker run` and `docker exec` ?  `optional`

## Write an insteresting app(sieve)

Write a program that outputs one single integer at the end `the number of prime numbers <= N`(at default N = 100,000,000) . Compile your program as a static binary. Note that your program must achieve O(N) complexity.

### Test sieve

You need to test your sieve program by building a `benchmark` program to validate its correctness and time complexity.

{: .highlight}
> `Hint` How to validate its time complexity ?

## Use GEM5
- to simulate the program in GEM5, these tutorials may be helpful

  - [create a simple configuration script](https://www.gem5.org/documentation/learning_gem5/part1/simple_config/)

  - [using the default configuration scripts](https://www.gem5.org/documentation/learning_gem5/part1/example_configs/)

- Run your sieve program in GEM5
  
  - choose an appropriate input size
  
  > {: .highlight}
  > You should use something large enough that the application is interesting, but not too large that gem5 takes more than 10 minutes to execute a simulation.
  
  - change the CPU model from TimingSimpleCPU to O3CPU.
  
  > {: .highlight}
  > `Challenge` : Can you change the CPU model to MinorCPU? GEM5 won't compile MinorCPU by default. You need to add some modifications. GEM5 use `CPU_MODELS` as a parameter in the past. Try to search the keyword `CPU_MODELS` and see what you can find out.
  
  - Vary the CPU clock from 1GHz to 2GHz (in steps of 1GHz) with both CPU models.
  
  - Change the memory configuration from DDR3_1600_x64 to DDR3_2133_x64 (DDR3 with a faster clock)

{: .question}
> `Question 2`: In each output, does `system.cpu.numCycles` times `system.clk_domain.clock` equals `simTicks` ? Why ?

## Submit

- Your config file (.py)

- The output (include config) under the **combination** (total is 8) of these configs

| CPU             | CPU_clock | DRAM          |
| --------------- | --------- | ------------- |
| TimingSimpleCPU | 1GHz      | DDR3_1600_x64 |
| O3CPU           | 2GHz      | DDR3_2133_x64 |

- Your `sieve` program and corresponding `benchmark` program

- Answer `Question 1(optional) and 2`

- Your solution to changing the CPU model to MinorCPU `challenge`
