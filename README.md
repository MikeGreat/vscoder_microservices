# vscoder_microservices

[![Build Status](https://travis-ci.com/Otus-DevOps-2019-08/vscoder_microservices.svg?branch=master)](https://travis-ci.com/Otus-DevOps-2019-08/vscoder_microservices)

vscoder microservices repository

- [vscoder_microservices](#vscodermicroservices)
- [Makefile](#makefile)
  - [Variables](#%d0%9f%d0%b5%d1%80%d0%b5%d0%bc%d0%b5%d0%b5)
  - [Goals](#%d0%a6%d0%b5%b5%d0%b8)
- [Homework](#%d0%94%d0%be%d0%bc%d0%b0%d1%88%d0%bd%d0%b8%d0%b5-%d0%b7%d0%b0%b4%d0%b0%d0%bd%d0%b8%d1%8f)
  - [HomeWork 12: Containerization technology. Introduction to Docker](#homework-12-%d0%a2%d0%b5%d1%85%d0%bd%d0%be%d0%b%d0%be%d0%b3%d0%b8%d1%8f-) %d0%ba%d0%be%d0%bd%d1%82%d0%b5%d0%b9%d0%bd%d0%b5%d1%80%d0%b8%d0%b7%d0%b0%d1%86%d0%b8%d0%b8-%d0%92%d0%b2%d0%b5-%d0%b2-docker)
    - [Project preparation. Integration](#%d0%9f%d0%be%d0%b4%d0%b3%d0%be%d1%82%d0%be%d0%b2%d0%ba%d0%b0-%d0%bf%d1%80%d0%be%d0%b5%d0%ba%1%82%d0%b0-%d0%98%d0%bd%d1%82%d0%b5%d0%b3%d1%80%d0%b1%86%d0%b8%d0%b8)
    - [Installing docker](#%d0%a3%d1%81%d1%82%d0%b0%d0%bd%d0%be%d0%b2%d0%ba%d0%b0-docker)
    - [Working with docker](#%d0%a0%d0%b0%b1%d0%be%d1%82%d0%b0-%d1%81-docker)
    - [Assignment from \*: Distinctions between image and container](#%d0%97%d0%b0%d0%b4%d0%b0%d0%b8%d0%b5-%d1%81%d0%be-- %d0%9e%d1%82%d0%bb%d0%b8%d1%87%d0%b8%d1%8f-%d0%be%d0%b1%d1%80%b0%d0%b7%d0%b0-%d0%b8-%d0%ba%d0%be%d0%b%1%82%d0%b5%d0%b9%d0%bd%d0%b5%d1%80%d0%b0)
    - [More docker commands](#%d0%91%d0%be%d0%bb%d1%8c%d1%88%d0%b5-docker-%d0%ba%d0%be%d0%bc%d0%b0%d0%b4)
      - [Docker kill & stop](#docker-kill-stop)
      - [docker system df](#docker-system-df)
      - [Docker rm & rmi](#docker-rm--rmi)
    - [Docker containers](#docker-%d0%ba%d0%be%d0%bd%1%82%d0%b5%d0%b9%d0%bd%d0%b5%d1%80%d1%8b)
      - [GCE](#gce)
      - [Docker machine](#docker-machine)
      - [Working with namespaces](#%d0%a0%d0%b0%b1%d0%be%d1%82%d0%b0-%d1%81-namespaces)
        - [PID namespace](#pid-namespace)
        - [NET namespace](#net-namespace)
        - [USER namespace](#user-namespace)
      - [Dockerfile](#dockerfile)
      - [Container launch](#%d0%97%d0%b0%d0%bf%d1%83%d1%81%d0%ba-%d0%ba%d0%be%d0%bd%1%82%d0%b5%d0%b9%d0%bd%d0%b5%d1%80%d0%b0)
    - [Docker hub](#docker-hub)
    - [Assignment from \*: IaC using docker](#%d0%97%d0%b0%d0%b4%d0%b0%d0%b8%d0%b5-%d1%81%d0%be-iac-%d1%81-%d0%b8%d1%81%d0%bf%d0%be%d0%bb%d1%8c%d0%b7%d0%be%d0%b2%d0%b0%b8%d0%b8%d0%b5%d0%bc-docker)
      - [Packer](#packer)
      - [Terraform](#terraform)
        - [Project-wide objects](#project-wide-%d0%be%d0%b1%d1%8a%d0%b5%d0%ba%d1%82%d1%8b)
        - [Modules](#%d0%9c%d0%be%d0%b4%d1%83%d0%b%d0%b8)
        - [Stage environment](#stage-%d0%be%d0%ba%d1%80%d1%83%d0%b6%d0%b5%d0%b8%d0%b5)
      - [Launch container by means of ansible](#%d0%97%d0%b0%b0%bf%d1%83%d1%81%d0%ba- %d0%ba%d0%be%d0%bd%d1%82%d0%b5%d0%b9%d0%bd%d0%b5%d1%81%81%81%80%d0%b5%d0%b4%d1%81%d1%82%d0%b2%d0%b0%d0%bc%d0%b8-ansible)
    - [Outside ERS: security](#%d0%92%d0%bd%d0%b5-%d0%94%d0%97-%d0%b1%d0%b5%d0%b7%d0%be%d0%bf%d0%b0%d1%81%d0%bd%d0%be%d1%81%d1%82%d1%8c)
      - [TODO:](#todo)
      - [Docker Security Benchmark](#docker-security-benchmark)
  - [HomeWork 13: Docker-images and Microservices](#homework-13-docker-%d0%be%d0%b1%d1%80%d0%b0%b7%d1%8b-%d0%b8-%d0%9c%d0%b8%d0%ba%d1%80%d0%be%d1%81%d0%b5%d1%80%b2%d0%b8%d1%8b)
    - [Preparation](#%d0%9f%d0%be%d0%b4%d0%b3%d0%b1%82%d0%be%d0%b2%d0%ba%d0%b0)
      - [Dockerfile best practices (collapsed)](#dockerfile-best-practices-collapsed)
        - [FROM](#from)
        - [LABEL](#label)
        - [RUN](#run)
        - [CMD](#cmd)
        - [EXPOSE](#expose)
        - [ENV](#env)
        - [ADD or COPY](#add-or-copy)
        - [ENTRYPOINT](#entrypoint)
        - [VOLUME](#volume)
        - [USER](#user)
        - [WORKDIR](#workdir)
        - [ONBUILD](#onbuild)
    - [Launch](#%d0%97%d0%b0%d0%bf%d1%83%d1%81%d0%ba)
      - [New application structure](#%d0%9d%d0%be%d0%b2%d0%b0%d1%8f-%81%d1%82%d1%80%d1%83%d0%ba%d1%82%d1%83%d1%80%b0-%d0%bf%d1%80%d0%b8%d0%b%d0%be%d0%b6%d0%b5%d0%b8%d1%8f)
      - [Collecting images](#%d0%a1%d0%b1%d0%be%d1%80%d0%ba%d0%b0-%d0%be%d0%b1%d1%80%d0%b0%b7%d0%be%d0%b2)
      - [Launch the application](#%d0%97%d0%b0%d0%bf%d1%83%d1%81%d0%ba-%d0%bf%d1%80%d0%b8%d0%b%d0%be%d0%b6%d0%b5%d0%bd%d0%b8%d1%8f)
    - [Assignment from \*: Redefining network aliases](#%d0%97%d0%b0%d0%b4%d0%b0%d0%bd%d0%b8%d0%b5-%d1%81%d0%be-- %d0%9f%d0%b5%d1%80%d0%b5%d0%be%d0%bf%d1%80%d0%b5%d0%b4%d0%b5%d0%b5%d0%b5%d0%b8%d0%b5-%d1%81%d0%b5%d1%82%d0%b5%d0%b2%d1%8b%d1%85-%d0%b0%b%d0%b8%d0%b1%81%d0%b2)
      - [Theory](#%d0%a2%d0%b5%d0%be%d1%80%d0%b8%d1%8f)
      - [Implementation](#%d0%a0%d0%b5%d0%b0%b0%b8%d0%b7%d0%b0%d1%86%d0%b8%d1%8f)
    - [Images](#%d0%9e%d0%b1%d1%80%d0%b0%b7%d1%8b)
    - [Assignment from \*: Decrease the size of the image](#%d0%97%d0%b0%d0%b4%d0%b0%d0%b8%d0%b5-%d1%81%d0%be-- %d0%a3%d0%bc%d0%b5%d0%bd%1%8c%d1%88%d0%b0%b5%d0%bc-%d1%80%d0%b0%d7%d0%bc%d0%b5%d1%80-%d0%be%d0%b1%d1%80%d0%b0%d7%d0%b0)
      - [Analysis](#%d0%90%d0%bd%d0%b0%b8%d0%b7)
      - [Assembly based on alpine linux](#%d0%a1%d0%b1%d0%be%d1%80%d0%ba%d0%b0-%d0%bd%d0%b0-%d0%be%d1%81%d0%bd%d0%be%d0%b2%d0%b5-alpine-linux)
        - [ui](#ui)
        - [comment](#comment)
        - [post](#post)
    - [Further action](#%d0%94%d0%b0%d0%b%1%8c%d0%bd%5%b9%d1%88%d0%b8%d0%b5-%d0%b4%d0%b5%d0%b9%d1%81%d1%82%d0%b2%d0%b8%d1%8f)
      - [performance check](#%d0%9f%d1%80%d0%be%d0%b2%d0%b5%d1%80%d0%ba%d0%b0-%d1%80%d0%b1%d0%be%d1%82%d0%be%d1%81%d0%bf%d0%be%d1%81%d0%b1%d0%b2%d0%b5%d1%80%ba%d0%b0-%d1%81%82%d0%b8)
      - [Creating volume for MongoDB](#%d0%a1%d0%be%d0%b7%d0%b4%d0%b0%d0%b8%d0%b5-volume-%d0%b4%d0%b%d1%8f-mongodb)
    - [src/Makefile](#srcmakefile)
      - [Variables](#%d0%9f%d0%b5%d1%80%d0%b5%d0%bc%d0%b5%d0%bd%d0%bd%1%8b%d0%b5-1)
      - [Goals](#%d0%a6%d0%b5%b5%d0%b%d0%b8-1)
  - [HomeWork 14: Docker: networks, docker-compose](#homework-14-docker-%d1%81%d0%b5%d1%82%d0%b8-docker-compose)
    - [Networking in Docker](#%d0%a0%d0%b0%b1%d0%be%d1%82%d0%b0-%d1%81-%d1%81%d0%b5%d1%82%d1%8f%d0%bc%d0%b8-%d0%b2-docker)
      - [Preparation](#%d0%9f%d0%be%d0%b4%d0%b3%d0%b1%82%d0%be%d0%b2%d0%ba%d0%b0-1)
      - [Networking in Docker](#%d0%a0%d0%b0%b1%d0%be%d1%82%d0%b0-%d1%81-%d1%81%d0%b5%d1%82%d1%8c%d1%8e-%d0%b2-docker)
        - [none](#none)
        - [host](#host)
          - [network namespaces](#network-namespaces)
        - [bridge](#bridge)
          - [Launch the application](#%d0%97%d0%b0%d0%bf%d1%83%d1%81%d0%ba-%d0%bf%d1%80%d0%b8%d0%b%d0%be%d0%b6%d0%b5%d0%bd%d0%b8%d1%8f-1)
          - [Analysis](#%d0%90%d0%bd%d0%b0%b8%d0%b7-1)
    - [Using docker-compose](#%d0%98%d1%81%d0%bf%d0%be%d0%b%d1%8c%d0%b7%d0%be%d0%b2%d0%b0%bd%d0%b8%d0%b5-docker-compose)
      - [Installation](#%d0%a3%d1%81%d1%82%d0%b0%d0%bd%d0%be%d0%b2%d0%ba%d0%b0)
      - [docker-compose.yml](#docker-composeyml)
        - [Environment variables](#%d0%9f%d0%b5%d1%80%d0%b5%d0%bc%d0%b5%d0%bd%d1%8b%d0%b5-%d0%be%d0%ba%d1%80%d1%83%d0%b6%d0%b5%d0%bd%d0%b8%d1%8f)
        - [Project name](#%d0%98%d0%bc%d1%8f-%d0%bf%d1%80%d0%be%d0%b5%d0%ba%d1%82%d0%b0)
    - [Assignment from \*: docker-compose.override.yml](#%d0%97%d0%b0%d0%b4%d0%b0%d0%b8%d0%b5-%d1%81%d0%be-docker-composeoverrideyml).
      - [Analysis](#%d0%90%d0%bd%d0%b0%b8%d0%b7-2)
      - [Implementation](#%d0%a0%d0%b5%d0%b0%b0%b8%d0%b7%d0%b0%d1%86%d0%b8%d1%8f-1)
    - [Outside of tasks](#%d0%92%d0%bd%d0%b5-%d0%b7%d0%b4%d0%b0%d0%b8%d0%b9)
  - [HomeWork 15: Gitlab CI device. Building a Continuous Delivery Process](#homework-15-%d0%a3%d1%81%d1%82%d1%80%d0%be%d0%b9%d1%81%1%82%d0%b2%d0%be-gitlab-ci-%d0%9f%d0%be%1%81%d1%82%d1%80%b5%d0%b5%d0%b8%d0%b5-. %d0%bf%d1%80%d0%be%d1%86%d0%b5%d1%81%81%d0%b0-%d0%bd%d0%b5%d0%bf%d1%80%d0%b5%d1%8b%d0%b2%d0%bd0%be%d0%b9-%d0%bf%d0%be%1%81%d1%82%d0%b0%b2%d0%ba%d0%b8)
    - [Deployment of gitlab](#%d0%a0%b0%b7%d0%b2%d1%91%d1%80%d1%82%d1%8b%d0%b2%d0%b0%d0%bd%d0%b8%d0%b5-gitlab)
      - [Host preparation](#%d0%9f%d0%be%d0%b4%d0%b3%d0%be%d1%82%d0%be%d0%b2%d0%ba%d0%b0-%d1%85%d0%be%d1%81%d1%82%d0%b0)
        - [ansible](#ansible)
        - [packer](#packer-1)
        - [terraform](#terraform-1)
      - [Deployment of gitlab](#%d0%a0%b0%b7%d0%b2%d1%91%d1%80%d1%82%d1%8b%d0%b2%d0%b0%d0%bd%d0%b8%d0%b5-gitlab-1)
      - [Initial setting](#%d0%9f%d0%b5%d1%80%d0%b2%d0%be%d0%bd%d0%b0%d1%87%d0%b0%b%d1%8c%d0%bd%d0%b0%d1%8f-%d0%bD1%81%d1%82%d1%80%d0%be%d0%b9%d0%ba%d0%b0)
        - [Working with the repository via ssh](#%d0%a0%b0%b1%d0%b1%d0%be%1%82%d0%b0-%d1%81-%d1%80%d0%b5%d0%bf%d0%be%d0%b7%d0%b8%d1%82%d0%be%d1%80%d0%b8%d0%b5%bc-%d1%87%d0%b5%d1%80%b5%d0%b7-ssh)
    - [Project creation](#%d0%a1%d0%be%d0%b7%d0%b4%d0%b0%b8%d0%b5-%d0%bf%d1%80%d0%be%d0%b5%d0%ba%d1%82%d0%b0)
      - [CI/CD Pipeline](#cicd-pipeline)
    - [Runner](#runner)
    - [Testing Reddit](#%d0%a2%d0%b5%d1%81%d1%82%d0%b8%d1%80%d0%be%d0%b2%d0%b0%d0%b8%d0%b5-reddit)
    - [Working with environments](#%d0%a0%d0%b0%b1%d0%be%d1%82%d0%b0-%d1%81-%d0%be%d0%ba%d1%80%d1%83%d0%b6%d0%b5%d0%bd%d0%b8%d1%8f%d0%bc%d0%b8)
      - [dev](#dev)
      - [staging and production](#staging-%d0%b8-production)
      - [Dynamic environments] (#%d0%94%d0%b8%d0%bd%d0%b8%d1%87%d0%b5%d1%81%d0%ba%d0%b8%d0%b5-%d0%be%d0%ba%d1%80%d1%83%d0%b6%d0%b5%d0%b8%d1%8f)
    - [Outside of tasks: improvements] (#%d0%92%d0%bd%d0%b5-%d0%b7%d0%b0%d0%b4%d0%b0%b8%d0%b9-%d1%83%d0%b%d1%83%d1%87%d1%88%d0%b0%d0%b%d0%ba%d0%b8)
    - [Assignment from \*: Automated build of the application reddit](#%d0%97%d0%b0%d0%b4%d0%b0%d0%bd%d0%b8%d0%b5-%d1%81%d0%be-- %d0%90%d0%b2%d1%82%d0%be%d0%bc%d0%b0%d1%82%d0%b8%d0%b7%d0%b8%d1%80%d0%be%d0%b2%d0%b0%d0%bd%d0%bd0%b2%d0%bd%d0%b1%8f %d1%81%d0%b1%d0%be%d1%80%d0%ba%d0%b0-%d0%bf%d1%80%d0%b8%d0%b%d0%b6%d0%b5%d0%bd%d0%b8%d1%8f-reddit)
      - [Plan](#%d0%9f%d0%bb%d0%b0%d0%bd)
      - [Implementation](#%d0%a0%d0%b5%d0%b0%b0%b8%d0%b7%d0%b0%d1%86%d0%b8%d1%8f-2)
        - [Adjusting terraform module instance](#%d0%9d%d0%b0%d1%81%d1%82%d1%80%d0%be%d0%b9%d0%ba%d0%b0-terraform-module-instance)
        - [Adjusting the stage environment terraform](#%d0%9d%d0%b0%d1%81%d1%82%d1%80%d0%be%d0%b9%d0%ba%d0%b0-stage-%d0%be%d0%ba%d1%80%d1%83%d0%b6%d0%b5%d0%bd%d0%b8%d1%8f-terraform)
        - [Infrastructure application](#%d0%9f%d1%80%d0%b8%d0%bc%d0%b5-%d0%b8%d0%b8%d0%b5-%d0%b8%d0%bd1%84%d1%80%d0%b0%d1%81%d1%82%d1%80%d1%83%d0%ba%1%82%d%83%d1%8b)
        - [Integration with Let's Encrypt](#%d0%98%d0%bd%1%82%d0%b5%d0%b3%d1%80%d0%b0%d1%86%d0%b8%d1%8f-%d1%81-lets-encrypt)
        - [Setting up image assembly in .gitlab-ci. yml](#%d0%9d%d0%b0%d1%81%d1%82%d1%80%d0%be%d0%b9%d0%ba%d0%b0-%d1%81%d0%b1%d0%be%d1%80%d0%ba%d0%b8-%d0%be%d0%b1%80%b0%b7%d0%be%d0%b2-%d0%b2-gitlab-ciyml)
          - [Trying to solve the problem on the forehead (unsuccessful)](#%d0%9f%d0%be%d0%bf%d1%8b%d1%82%d0%ba%d0%b0- %d1%80%d0%b5%d1%88%d0%b8%d1%82%d1%8c-%d0%b7%d0%b0%d0%b4%d0%b0%d1%87%d1%83-%d0%b2-%d0%b%d0%be%d0%b1-%d0%bd%d0%b5%d1%83%d0%b4%d0%b0%d1%87%d0%bD1%8f)
          - [Analysis](#%d0%90%d0%bd%d0%b0%b8%d0%b7-3)
          - [Host preparation for docker runner](#%d0%9f%d0%be%d0%b4%d0%b3%d0%be%d1%82%d0%be%d0%b2%d0%ba%d0%b0-%d1%85%d0%be%1%81%d1%82%d0%b0-%d0%b4%d0%b%d1%8f-docker-runner)
          - [Prepare docker-runner](#%d0%9f%d0%be%d0%b4%d0%b3%d0%be%d1%82%d0%be%d0%b2%d0%bb%d0%b5%d0%bd-docker-runner)
          - [Automated image assembly](#%d0%90%d0%b2%d1%82%d0%be%d0%bc%d0%b0%d1%82%d0%b8%d0%b7%d0%b8%d1%80%d0%be%d0%b2%d0%b0%d0%b2%d0%bd%d0%bd%d0%bd1%8f %d1%81%d0%b1%d0%be%d1%80%d0%ba%d0%b0-%d0%be%d0%b1%d1%80%d0%b0%b7%d0%be%d0%b2)
        - [Loading images in gitlab registry](#%d0%97%d0%b0%b3%d1%80%d1%83%d0%b7%d0%ba%d0%b0-%d0%be%d0%b1%d1%80%d0%b7%d0%be%d0%b2-%d0%b2-gitlab-registry)
    - [Assignment from \*: Depleted container on the server created for the branch](#%d0%97%d0%b0%d0%b4%d0%b0%d0%b%d0%b8%d0%b5-%d1%81%d0%be-%d0%94%d0%b5%d0%bf%d0%b%d0%be%d0%b9- %d0%ba%d0%be%d0%bd%d1%82%d0%b5%d0%b9%d0%bd%d0%b5%d1%80%d0%b0-%d0%b0-%d1%81%d0%be%d0%b7%d0%b4%d0%b0%d0%bd%d0%b9- %d0%b4%d0%b%d1%8f-%d0%b2%d0%b5%d1%82%d0%ba%d0%b8-%d1%81%d0%b5%d1%80)
      - [Implementation](#%d0%a0%d0%b5%d0%b0%b0%b8%d0%b7%d0%b0%d1%86%d0%b8%d1%8f-3)
        - [Packer](#packer-2)
        - [Terraform](#terraform-2)
        - [Ansible](#ansible-1)
          - [Search for solution](#%d0%9f%d0%be%d0%b8%d1%81%d0%ba-%d1%80%d0%b5%d1%88%d0%b5%d0%bd%d0%b8%d1%8f)
          - [Implementation](#%d0%a0%d0%b5%d0%b0%b0%b8%d0%b7%d0%b0%d1%86%d0%b8%d1%8f-4)
          - [Preparation of gitlab-runner](#%d0%9f%d0%be%d0%b4%d0%b3%d0%be%d1%82%d0%be%d0%b2%d0%ba%d0%b0-gitlab-runner)
          - [Check](#%d0%9f%d1%80%d0%be%d0%b2%d0%b5%d1%80%d0%ba%d0%b0)
          - [Create Environment](#%d0%a1%d0%be%d0%b7%d0%b4%d0%b0%d0%b8%d0%b5-environment)
    - [Assignment from \*: Automated creation and registration of scanners](#%d0%97%d0%b0%d0%b4%d0%b0%d0%b8%d0%b5-. %d1%81%d0%be--%d0%90%d0%b2%d1%82%d0%bey%d0%bc%d0%b0%d1%82%d0%b8%d0%b7%d0%b8%d1%80%d0%bey%d0%b2%d0%b0%d0%b5- %d1%81%d0%be%d0%b7%d0%b4%d0%b0%d0%b8%d0%b5-%d0%b8-%d1%80%d0%b5%d0%b3%d0%b8%d1%81%d1%82%d1%80%d0%b0%d1%86%d0%b8%d1%8f-%d1%80%d0%b2)
      - [Scaling up the rankers](#%d0%9f%d1%80%d0%be%d1%80%d0%b0%b1%d0%be%d1%82%d0%ba%d0%b0 %d1%81%d0%ba%d0%b5%d0%b9%d0%b%d0%b8%d0%bd%d0%b3%d0%b0-%d1%80%d0%b0%d0%b%d0%bd%d0%b5%d1%80%d0%be%d0%b2)
    - [Assignment from \*: Sending notifications about pipeline operation in Slack](#%d0%97%d0%b0%d0%b4%d0%b0%d0%b%d0%b8%d0%b5-%d1%81%d0%be-- %d0%9e%d1%82%d0%bf%d1%80%d0%b0%b2%d0%ba%d0%b0-%d1%83%d0%b2%d0%b5%d0%b4%d0%be%d0%bc%d0%bb%d0%b5-pipeline-%d0%b2-slack)
    - [Passing travis-ci tests] (#%d0%9f%d1%80%d0%be%1%85%d0%be%d0%b6%d0%b4%d0%b5%d0%b%d0%b8%d0%b5-%d1%82%d0%b5%d1%81%d1%82%d0%be%d0%b2-travis-ci)
    - [Other](#%d0%9f%d1%80%d0%be%d1%87%d0%b5%d0%b5)
  - [HomeWork 16: Introduction to monitoring. Monitoring systems. ](#homework-16-%d0%92%d0%b2%d0%b5%d0%b4%d0%b5%d0%bd%d0%b8%d0%b5-%d0%b2-%d0%bc%d0%be%d0%bd%d0%b8%d1%82%d0%be%1%80%d0%b8%d0%b3-. %d0%a1%d0%b8%d1%81%d1%82%d0%b5%d0%bc%1%8b-%d0%bc%d0%be%d0%bd%d0%b8%d1%82%d0%be%d1%80%b8%d0%b3%d0%b0)
    - [Prometheus.] start, configuration, acquaintance with Web UI](#prometheus-%d0%b7%d0%b0%d0%bf%d1%83%d1%81%d0%ba- %d0%ba%d0%be%d0%bd%d1%84%d0%b8%d0%b3%d1%83%d1%80%b0%d1%86%d0%b8%d1%8f-%d0%b7%d0%bd%d0%b0%ba%0%be%d0%bc%d1%81%d1%82%d0%b2%d0%be-%81-web-ui)
      - [Run docker-machine host for prometheus](#%d0%97%d0%b0%d0%bf%d1%83%d1%81%d0%ba-docker-machine-%d1%85%d0%be%d1%81%d1%82%d0%b0-%d0%b4%d0%bb%d1%8f-prometheus)
      - [Launch prometheus](#%d0%97%d0%b0%bf%d1%83%d1%81%d0%ba-prometheus)
      - [Web-interface](#web-%d0%b8%d0%bd%1%82%d0%b5%d1%84%d0%b5%d0%b9%d1%81)
      - [Targets](#targets)
      - [List of metrics](#%d0%a1%d0%bf%d0%b8%d1%81%d0%be%d0%ba-%d0%bc%d0%b5%d1%82%d1%80%d0%b8%d0%ba)
    - [Monitoring of microservices](#%d0%9c%d0%be%d0%bd%d0%b8%d1%82%d0%be%d1%80%d0%b8%d0%b3- %d1%81%d0%be%d1%81%d1%82%d0%be%d1%8f%d0%bd%d0%b8%8f-%d0%bc%d0%b8%d0%ba%d1%81%d0%b5%d1%81%d0%b2%d0%b8%81%d0%be%0%b2)
      - [Re-order directory structure](#%d0%9f%d0%b5%d1%80%d0%b5%d1%83%d0%bf%d0%be%1%80%d1%8f%d0%b4%d0%be%d1%87%d0%b8%d0%bc- %d1%81%d1%82%d1%80%d1%83%d0%ba%d1%82%d1%83%d1%80%d1%83-%d0%b4%d0%b8%d1%80%d0%b5%d0%ba%d1%82%d0%be%1%80%d0%b8%d0%b9)
      - [Creating a Docker image](#%d0%a1%d0%be%d0%b7%d0%b4%d0%b0%d0%b8%d0%b5-docker-%d0%be%d0%b1%d1%80%d0%b0%b7%d0%b0)
      - [Configuration](#%d0%9a%d0%be%d0%bd%1%84%d0%b8%d0%b3%d1%83%d1%80%b0%d1%86%d0%b8%d1%8f)
      - [Create an image](#%d0%a1%d0%be%d0%b7%d0%b4%d0%b0%b55%d0%bc-%d0%be%d0%b1%80%d0%b0%d0%b7)
      - [Microservice images] (#%d0%9e%d0%b1%80%d0%b7%d1%8b-%d0%bc%d0%b8%d0%ba%d1%81%d0%b5%d1%81%d0%b5%d1%80%d0%b2%d0%b8%d1%81%d0%be%0%b2)
      - [Collect images](#%d0%a1%d0%be%d0%b1%d0%b5%d1%80%d0%b5%d0%bc-images)
      - [docker-compose.yml](#docker-composeyml-1)
      - [Launch of microservices](#%d0%97%d0%b0%bf%d1%83%d1%81%d0%ba-%d0%bc%d0%b8%d0%ba%d1%81%d0%b5%d1%80%d0%b2%d0%b8%81%d0%b5%d1%80%d0%b2)
      - [Healthchecks](#healthchecks)
      - [UI service status](#%d0%a1%d0%be%81%d1%82%d0%be%d1%8f%d0%bd%d0%b8%d0%b5-%d1%81%d0%b5%d1%80%d0%b2%d0%b8%81%d0%b0-ui)
      - [Fix docker-machine from another host] [#fix-docker-machine-from-other-host]
      - [UI service status. Continuation](#%d0%a1%d0%be%d1%81%d1%82%d0%be%1%8f%d0%bd%d0%b8%d0%b5-%d1%81%d0%b5%d1%80%d0%b2%d0%b8%d1%81%d0%b0-ui-%d0%9f%d1%80%d0%b4%d0%be%d0%b6%d0%b5%d0%b8%d0%b5)
        - [Checking metrics](#%d0%9f%d1%80%d0%be%d0%b2%d0%b5%d1%80%d0%ba%d0%b0-%d0%bc%d0%b5%d1%82%d1%80%d0%b8%d0%ba)
        - [Finding the problem](#%d0%9f%d0%be%d0%b8%d1%81%d0%ba-%d0%bf%d1%80%d0%be%d0%b1%d0%b1%d0%b5%d0%bc%d1%8b)
        - [Independently](#%d0%a1%d0%b0%d0%bc%d0%be%d1%81%d1%82%d0%be%d1%8f%d1%82%d0%b5%d0%bb%d1%8c%d0%bd%d0%d0%be)
        - [Re-creation of docker-machine](#%d0%9f%d0%b5%d1%81%d0%be%d0%b7%d0%b4%d0%b0%d0%b8%d0%b5-docker-machine)
    - [Collect host metrics using exporter](#%d0%a1%d0%b1%d0%be%d1%80-%d0%bc%d0%b5%d1%82%d1%80%d0%b8%d0%ba- %d1%85%d0%be%d1%81%d1%82%d0%b0-%d1%81-%d0%b8%d1%81%d0%bf%d0%bey%d0%b%d1%8c%d0%b7%d0%bey%d0%b2%d0%b0)
      - [Node exporter](#node-exporter)
      - [docker-compose.yml](#docker-composeyml-2)
      - [Extra: parameterize the versions of the images](#%d0%94%d0%be%d0%bf%d0%be%d0%bb%d0%b%d0%b8%d1%82%d0%b5%d0%b%d1%8c%d0%bd%d0%be- %d0%bf%d0%b0%d1%80%d0%b0%bc%d0%b5%d1%82%d1%80%b8%d0%b7%d1%83%d0%b5%d0%bc-%d0%b2%d0%b5%d1%81%d0%b8%d0%b8-%d0%be%d0%b1%80%d0%b7%d0%b2)
      - [Optional: Makefile target build_prometheus] (#%d0%94%d0%be%d0%bf%d0%be%d0%b%d0%b%d0%b8%d1%82%d0%b5%d0%b%d1%8c%d0%bd%d0%be-makefile-target-buildprometheus)
      - [prometheus.yml](#prometheusyml)
      - [Re-create our services] (#%d0%9f%d0%b5%d1%81%d0%be%d0%b7%d0%b4%d0%b0%d0%b4%d0%b8%d0%bc-%d0%bd%d0%b0%d1%88%d0%b8-%d1%81%d0%b5%d1%81%81%d0%b5%d2%d0%b8%d1%81%b)
      - [Receiving information](#%d0%9f%d0%be%d0%bb%d1%83%d1%87%d0%b5%d0%bd%d0%b8%d0%b5-%d0%b8%d0%bd%d1%84%d0%be%1%80%d0%bc%d0%b0%d1%86%d0%b8%d0%b8)
    - [Completion](#%d0%97%d0%b0%d0%b2%d0%b5%d1%8%d0%b5%d0%b8%d0%b5-%d1%80%d0%b0%d0%b1%d0%be%d1%82%d1%8b)
      - [Makefile](#makefile-targets)
      - [Push images](#%d0%9f%d1%83%d1%88%d0%b8%d0%bc-%d0%be%d0%b1%d1%80%d0%b0%d0%b7%d1%8b)
    - [Tasks from \*](#%d0%97%d0%b0%d0%b4%d0%b0%b8%d1%8f-%d1%81%d0%be)
      - [MongoDB exporter](#mongodb-exporter)
        - [Installation](#%d0%a3%d1%81%d1%82%d0%b0%d0%bd%d0%be%d0%b2%d0%ba%d0%b0-1)
      - [Cloudprober](#cloudprober)
        - [Implementation](#%d0%a0%d0%b5%d0%b0%b0%b8%d0%b7%d0%b0%d1%86%d0%b8%d1%8f-5)
      - [Makefile](#makefile-1)
    - [Project Launch](#%d0%97%d0%b0%d0%bf%d1%83%d1%81%d0%ba-%d0%bf%d1%80%d0%be%d0%b5%d0%ba%1%82%d0%b0)
      - [Preparation](#%d0%9f%d0%be%d0%b4%d0%b3%d0%b1%82%d0%be%d0%b2%d0%ba%d0%b0-2)
      - [Project Launch](#%d0%97%d0%b0%d0%bf%d1%83%d1%81%d0%ba-%d0%bf%d1%80%d0%be%d0%b5%d0%ba%1%82%d0%b0-1)
  - [HomeWork 17: Application and Infrastructure Monitoring](#homework-17-%d0%9c%d0%be%d0%bd%d0%b8%d1%82%d0%be%1%80%d0%b8%d0%b3- %d0%bf%d1%80%d0%b8%d0%b%d0%be%d0%b6%d0%b5%d0%bd%d0%b8%d1%8f-%d0%b8-%d0%b8%d0%bd1%84%d1%80%d0%b0%d1%81%d1%82%d1%80%d1%83%d0%ba%d1%82%d1%83%d1%8b)
    - [Plan](#%d0%9f%d0%bb%d0%b0%bd-1)
    - [Container Docker Monitoring](#%d0%9c%d0%be%d0%bd%d0%b8%d1%82%d0%be%d1%80%d0%b8%d0%b3-docker-%d0%ba%d0%be%d0%bd%d1%82%d0%b5%d0%b9%d0%bd%d0%b5%d1%80%d0%b2)
      - [Environment preparation](#%d0%9f%d0%be%d0%b4%d0%b3%d0%be%1%82%d0%be%d0%b2%d0%ba%d0%b0-%d0%be%d0%ba%d1%80%d1%83%d0%b6%d0%b5%d0%bd%d0%b8%d1%8f)
      - [Container Docker Monitoring](#%d0%9c%d0%be%d0%bd%d0%b8%d1%82%d0%be%d1%80%d0%b8%d0%b3-docker-%d0%ba%d0%be%d0%bd%d1%82%d0%b5%d0%b9%d0%bd%d0%b5%d1%80%d0%b2-1)
      - [cAdvisor](#cadvisor)
      - [File docker-compose-monitoring.yml](#%d0%a4%d0%b0%b9%d0%b-docker-compose-monitoringyml)
      - [File prometheus.yml](#%d0%a4%d0%b0%b9%d0%b-prometheusyml)
      - [cAdvisor UI](#cadvisor-ui)
    - [Metrics visualization: Grafana](#%d0%92%d0%b8%d0%b7%d1%83%d0%b0%b8%d0%b7%d0%b0%d1%86%d0%b8%d1%8f-%d0%bc%d0%b5%d1%82%d1%80%d0%b8%d0%ba-grafana)
      - [Grafana: Web UI](#grafana-web-ui)
      - [Grafana: Adding a data source](#grafana-%d0%94%d0%be%d0%b1%d0%b1%d0%b2%d0%b%d0%b5%d0%b8%d0%b5-%d0%b8%d1%81%d1%82%d0%be%d1%87%d0%bd%d0%b8%d0%ba%d0%b0-%d0%b4%d0%b0%d%d0%b1%85)
      - [Dashboards](#%d0%94%d0%b0%d1%88%d0%b1%d0%be%d1%8b)
      - [Import of dashboard](#%d0%98%d0%bc%d0%bf%d0%be%d1%80%d1%82-%d0%b4%d0%b0%d1%88%d0%b1%d0%be%d1%80%d0%b4%d0%b0)
    - [Collection of application metrics] (#%d0%a1%d0%b1%d0%be%d1%80-%d0%bc%d0%b5%d1%82%d1%80%d0%b8%d0%ba-%d1%80%d0%b0%b1%d0%be%1%82%d1%8b-%d0%bf%d1%80%d0%b8%d0%bb6%d0%b5%d0%b8%d1%8f)
      - [Why?](#%d0%97%d0%b0%d1%87%d0%b5%d0%bc)
      - [prometheus.yml](#prometheusyml-1)
      - [Creating a dashboard in Grafana](#%d0%a1%d0%be%d0%b7%d0%b4%d0%b0%d0%b8%d0%b5-%d0%b4%d0%b0%d1%88%d0%b1%d0%be%d1%80%d0%b4%d0%b0-%d0%b2-grafana)
      - [Independently](#%d0%a1%d0%b0%d0%bc%d0%be%d1%81%d1%82%d0%be%d1%8f%d1%82%d0%b5%d0%bb%d1%8c%d0%bd%d0%be-1)
      - [Histogram](#%d0%93%d0%b8%d1%81%d1%82%d0%be%d0%b3%d1%80%d0%b0%c%d0%bc%d0%b0)
      - [Histogram metrics](#histogram-%d0%bc%d0%b5%d1%82%d1%80%d0%b8%d0%ba%d0%b0)
      - [Percentage](#%d0%9f%d1%80%d0%be%d1%86%d0%b5%d0%bd%1%82%d0%b8%d0%b%d1%8c)
        - [Example percentile](#%d0%9f%d1%80%d0%b8%d0%bc%d0%b5%d1%80-%d0%bf%d1%80%d0%be%d1%86%d0%b5%d0%bd%1%82%d0%b8%d0%bb%1%8c)
        - [95th percentile](#95-%d0%b9-%d0%bf%d1%80%d0%be%1%86%d0%b5%d0%bd%1%82%d0%b8%d0%b%d1%8c)
    - [Collecting business logic metrics](#%d0%a1%d0%b1%d0%be%d1%80-%d0%bc%d0%b5%d1%82%d1%80%d0%b8%d0%ba-%d0%b1%d0%b8%d0%b7%d0%bd%d0%b5%d1%81%d0%b%d0%be%d0%b3%d0%b8%d0%ba%d0%b8)
    - [Setting up and checking for allergies](#%d0%9d%d0%b0%d1%81%d1%82%d1%80%d0%be%d0%b9%d0%ba%d0%b0 %d0%b8-%d0%bf%d1%80%d0%be%d0%b2%d0%b5%d1%80%d0%ba%d0%b0-%d0%b0%b%d0%b5%d1%80%d1%82%d0%b8%d0%b3%d0%b0)
      - [Allergen Rules](#%d0%9f%d1%80%d0%b0%d0%b2%d0%b8%d0%b%d0%b0-%d0%b0%b%d0%b5%d1%80%d1%82%d0%b8%d0%b3%d0%b0)
      - [Alertmanager](#alertmanager)
      - [Alert rules] [#alert-rules]
      - [prometheus.yml](#prometheusyml-2)
      - [Push slack api url to github ERROR] (#push-slack-api-url-to-github-error)
      - [Alert check](#%d0%9f%d1%80%d0%be%d0%b2%d0%b5%d1%80%d0%ba%d0%b0-%d0%b0%b5%d1%80%d1%82%d0%b0)
      - [Fix slack](#%d0%a7%d0%b8%d0%bd%d0%b8%d0%bc-slack)
        - [Implementation](#%d0%a0%d0%b5%d0%b0%b0%b8%d0%b7%d0%b0%d1%86%d0%b8%d1%8f-6)
      - [Alert check](#%d0%9f%d1%80%d0%be%d0%b2%d0%b5%d1%80%d0%ba%d0%b0-%d0%b0%b5%d1%80%d1%82%d0%b0-1)
    - [Completion](#%d0%97%d0%b0%d0%b2%d0%b5%d1%8%d0%b5%d0%b8%d0%b5-%d1%80%d0%b0%d0%b1%d0%be%1%82%d1%8b-1)
    - [Project Launch](#%d0%97%d0%b0%d0%bf%d1%83%d1%81%d0%ba-%d0%bf%d1%80%d0%be%d0%b5%d0%ba%1%82%d0%b0-2)
      - [Preparation](#%d0%9f%d0%be%d0%b4%d0%b3%d0%b1%82%d0%be%d0%b2%d0%ba%d0%b0-3)
      - [Project Launch](#%d0%97%d0%b0%d0%bf%d1%83%d1%81%d0%ba-%d0%bf%d1%80%d0%be%d0%b5%d0%ba%1%82%d0%b0-3)
    - [Fix travis-ci test] [#fix-travis-ci-test]
    - [Tasks from \*](#%d0%97%d0%b0%d0%b4%d0%b0%b8%d1%8f-%d1%81%d0%be-1)
      - [Makefile](#makefile-2)
      - [Collecting metrics with docker](#%d0%a1%d0%b1%d0%be%d1%80-%d0%bc%d0%b5%d1%82%d1%80%d0%b8%d0%ba-%d1%81-docker)
      - [Telegraf](#telegraf)
      - [Alertmanager email] [#alertmanager-email]
    - [Tasks from \*\*](#%d0%97%d0%b0%d0%b4%d0%b0%d0%b8%d1%8f-%d1%81)
      - [Grafana automatic deployment](#%d0%90%d0%b2%d1%82%d0%be%d0%bc%d0%b0%d1%82%d0%b8%d1%87%d0%b5%d1%81%d0%ba%d0%be%d0%b5- %d1%80%d0%b0%d0%b7%d0%b2%d1%91%d1%80%d1%82%d1%8b%d0%b2%d0%b0%d0%b%d0%b8%d0%b5-grafana)
      - [Stackdriver](#stackdriver)
      - [Your metrics](#%d0%a1%d0%b2%d0%be%d0%b8-%d0%bc%d0%b5%d1%82%d1%80%d0%b8%d0%ba%d0%b8)
    - [Tasks from \*\*\*](#%d0%97%d0%b0%d0%b4%d0%b0%d0%b%d0%b8%d1%8f-%d1%81%d0%be-2)
      - [Tickster](#tickster)
      - [Automatic problem correction](#%d0%90%d0%b2%d1%82%d0%be%d0%bc%d0%b0%d1%82%d0%b8%d1%87%d0%b5%d1%81%d0%ba%d0%be%d0%b5- %d0%b8%d1%81%d0%bf%d1%80%d0%b0%d0%b2%d0%bb%d0%b5%d0%bd%d0%b8%d0%b5-%d0%bf%d1%80%d0%be%d0%b1%d0%bb%d0%b5%bc)
  - [HomeWork 18: Logging and Distributed Trace](#homework-18-%d0%9b%d0%be%d0%b3%d0%b8%d1%80%d0%be%d0%b2%d0%d0%b2%d0%bd%d0%b8%d0%b5- %d0%b8-%d1%81%d0%bf%1%81%d0%bf%1%80%b5%d0%b4%d0%b5%d0%b5%d0%b5%d0%bd%d0%b0%8f-%d1%82%d1%80%d0%b0%1%81%d0%b8%1%81%d0%b8%80%d0%b2%d0%b0)
    - [Plan](#%d0%9f%d0%bb%d0%b0%d0%bd-2)
    - [Preparation](#%d0%9f%d0%be%d0%b4%d0%b3%d0%b1%82%d0%be%d0%b2%d0%ba%d0%b0-4)
      - [Environment preparation](#%d0%9f%d0%be%d0%b4%d0%b3%d0%be%d1%82%d0%be%d0%b2%d0%ba%d0%b0-%d0%be%d0%ba%d1%80%d1%83%d0%b6%d0%b5%d0%bd%d0%b8%d1%8f-1)
    - [Docker container logging](#%d0%9b%d0%be%d0%b3%d0%b8%d1%80%d0%be%d0%b2%d0%b0%d0%b8%d0%b5-docker-%d0%ba%d0%be%d0%bd1%82%d0%b5%d0%b9%d0%bd%d0%b5%d1%80%d0%b2)
      - [Elastic Stack] [#elastic-stack]
      - [docker-compose-logging.yml](#docker-compose-loggingyml)
      - [Fluentd](#fluentd)
    - [Structured logs] (#%d0%a1%d1%82%d1%80%d1%83%d0%ba%1%82%d1%83%d1%80%d0%b8%d1%80%d0%be%d0%b2%d0%b0%d0%bD1%8b%d0%b5-%d0%b%d0%b3%d0%b8)
      - [Sending logs to Fluentd](#%d0%9e%d1%82%d0%bf%d1%80%d0%b0%b2%d0%ba%d0%b0-%d0%b%d0%be%d0%b3%d0%be%d0%b2-%d0%b2%d0%be-fluentd)
      - [Collection of Post service logs](#%d0%a1%d0%b1%d0%be%d1%80-%d0%bb%d0%be%d0%b3%d0%be%d0%b2-post-%d1%81%d0%b5%d1%80%d0%b2%d0%b8%81%d0%b0)
      - [Kibana](#kibana)
        - [memory locking requested for elasticsearch process but memory is not locked](#memory-locking-requested-for-elasticsearch-process-but-memory-is-not-locked)
        - [Kibana continuation](#kibana-%d0%bf%d1%80%d0%be%d0%b4%d0%be%d0%b%d0%b6%d0%b5%d0%bd%d0%b8%d0%b5)
      - [Filters](#%d0%a4%d0%b8%d0%bb%d1%8c%d1%82%d1%80%d1%8b)
    - [Unstructured Logs] (#%d0%9d%d0%b5%d1%81%d1%82%d1%80%d1%83%d0%ba%d1%82%d1%83%d1%80%d0%b8%d1%80%d0%be%d0%b2%d0%b2%d0%b0%bd%d0%b3%d0%b8)
      - [UI service login](#%d0%9b%d0%be%d0%b3%d0%b8%d1%80%d0%be%d0%b2%d0%b0%d0%b8%d0%b5-ui-%d1%81%d0%b5%d1%80%d0%b2%d0%b8%81%d0%b0)
    - [Parsing](#%d0%9f%d0%b0%d1%81%d0%b8%d0%b8%d0%b3)
      - [Restart logging] (#%d0%9f%d0%b5%d1%80%d0%b5%b7%d0%b0%d0%bf%1%83%d1%81%d0%ba%d0%b0%d0%b5%d0%bc-%d0%bb%d0%be%d0%b3%d0%b3%d0%b8%d0%b3)
      - [Parsing](#%d0%9f%d0%b0%d1%81%d0%b8%d0%b8%d0%bd%d0%b3-1)
    - [Tasks co *](#%d0%97%d0%b0%d0%b4%d0%b0%d0%b8%d1%8f-co)
      - [grok](#grok)
        - [Analysis](#%d0%90%d0%bd%d0%b0%b8%d0%b7-4)
        - [Implementation](#%d0%a0%d0%b5%d0%b0%b0%b8%d0%b7%d0%b0%d1%86%d0%b8%d1%8f-7)
    - [Distributed tracings] (#%d0%a0%d0%b0%d1%81%d0%bf%d1%80%d0%b5%d0%b4%d0%b5%d0%b%d0%b5%b5%d0%bd%d0%bd1%8f-%d1%82%d1%80%d0%b0%d1%81%d0%b8%8%80%d0%be%d0%b2%d0%ba%d0%b0)
      - [Zipkin](#zipkin)
      - [docker-compose.yml](#docker-composeyml-3)
      - [Networks](#networks)
      - [Re-create our services] (#%d0%9f%d0%b5%d1%81%d0%be%d0%b7%d0%b4%d0%b0%d0%b4%d0%b8%d0%bc-%d0%bd%d0%b0%d1%88%d0%b8-%d1%81%d0%b5%d1%81%81%d0%b2%d0%b8%d1%81%b-1)
    - [Outside of tasks: problems with comment] (#%d0%92%d0%bd%d0%b5-%d0%b7%d0%b0%d0%b4%d0%b0%bd%d0%b8%d0%b9-%d0%bf%d1%80%d0%be%d0%b1%d0%bb%d0%b5%d0%bc%1%8b-%81-comment)
    - [Separate job with asterisk \*](#%d0%a1%d0%b0%d0%bc%d0%be%d1%81%d1%82%d0%be%1%8f%d1%82%d0%b5%d0%b%1%8c%d0%bd%0%be%d0%b5- %d0%b7%d0%b0%d0%b4%d0%b0%b8%d0%b5-%d1%81%d0%be-%d0%b7%d0%b2%d0%b5%d0%b7%d0%b4%d0%be%d1%87%d0%ba%d0%be%d0%b9)
      - [Repository](#%d0%a0%d0%b5%d0%bf%d0%be%d0%b7%d0%b8%d1%82%d0%be%1%80%d0%b8%d0%b9)
      - [The problem](#%d0%9f%d1%80%d0%be%d0%b1%d0%b1%d0%b%d0%b5%d0%bc%d0%b0)
      - [Finding the problem](#%d0%9f%d0%be%d0%b8%d1%81%d0%ba-%d0%bf%d1%80%d0%be%d0%b1%d0%b1%d0%b5%d0%bc%d1%8b-1)
      - [Problem with EFK](#%d0%9f%d1%80%d0%be%d0%b1%d0%bb%d0%b5%d0%bc%d0%b0-%d1%81-efk)
    - [How to launch the project:](#%d0%9a%d0%b0%ba-%d0%b7%d0%b0%b0%bf%d1%83%d1%81%d1%82%d0%b8%d1%82%d1%8c-%d0%bf%d1%80%d0%bbe%d0%b5%d0%ba%d1%82)
      - [Preparation](#%d0%9f%d0%be%d0%b4%d0%b3%d0%b1%82%d0%be%d0%b2%d0%ba%d0%b0-5)
      - [Launch](#%d0%97%d0%b0%d0%bf%d1%83%d1%81%d0%ba-1)
  - [HomeWork 19: Introduction to Kubernetes](#homework-19-%d0%92%d0%b2%d0%b5%d0%b4%d0%b5%d0%b%d0%b8%d0%b5-%d0%b2-kubernetes)
    - [Creating primitives](#%d0%a1%d0%be%d0%b7%d0%b4%d0%b0%b8%d0%b5-%d0%bf%d1%80%d0%b8%d0%bc%d0%b8%d1%82%d0%b8%d0%b2%d0%be%d0%b2)
    - [Assignment](#%d0%97%d0%b0%d0%b4%d0%b0%d0%b8%d0%b5)
    - [Kubernetes The Hard Way] [#kubernetes-the-hard-way]
    - [Assignment](#%d0%97%d0%b0%d0%b4%d0%b0%d0%b8%d0%b5-1)
    - [Possible problems](#%d0%92%d0%be%d0%b7%d0%bc%d0%b6%d0%bd%1%8b%d0%b5-%d0%bf%d1%80%d0%be%d0%b1%d0%bb%d0%b5%d0%bc%1%8b)
    - [Assignment from \*](#%d0%97%d0%b0%d0%b4%d0%b0%b8%d0%b5-%d1%81%d0%be)
    - [Job performance](#%d0%92%d1%8b%d0%bf%d0%be%d0%bb%d0%b5%d0%b8%d0%b5-%d0%b7%d0%b0%d0%b4%d0%b0%d0%b8%d1%8f)
    - [Deployments check] (#%d0%9f%d1%80%d0%be%d0%b2%d0%b5%d1%80%d0%ba%d0%b0-%d0%b4%d0%b5%d0%bf%d0%b%d0%b%d0%be%d1%8f)
  - [HomeWork 20: Kubernetes. Starting cluster and application. Security model. ](#homework-20-kubernetes-%d0%97%d0%b0%d0%bf%d1%83%d1%81%d0%ba-%d0%ba%d0%b%d0%b0%d1%81%d1%82%d0%b5%d1%80%d0%b0-%d0%b8- %d0%bf%d1%80%d0%b8%d0%b%d0%be%d0%b6%d0%b5%d0%bd%d0%b8%d1%8f-%d0%9c%d0%be%d0%b4%d0%b5%d0%bb%1%8c-%d0%b1%d0%b5%d0%b7%d0%be%d0%bf%d0%b0%d1%81%d0%bd%d0%be%81%d1%82%d0%b8)
    - [Plan](#%d0%9f%d0%bb%d0%b0%b0-3)
    - [Deploy Kubernetes locally] (#%d0%a0%b0%b7%d0%b2%d0%be%d1%80%b0%d1%87%d0%b8%d0%b2%d0%b0%b5%d0%bc-kubernetes-%d0%bb%d0%be%d0%ba%d0%b0%d0%b%1%8c%d0%bd%d0%be)
      - [Kubectl](#kubectl)
      - [minikube](#minikube)
    - [Minikube](#minikube-1)
      - [Before you begin](#before-you-begin)
      - [Installing minikube](#installing-minikube)
      - [Kubectl](#kubectl-1)
      - [Run the application] (#%d0%97%d0%b0%d0%bf%d1%83%d1%81%d1%82%d0%b8%d0%bc-%d0%bf%d1%80%d0%b8%d0%b%d0%be%d0%b6%d0%b5%d0%bd%d0%b8%d0%b5)
        - [Deployment](#deployment)
          - [UI](#ui-1)
          - [Comment](#comment-1)
          - [Post](#post-1)
          - [MongoDB](#mongodb)
      - [Services](#services)
        - [Assignment](#%d0%97%d0%b0%d0%b4%d0%b0%d0%b8%d0%b5-2)
        - [Services](#services-1)
      - [Minikube](#minikube-2)
      - [Namespaces](#namespaces)
      - [Dashboard](#dashboard)
    - [Deploy Kubernetes] (#%d0%a0%b0%b7%d0%b2%d0%be%d1%80%b0%d1%87%d0%b8%d0%b2%d0%b0%d0%b5%d0%bc-kubernetes)
    - [GKE](#gke)
      - [ERROR: No comments displayed](#%d0%9e%d0%a8%d0%98%d0%91%d0%9a%d0%90-%d0%9d%d0%b5-%d0%be%d1%82%d0%be%d0%b1%d1%80%b0%d0%b6%d0%b0%d1%8e%d1%82%d1%81%d1%8f-%d0%ba%d0%be%d0%bc%d0%bc%5%d0%bd%1%82%d1%8b)
    - [Assignment](#%d0%97%d0%b0%d0%b4%d0%b0%d0%b8%d0%b5-3)
    - [GKE Dashboard](#gke-dashboard)
    - [Assignment from \*](#%d0%97%d0%b0%d0%b4%d0%b0%b8%d0%b5-%d1%81%d0%be-1)
  - [HomeWork 21: Kubernetes. Networks, Storages](#homework-21-kubernetes-networks-storages)
    - [Plan](#%d0%9f%d0%bb%d0%b0%d0%bd-4)
    - [Network Interaction](#%d0%a1%d0%b5%d1%82%d0%b5%d0%b2%d0%be%d0%b5-%d0%b2%d0%b7%d0%b7%d0%b8%d0%bc%d0%be%d0%b4%d0%b5%d0%b9%d1%81%d1%82%d0%b2%d0%b8%d0%b5)
      - [Service](#service)
      - [Kube-dns] [#kube-dns]
      - [Service](#service-1)
      - [kube-dns](#kube-dns-1)
        - [And within the cluster?](#%d0%90-%d0%b2-%d1%80%d0%b0%bc%d0%ba%d0%b0%1%85-%d0%ba%d0%bb%d0%b0%d1%81%d1%82%d0%b5%d1%80%d0%b0).
      - [kubenet](#kubenet)
        - [And within the cluster?](#%d0%90-%d0%b2-%d1%80%d0%b0%bc%d0%ba%d0%b0%1%85-%d0%ba%d0%bb%d0%b0%d1%81%d1%82%d0%b5%d1%80%d0%b0-1)
      - [nodePort](#nodeport)
      - [LoadBalancer](#loadbalancer)
      - [Ingress](#ingress)
        - [Ingress Conroller] [#ingress-conroller]
        - [Ingress](#ingress-1)
      - [Secret](#secret)
        - [TLS Termination](#tls-termination)
      - [Assignment from \* Secret as a Kubernetes Manifesto](#%d0%97%d0%b0%d0%b4%d0%b0%d0%b8%d0%b5- %d1%81%d0%be-secret-%d0%b2-%d0%b2%d0%b8%d0%b4%d0%b5-kubernetes-%d0%bc%d0%bc%d0%b0)
        - [Analysis](#%d0%90%d0%bd%d0%b0%b8%d0%b7-5)
        - [Implementation](#%d0%a0%d0%b5%d0%b0%b0%b8%d0%b7%d0%b0%d1%86%d0%b8%d1%8f-8)
      - [Network Policy](#network-policy)
        - [Assignment](#%d0%97%d0%b0%d0%b4%d0%b0%d0%b8%d0%b5-4)
    - [Storage for the base](#%d0%a5%d1%80%d0%b0%b%d0%b8%d0%b8%d1%89%d0%b5-%d0%b4%d0%b%d1%8f-%d0%b1%d0%b0%d0%b7%d1%8b)
      - [Volume](#volume-1)
      - [PersistentVolume](#persistentvolume)
      - [PersistentVolumeClaim](#persistentvolumeclaim)
      - [PersistentVolume](#persistentvolume-1)
      - [PersistentVolumeClaim](#persistentvolumeclaim-1)
      - [Connect PVC to our Pods](#%d0%9f%d0%be%d0%b4%d0%ba%d0%bb%d1%8e%d1%87%d0%b8%d0%bc-pvc-%d0%ba-%d0%bd%d0%b0%d1%88%d0%b8%d0%b8%d0%bc-pod%c)
      - [Dynamic Volume Allocation](#%d0%94%d0%b8%d0%bd%d0%bc%d0%b8%d1%87%d0%b5%d1%81%d0%ba%d0%be%d0%b5-%d0%b2%d1%8b%d0%b4%d0%b5%d0%b%d0%b5-volume%d0%b2)
      - [StorageClass](#storageclass)
      - [PVC + StorageClass](#pvc--storageclass)
      - [Dynamic PVC Connection](#%d0%9f%d0%be%d0%b4%d0%ba%d0%bb%1%8e%d1%87%d0%b5%d0%b%d0%b8%d0%b5-%d0%b4%d0%b8%d0%b8%d0%bc%d0%b8%d1%87%d0%b5%d1%81%d0%ba%d0%b3%d0%be-pvc)
    - [How to launch](#%d0%9a%d0%b0%d0%ba-%d0%b7%d0%b0%bf%d1%83%d1%81%d1%82%d0%b8%d1%82%d1%8c)
      - [Hands](#%d0%a0%d1%83%d0%ba%d0%b0%bc%d0%b8)
      - [./kubernetes/Makefile](#kubernetesmakefile)
        - [Variables](#variables)
        - [Targets](#targets-1)
  - [HomeWork 22: CI/CD in Kubernetes](#homework-22-cicd-%d0%b2-kubernetes)
    - [Plan](#%d0%9f%d0%bb%d0%b0%b0-5)
    - [Helm](#helm)
      - [Helm - installation](#helm---%d1%83%d1%81%d1%82%d0%b0%bd%0%be%d0%b2%d0%ba%d0%b0)
      - [Charts](#charts)
      - [Templates](#templates)
        - [Post](#post-2)
        - [Comment](#comment-2)
        - [Helpers](#helpers)
        - [Assignment](#%d0%97%d0%b0%d0%b4%d0%b0%d0%b8%d0%b5-5)
      - [Dependencies management](#%d0%a3%d0%bf%d1%80%b0%b2%d0%bb%d0%b5%d0%b8%d0%b5-%d0%b7%d0%b0%b2%d0%b8%d1%81%d0%b8%d0%bc%d0%be%1%81%d1%82%d1%8f%d0%bc%d0%b8)
      - [helm2 tiller plugin](#helm2-tiller-plugin)
      - [Helm3](#helm3)
    - [GitLab + Kubernetes](#gitlab--kubernetes)
      - [Install GitLab](#%d0%a3%d1%81%d1%82%d0%b0%bd%d0%be%d0%b2%d0%b8%d0%bc-gitlab)
      - [Launch the project](#%d0%97%d0%b0%bf%d1%83%d1%81%d1%82%d0%b8%d0%bc-%d0%bf%d1%80%d0%be%d0%b5%d0%ba%d1%82)
        - [ui](#ui-2)
        - [comment](#comment-3)
        - [post](#post-3)
        - [reddit-deploy](#reddit-deploy)
      - [Customize CI](#%d0%9d%d0%b0%d1%81%d1%82%d1%80%d0%be%d0%b8%d0%bc-ci)
        - [ui](#ui-3)
        - [comment](#comment-4)
        - [post](#post-4)
        - [feature-branch](#feature-branch)
          - [For `post`](#%d0%94%d0%bb%d1%8f-post)
          - [comment](#comment-5)
      - [Deploym](#%d0%94%d0%b5%d0%bf%d0%b%d0%be%d0%b8%d0%bc)
      - [Pipeline of a healthy person](#%d0%9f%d0%b0%b9%d0%bf%d0%bb%d0%b0%d0%b9%d0%bd-%d0%b7%d0%b4%d0%be%d1%80%d0%be%d0%b2%d0%be%d0%b3%d0%be-%d1%87%d0%b5%d0%b2%d0%b2%d0%b0)
      - [Evicted](#evicted)
      - [Pipeline is a healthy man.] task](#%d0%9f%d0%b0%d0%b9%d0%bf%d0%b%d0%b9%d0%bd-%d0%b7%d0%b4%d0%be%d1%80%d0%be%d0%b2%d0%be%d0%b3%d0%be- %d1%87%d0%b5%d0%b%d0%be%d0%b2%d0%b5%d0%ba%d0%b0-%d0%b7%d0%b0%b4%d0%b0%d0%b8%d0%b5)
        - [Optimize the Pipeline ui](#%d0%9e%d0%bf%d1%82%d0%b8%d0%bc%d0%b8%d0%b7%d0%b8%d1%80%d1%83%d0%b5%bc-%d0%bc-%d0%bf%d0%b0%b9%d0%bf%d0%b0%b9%d0%bb9%d0%bd-ui)
        - [comment + tiller plugin](#comment-tiller-plugin)
        - [post + helm3](#post--helm3)
        - [reddit-deploy](#reddit-deploy-1)
    - [Assignment from \*: Automatic deposition production](#%d0%97%d0%b0%d0%b4%d0%b0%d0%b8%d0%b5-%d1%81%d0%be-- %d0%90%d0%b2%d1%82%d0%be%d0%bc%d0%b1%82%d0%b8%d1%87%d0%b5%d1%81%d0%ba%d0%b8%d0%b9-%d0%b4%d0%b5%d0%bf%d0%bb%d0%be%d0%b9-production)
    - [Completion](#%d0%97%d0%b0%d0%b2%d0%b5%d1%8%d0%b5%d0%b8%d0%b5)
  - [HomeWork 23: Kubernetes.] Monitoring and Logging](#homework-23-kubernetes-%d0%9c%d0%be%d0%bd%d0%b8%d1%82%d0%be%1%80%d0%b8%d0%b3%d0%b8-%d0%b8-%d0%b%d0%be%d0%b3%d0%b8%d1%80%d0%b2%d0%b5)
    - [Preparation](#%d0%9f%d0%be%d0%b4%d0%b3%d0%b1%82%d0%be%d0%b2%d0%ba%d0%b0-6)
      - [Setting up the infrastructure](#%d0%9d%d0%b0%d1%81%d1%82%d1%80%d0%be%d0%b9%d0%ba%d0%b0-%d0%b8%d0%b8%d1%84%d1%80%b0%d1%81%d1%82%d1%80%d1%83%d0%ba%1%82%d1%83%d1%80%d1%8b)
      - [Installing nginx-ingress-controller](#%d0%a3%d1%81%d1%82%d0%b0%d0%bd%d0%be%d0%b2%d0%ba%d0%b0-nginx-ingress-controller)
        - [ERS path](#%d0%9f%d1%83%d1%82%d1%8c-%d0%94%d0%97)
        - [Path terraform](#%d0%9f%d1%83%d1%82%d1%8c-terraform)
    - [Plan](#%d0%9f%d0%bb%d0%b0%bd-6)
    - [Monitoring](#%d0%9c%d0%be%d0%bd%d0%b8%d1%82%d0%be%d1%80%d0%b8%d0%bd%d0%b3)
      - [Stack](#%d0%a1%d1%82%d0%b5%d0%ba)
      - [Install Prometheus](#%d0%a3%d1%81%d1%82%d0%b0%d0%bd%d0%be%d0%b2%d0%b8%d0%bc-prometheus)
      - [Targets](#targets-2)
      - [Relabel config](#relabel-config)
      - [Metrics](#metrics)
        - [Assignment](#%d0%97%d0%b0%d0%b4%d0%b0%d0%b8%d0%b5-6)
      - [Application Metrics](#%d0%9c%d0%b5%d1%82%d1%80%d0%b8%d0%ba%d0%b8-%d0%bf%d1%80%d0%b8%d0%b%d0%be%d0%b6%d0%b5%d0%bd%d0%b9)
        - [Assignment](#%d0%97%d0%b0%d0%b4%d0%b0%d0%b8%d0%b5-7)
      - [Visualization](#%d0%92%d0%b8%d0%b7%d1%83%d0%b0%b8%d0%b7%d0%b0%d1%86%d0%b8%d1%8f)
        - [Urashcheki, robbers](#%d0%a3%d1%80%d0%b0%d1%88%d0%b5%d1%87%d0%ba%d0%b8-%d0%b3%d1%80%d0%b0%b1%d0%b5%d0%b%d1%8c%d0%ba%d0%b8)
      - [Templating](#templating)
        - [UI metrics](#ui-metrics)
        - [Business Logic Monitoring](#business-logic-monitoring)
      - [Mixed charts](#%d0%a1%d0%bc%d0%b5%d1%88%d0%b0%bd%d0%bd%1%8b%d0%b5-%d0%b3%d1%84%d0%b8%d0%ba%d0%b8)
    - [Assignment from \*: alertmanager] (#%d0%97%d0%b0%d0%b4%d0%b0%d0%b%d0%b8%d0%b5-%d1%81%d0%be-alertmanager).
      - [nginx-ingress-controller](#nginx-ingress-controller)
      - [Fix alertmanager](#fix-alertmanager)
      - [Alert rules](#alert-rules-1)
    - [Assignment from \*: Prometheus operator](#%d0%97%d0%b0%d0%b4%d0%b0%d0%b8%d0%b5-%d1%81%d0%be--prometheus-operator)
      - [Install prometheus operator](#install-prometheus-operator)
      - [ServiceMonitor](#servicemonitor)
    - [Logging](#%d0%9b%d0%be%d0%b3%d0%b3%d0%b8%d1%80%d0%be%d0%b2%d0%b0%d0%b8%d0%b5)
      - [Preparation](#%d0%9f%d0%be%d0%b4%d0%b3%d0%b1%82%d0%be%d0%b2%d0%ba%d0%b0-7)
      - [Stack](#%d0%a1%d1%82%d0%b5%d0%ba-1)
      - [EFK](#efk)
    - [Assignment from \*: Helm Chart EFK](#%d0%97%d0%b0%d0%b4%d0%b0%d0%b%d0%b8%d0%b5-%d1%81%d0%be--helm-chart-efk)

# Makefile

## Variables

| variable | default | description |


| BIN_DIR | ~/bin | The path to install executable files for `install_docker_machine` |.
| TEMP_DIR | /tmp | Time directory for downloading files |
| ENV | stage | Name of the environment |
| DOCKER_MACHINE_VERSION | v0.16.0 | docker-machine version |.
| DOCKER_MACHINE_OS | \$(shell uname -s) | Operating system name |
| DOCKER_MACHINE_ARCH | \$(shell uname -m) | architecture name |
| DOCKER_MACHINE | \${BIN_DIR}/docker-machine | The path to the executable file `docker-machine` |.
| DOCKER_MACHINE_NAME | docker-host | Instance name |
| DOCKER_MACHINE_TYPE | n1-standard-1 | Instance type |
| DOCKER_MACHINE_REGION | europe-west1-b | region |
| PACKER_VERSION | 1.4.4 | Packer version |
| PACKER | ${BIN_DIR}/packer | The path to the executable file `packer` |.
| ANSIBLE | .../.venv/bin/ansible | The path to the executable file `ansible` |.
| TERRAFORM_VERSION | 0.12.12 | Terraform version |
| TERRAFORM | ${BIN_DIR}/terraform | The path to the executable file `terraform` |.
| TFLINT_VERSION | 0.12.1 | tflist version |
| TFLINT | ${BIN_DIR}/tflint | The path to the executable file `tflint` |.
| HADOLINT_VERSION | 1.17.2 | Hadolint version (linter for Dockerfile) |.
| HADOLINT | ${BIN_DIR}/hadolint | Path to `hadolint` executable |
| IMAGE_VERSION | 1.0 | The version of the docker-image vscoder/otus-reddit for sending to docker-hub |.

## Targets

| target | used variables | description |
  ----------------------------------------------------------------------------------------------------------------------------------- |
| debug | all | Show values of all variables |
| install_requirements | no | Set python virualenv [./venv](./venv) dependency from [requirements.txt](requirements.txt) |.
| install_requirements_dev | no | Run `make install_requirements` as well as set dependencies from [requirements-dev.txt](requirements-dev.txt) |.
| install_requirements_virtualenv | no | Set python virualenv [./venv](./venv) dependencies from [requirements.txt](requirements.txt) using the virtualenv package (for python2) |.
| install_docker_machine | DOCKER_MACHINE_BASEURL, DOCKER_MACHINE_VERSION, TEMP_DIR, BIN_DIR | Download and install to `${BIN_DIR}` the executable file `docker-machine` |.
| docker_machine_create | DOCKER_MACHINE, DOCKER_MACHINE_NAME, DOCKER_MACHINE_TYPE, DOCKER_MACHINE_REGION | Create docker-machine instance in gce |.
| docker_machine_rm | DOCKER_MACHINE, DOCKER_MACHINE_NAME | Delete instance |.
| install_packer | TEMP_DIR, PACKER_VERSION, BIN_DIR | Download and install the binary packer at ${BIN_DIR} |.
| monolith_packer_build | PACKER | Collect the base image from docker-monolith/packer/docker.json template |.
| monolith_packer_validate | PACKER | Check the correctness of docker-monolith/packer/docker.json template |.
| install_terraform | TEMP_DIR, BIN_DIR, TERRAFORM_VERSION | install terraform |.
| install_tflint | TEMP_DIR, BIN_DIR, TFLINT_VERSION | install tflint |.
| install_hadolint | TEMP_DIR, BIN_DIR, HADOLINT_VERSION, HADOLINT | Install hadolint |
| monolith_terraform_init | ENV, TERRAFORM | Initialize terraform for basic environment `${ENV}` environment |.
| monolith_terraform_init_nobackend | ENV, TERRAFORM | Initialize terraform for environment `${ENV}`, without initializing remote backend. Used in automated checks |.
| monolith_terraform_validate | TERRAFORM | Validate all terraform environments |.
| monolith_terraform_tflint | TFLINT | Run tflint for all terraform environments |.
| monolith_terraform_apply | ENV, TERRAFORM | Apply terraform infrastructure for environment `${ENV}` |.
| monolith_terraform_destroy | ENV, TERRAFORM | Destroy terraform infrastructure for environment `${ENV}` |.
| monolith_ansible_install_requirements | ANSIBLE | Install external roles from [requirements.yml](docker-monolith/ansible/environments/stage/requirements.yml) |.
| monolith_ansible_inventory_list | ANSIBLE | Show content of ansible-inventory in json format |.
| monolith_ansible_lint | ANSIBLE | Run ansible-lint for all playbooks |.
| monolith_ansible_syntax | ANSIBLE | Check the syntax of all playbooks |.
| monolith_ansible_reddit_app | ANSIBLE, ENV | Expand reddit-app in the container |.
| monolith_docker_build | Collect a container from [docker-monolith/Dockerfile] |.
| monolith_docker_publish | IMAGE_VERSION | Download image `vscoder/otus-reddit:${IMAGE_VERSION}` to docker-hub |.

# Homework assignments

## HomeWork 12: Containerization technology. Introduction to Docker

### Preparing the project. Integration .

- Sloped repository [Otus-DevOps-2019-08/vscoder_microservices
  ](https://github.com/Otus-DevOps-2019-08/vscoder_microservices)
- Integration with slack has been implemented:
  - workspace `devops-team-otus.slack.com`.
  - In the chat aleksey_koloskov command `/github subscribe Otus-DevOps-2019-08/vscoder_microservices commits:all` is executed.
- Configured slack notifications from travis-ci
  - In client: _+ Add apps_ -> _Travis-CI_ -> _Settings_ -> _Add to Slack_.
  - In [.travis.yml](.travis.yml) the notifications are set according to the instruction from the opened page.
    ``Yaml
    I'm sorry:
      slack: slackchannel:faketoken
    ```
- Added by [.gitignore](.gitignore)
- Added Makefile. Aims:
  - install_requirements
  - install_docker_machine

### Installing the docker

- Installed docker as described in https://docs.docker.com/engine/installation/linux/docker-ce/ubuntu/ documentation.

  <details><summary>docker version</summary>.
  <p>

  ```
  Client: Docker Engine - Community
   Version: 19.03.4
   API version: 1.40
   Go version: go1.12.10
   Git commit: 9013bf583a
   Built: Fri Oct 18 15:54:09 2019
   OS/Arch: linux/amd64
   Experimental: false

  Server: Docker Engine - Community
   Engine:
    Version: 19.03.4
    API version: 1.40 (minimum version 1.12)
    Go version: go1.12.10
    Git commit: 9013bf583a
    Built: Fri Oct 18 15:52:40 2019
    OS/Arch: linux/amd64
    Experimental: false
   containerd:
    Version: 1.2.10
    GitCommit: b34a5c8af56e510852c35414db4c1f4fa6172339
   runc:
    Version: 1.0.0-rc8+dev
    GitCommit: 3e425f80a8c931f88e6d94a8c831b9d5a481657
   docker-init:
    Version: 0.18.0
    GitCommit: fec3683
  ```

  </p>
  </details>
  <br>
  <details><summary>docker info</summary>.
  <p>

  ```
  Client:
   Debug Mode: false

  Server:
   Containers: 0
    Running: 0
    Paused: 0
    Stopped: 0
   Images: 0
   Server Version: 19.03.4
   Storage Driver: overlay2
    Backing Filesystem: extfs
    Supports d_type: true
    Native Overlay Diff: true
   Logging Driver: json-file
   Cgroup Driver: cgroupfs
   Plugins:
    Volume: local
    Network: bridge host ipvlan macvlan null overlay
    Log: awslogs fluentd gcplogs gelf journald json-file local logentries splunk syslog
   Swarm: inactive
   Runtimes: runc
   Default Runtime: runc
   Init Binary: docker-init
   containerd version: b34a5c8af56e510852c35414db4c1f4fa6172339
   runc version: 3e425f80a8c931f88e6d94a8c831b9d5a481657
   init version: fec3683
   Security Options:
    apparmor
    seccomp
     Profile: default
   Kernel Version: 5.0.0-32-generic
   Operating System: Ubuntu 18.04.3 LTS
   OSType: linux
   Architecture: x86_64
   CPUs: 12
   Total Memory: 31.28GiB
   Name: vsc-home
   ID: RPZE:O6VJ:2IMK:H4GU:AGV7:BHBM:C5HT:MI5X:GYSH:MHZ5:BWDV:HHUC
   Docker Root Dir: /var/lib/docker
   Debug Mode: false
   Registry: https://index.docker.io/v1/
   Labels:
   Experimental: false
   Insecure Registries:
    127.0.0.0/8
   Live Restore Enabled: false

  WARNING: No swap limit support
  ```

  </p>
  </details>
  <br>
  <details><summary>docker run hello-world</summary>.
  <p>

  ```
  Unable to find image 'hello-world:latest' locally
  latest: Pulling from library/hello-world
  1b930d010525: Pull complete
  Digest: sha256:c3b4ada4687bbaa170745b3e4dd8ac3f194ca95b2d0518b417fb47e5879d9b5f
  Status: Downloaded newer image for hello-world:latest

  Hello from Docker!
  This message shows that your installation appears to be working correctly.

  To generate this message, Docker took the following steps:
   1. The Docker client contacted the Docker daemon.
   2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
      (amd64)
   3. The Docker daemon created a new container from that image which runs the
      Executable that produces the output you are currently reading.
   4. The Docker daemon streamed that output to the Docker client, which sent it
      to your terminal.

  To try something more ambitious, you can run an Ubuntu container with:
   $ docker run -it ubuntu bash

  Share images, automate workflows, and more with a free Docker ID:
   https://hub.docker.com/

  For more and ideas, visit:
   https://docs.docker.com/get-started/
  ```

  </p>
  </details>

- Installed docker-compose in [./venv](.venv)
  ``shell
  docker-compose version 1.24.1, build 4667896
  ```
- Binarnik `docker-machine` is installed.
  ``shell
  docker-machine version 0.16.0, build 702c267f
  ```

### Working with docker

- Basic docker commands list
  
  | Team | Description |
  | ----------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
  | docker ps | List of running containers |
  | docker ps -a | List of all containers |
  | docker images | List of locally saved images |
  | docker run -it ubuntu:16.04 /bin/bash | run `/bin/bash` in container ubuntu:16:04. Each time a new container is created. Without `--rm` flag, the stopped container will remain on disk. |.
  | docker ps -a --format "table {{{.ID}}\t{{{.Image}}\t{{{.CreatedAt}}\t{{{.Names}}" | A list of all containers. You will see a table with the columns listed at |.
  | docker start <u_container_id> | docker attach <u_container_id> | Connect the terminal to the created container. To disable it, press `CTRL+p` `CTRL+q` |.
  | docker create | Create a container without launching it |.
  | docker exec -it <u_container_id> bash | Start a new process inside the container |.
  | docker commit <u_container_id> yourname/ubuntu-tmp-file | Create a yourname/ubuntu-tmp-file image from the <u_container_id> container. In doing so, the container will remain running. |.

- Note _docker run = docker create + docker start + docker attach\*_ \* _docker attach_ is executed with the option `-i`.
- Basic Options
  
  | Option | Description |
  | ------------ | ---------------------------------------------------------- |
  | -i | starts the container in foreground mode (docker attach) |.
  | -d | starts the container in background mode |.
  | -t | creates TTY |
  | --entrypoint | allows you to override ENTRYPOINT when you run the container |.
- After executing commands from RS, the list of images is saved in [docker-monolith/docker-1.log](docker-monolith/docker-1.log).

### Task from \ ##: Differences in image and container

* Links to the subject:
  * An Image is an ordered collection of root filesystem changes and the corresponding execution parameters for use within a container runtime.
  * [About storage drivers](https://docs.docker.com/storage/storagedriver/)
  * [How the overlay2 driver works] [https://docs.docker.com/storage/storagedriver/overlayfs-driver/#how-the-overlay2-driver-works]
  * [Docker Image Specification v1.2.0. Image JSON Field Descriptions] (https://github.com/docker/docker-ce/blob/master/components/engine/image/spec/v1.2.md)
  * [Docker images and containers in pictures] (https://habr.com/en/post/272145/)
  * [What to Inspect When You're Inspecting](https://www.ctl.io/developers/blog/post/what-to-inspect-when-youre-inspecting)
  * [Engine API v1.24](https://docs.docker.com/engine/api/v1.24/)
  * [Connecting the container to multiple networks] (https://success.docker.com/article/multiple-docker-networks)
* The output results of the command `docker inspect <u_image_id>` are analyzed.
  <details><summary>Results</summary>.
  <p>

  `json
  [
    {
      "Id": "sha256:5f2bf26e35249d8b47f002045c57b2ea9d8ba68704f45f3c209182a7a2a9ece5", # SHA256 hash of its configuration JSON.
      "RepoTags." [ # List of image tags
        "ubuntu:16.04."
      ],
      "RepoDigests." [ # The Chexum of the Image
        "ubuntu@sha256:bb5b48c7750a6a8775c74bcb601f7e5399135d0a06de004d000e05fd25c1a71c."
      ],
      "Parent." "", # Superior layer ID in the image store. Empty due to the absence of parent layers in the local repository. For more information: https://stackoverflow.com/questions/45820905/docker-image-inspection-json-interpretation Documentation: https://docs.docker.com/storage/storagedriver/.
      "Comment." "", # Comment
      "Created": "2019-10-31T22:21:29.640561379Z", # Image creation date
      "Container." "363288fa6924e2d1e1b00da6525ffde40bb0de65b1da6ce6e44e363df532614e", # The temporary identifier of the container created during the assembly of the image. Docker will create a container during the image construction process, and this identifier is stored in the image data.
      "ContainerConfig": { # This data again is referring to the temporary container created when the Docker build command was executed
        "Hostname": "363288fa6924."
        "Domainname": ""
        "User." "",
        "AttachStdin": false,
        "AttachStdout": false,
        "AttachStderr": false,
        "Tty": false,
        "OpenStdin": false,
        "StdinOnce": false,
        "Env." [
          "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin."
        ],
        "Cmd." [
          "/bin/sh."
          "-c",
          "#(nop)."
          "CMD [\"/bin/bash\"]"
        ],
        "ArgsEscaped": true,
        "Image." "sha256:66d791e2304a4caa9fda9b56ad9fff2679e7b933c83d23fca8e3ec3b5595c4dc",
        "Volumes": null,
        "WorkingDir." "",
        "Entrypoint": null,
        "OnBuild": null,
        "Labels." {}
      },
      "DockerVersion." "18.06.1-ce", # The docker version used to build the image
      "Author." "", # Author of the image
      "Config." { # The configuration parameters that should be taken as the basis for launching the container based on this image. Judging by the documentation, all these parameters can be overridden when creating the container
        "Hostname." "",
        "Domainname." "",
        "User." "", # The default user of the running container
        "AttachStdin": false,
        "AttachStdout": false,
        "AttachStderr": false,
        "Tty": false,
        "OpenStdin": false,
        "StdinOnce": false,
        "Env." [ # Environment Variables
          "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin."
        ],
        "Cmd." [ # CMD by default
          "bin/bash"
        ],
        "ArgsEscaped": true,
        "Image." "sha256:66d791e2304a4caa9fda9b56ad9fff2679e7b933c83d23fca8e3ec3b5595c4dc",
        "Volumes": null, # default volumes
        "WorkingDir." "", # The default working directory
        "Entrypoint": null, # ENTRYPOINT by default
        "OnBuild": null,
        "Labels": null
      },
      "Architecture." "amd64", # Architecture for which the image binary files [i386, amd64, arm] were created
      "Os." "linux", # The name of the OS where the image should be run
      "Size." 122564827,
      "VirtualSize." 122564827, # The size of the image reported in bytes
      "GraphDriver." { # https://docs.docker.com/storage/storagedriver/select-storage-driver/]
        "Data." { # https://stackoverflow.com/a/56551786/3488348
          "LowerDir." "/var/lib/docker/overlay2/897edb9e383005a310bb7685eda9b259c5c0b7740d2d65e7d1c44f228dc73ce9/diff. /var/lib/docker/overlay2/bc1b6b3a839591c8870d5aa8ad328af83c5325b82a88163986a0186b11016921/diff:/var/lib/docker/overlay2/11810c8b5bbff1b9b14089bcef62d0029a39ae0686c51a5ce0e616e71f2573bf/diff",
          "MergedDir." "/var/lib/docker/overlay2/8dac1ac5277e9c3bf4e3d7111d947bf2f4553dd85764077b0ed057d3e1b93022/merged",
          "UpperDir." "/var/lib/docker/overlay2/8dac1ac5277e9c3bf4e3d7111d947bf2f4553dd85764077b0ed057d3e1b93022/diff",
          "WorkDir." "/var/lib/docker/overlay2/8dac1ac5277e9c3bf4e3d7111d947bf2f4553dd85764077b0ed057d3e1b93022/work."
        },
        "Name." "overlay2" # https://docs.docker.com/storage/storagedriver/overlayfs-driver/#how-the-overlay2-driver-works
      },
      "RootFS." { # Refers to addresses of the contents of the layers used in the image
        "Type." "layers."
        "Layers." [
          "sha256:788b17b748c23d38ec62e913e87b084b7e3efda49843b3c0809b1857559b553e."
          "sha256:a5a5f8c62487121247923a4df970f2094725ac2fea8c1347236466c4a3265ae0."
          "sha256:903669ee720750938f08f95f7c8f1022d7fd7c57602af847b316f0b39efbd01c."
          "sha256:bc72fb2e7b7487b3b9f9135437319525feaf1fab6ba61dab7e2e961e5c1db8b."
        ]
      },
      "Metadata." { # Metadata
        "LastTagTime." "0001-01-01T00:00:00Z."
      }
    }
  ]
  
  ```

  </p>
  </details>
* The output of the command `docker inspect <u_container_id>` is analyzed.
  <details><summary>Results</summary>.
    <p>

  `json
  [
      {
          "Id." "03a9eea159ef6e417a2e67802c5fa021f4a8d0b634ba377cd0074d6ff5eef511."
          "Created." "2019-11-02T16:08:06.723203393Z", # Container creation date
          "Path." "bash."
          "Args." [],
          "State." { # Description of container status
              "Status." "running", # Current status
              "Running": true, # Launched?
              "Paused": false, # Suspended?
              "Restarting": false, # Restarted?
              "OOMKilled": false, # Killed by an OOM killer?
              "Dead": false, # Fallen (dead)?
              "Pid." 25711, # Container process ID in host os
              "ExitCode." 0, # Completion cat (used to restart after falling)
              "Error." "", # Error in case of a fall
              "StartedAt." "2019-11-02T16:08:07.16481008Z", # Launch time
              "FinishedAt." "0001-01-01T00:00:00Z" # Finished time
          },
          "Image." "sha256:5f2bf26e35249d8b47f002045c57b2ea9d8ba68704f45f3c209182a7a2a9ece5", # Image ID on which the container was created
          "ResolvConfPath." "/var/lib/docker/containers/03a9eea159ef6e417a2e67802c5fa021f4a8d0b634ba377cd0074d6ff5eef511/resolv.conf",
          "HostnamePath." "/var/lib/docker/containers/03a9eea159ef6e417a2e67802c5fa021f4a8d0b634ba377cd0074d6ff5eef511/hostname."
          "HostsPath." "/var/lib/docker/containers/03a9eea159ef6e417a2e67802c5fa021f4a8d0b634ba377cd0074d6ff5eef511/hosts",
          "LogPath." "/var/lib/docker/containers/03a9eea159ef6e417a2e67802c5fa021f4a8d0b634ba377cd0074d6ff5eef511/03a9eea159ef6e417a2e67802c5fa021f4a8d0b634ba377cd0074d6ff5eef511-json.log",
          "Name." "/wonderful_blackwell", # The container name. To be generated randomly, unless explicitly specified.
          "RestartCount." 0, # Number of restarts. Used for https://docs.docker.com/engine/reference/commandline/run/#restart-policies---restart.
          "Driver." "overlay2."
          "Platform." "linux."
          "MountLabel." "",
          "ProcessLabel." "",
          "AppArmorProfile." "docker-default."
          "ExecIDs": null,
          "HostConfig." { # Host system configuration
              "Binds": null,
              "ContainerIDFile." "",
              "LogConfig." { # Logging settings
                  "Type." "json-file."
                  "Config." {}
              },
              "NetworkMode." "default", # Sets the networking mode for the container. Supported standard values are: bridge, host, none, and container:<name|id>. Any other value is taken as a custom network's name to which this container should connect to.
              "PortBindings." {}, # PortBindings
              "RestartPolicy." { # Restart policy https://docs.docker.com/engine/reference/commandline/run/#restart-policies---restart]
                  "Name." "no."
                  "MaximumRetryCount." 0
              },
              "AutoRemove": false, # Automatically remove the container after installation
              "VolumeDriver." "", # Driver that this container users to mount volumes.
              "VolumesFrom": null, # A list of volumes to inherit from another container. Specified in the form <container name>[:<ro|rw>].
              "CapAdd": null, # A list of kernel capabilities added to the container.
              "CapDrop": null, # A list of kernel capabilities dropped from the container.
              "Capabilities": null,
              "Dns." [], # dns servers used by the container
              "DnsOptions." [],
              "DnsSearch." [],
              "ExtraHosts": null, # Additional entries in /etc/hosts
              "GroupAdd": null, # A list of additional groups that the container process will run as
              "IpcMode." "private."
              "Cgroup." "",
              "Links": null, # A list of links for the container. Each link entry is in the form of container_name:alias.
              "OomScoreAdj." 0, # An integer value containing the score given to the container in order to tune OOM killer preferences.
              "PidMode." "", # Set the PID (Process) Namespace mode for the container; "container:<name|id>": joins another container's PID namespace "host": use the host's PID namespace inside the container
              "Privileged": false, # The container is running in privileged mode https://docs.docker.com/engine/reference/run/#runtime-privilege-and-linux-capabilities.
              "PublishAllPorts: false, # Allocates an ephemeral host port for all of a container's exposed ports. Specified as a boolean value. Ports are de-allocated when the container stops and when the container starts. The port might be changed when restarting the container.
              "ReadonlyRootfs": false, # The container's file system is read-only.
              "SecurityOpt": null, # A list of string values to customize labels for MLS systems, such as SELinux.
              "UTSMode." "",
              "UsernsMode." "", # Sets the usernamespace mode for the container when usernamespace remapping option is: host.
              "ShmSize." 67108864, # Size of /dev/shm in bytes. The size must be greater than 0. If omitted the system uses 64MB.
              "Runtime": "runc", # Runtime used.
              "ConsoleSize." [
                  0,
                  0
              ],
              "Isolation." "", # isolation=(default process hyperv) (Windows daemon only)
              "CpuShares." 0, # An integer value containing the container's CPU Shares (ie. the relative weight vs other containers).
              "Memory." 0, # Memory limit in bytes.
              "NanoCpus." 0,
              "CgroupParent." "", # Path to cgroups under which the container's cgroup is created. If the path is not absolute, the path is considered to be relative to the cgroups path of the init process. If the path is not absolute, the path is considered to be relative to the cgroups path of the init process.
              "BlkioWeight": 0, # Block IO weight (relative weight) accepts a weight value between 10 and 1000.
              "BlkioWeightDevice": [],
              "BlkioDeviceReadBps": null,
              "BlkioDeviceWriteBps": null,
              "BlkioDeviceReadIOps": null,
              "BlkioDeviceWriteIOps": null,
              "CpuPeriod." 0, # The length of a CPU period in microseconds.
              "CpuQuota." 0, # The microseconds of CPU time that the container can get in a CPU period.
              "CpuRealtimePeriod." 0,
              "CpuRealtimeRuntime." 0,
              "CpusetCpus." "", # String value containing the cgroups CpusetCpus to use.
              "CpusetMems." "", # Memory nodes (MEMs) in which to allow execution (0-3, 0.1). Only effective on NUMA systems.
              "Devices." [], # A list of devices to add to the container specified as a JSON object in the form { "PathOnHost": "/dev/deviceName", "PathInContainer": "/dev/deviceName", "CgroupPermissions": "mrw"}
              "DeviceCgroupRules": null,
              "DeviceRequests": null,
              "KernelMemory." 0, # Kernel memory limit in bytes.
              "KernelMemoryTCP." 0,
              "MemoryReservation." 0, # Memory soft limit in bytes.
              "MemorySwap": 0, # Total memory limit (memory + swap); -1 is unlimited swap. You must use this with memory and make the swap value larger than memory.
              "MemorySwappiness": null, # Tune a container's memory swappiness behavior. Integer between 0 and 100.
              "OomKillDisable": false, # Boolean value, whether to disable OOM Killer for the container or not.
              "PidsLimit": null, # A container's pids limit. -1 if unlimited.
              "Ulimits": null, # A list of ulimits to set in the container, specified as { "Name": <name>, "Soft": <soft limit>, "Hard": <hard limit> }, for example: Ulimits: {"Name": }, for example: Ulimits: { "Name": }: "nofile", "Soft": 1024, "Hard": 2048 }
              "CpuCount." 0,
              "CpuPercent." 0, # An integer value containing the usable percentage of the CPUs. (Windows daemon only)
              "IOMaximumIOps." 0, # Maximum IO absolute rate in terms of bytes per second.
              "IOMaximumBandwidth." 0, # Maximum IO absolute rate in terms of IOps.
              "MaskedPaths." [
                  "/proc/asound."
                  "/proc/acpi."
                  "Proc/kcore."
                  "/proc/keys."
                  "/proc/latency_stats."
                  "/proc/timer_list."
                  "/proc/timer_stats."
                  "/proc/sched_debug."
                  "/proc/scsi."
                  "/sys/firmware"
              ],
              "ReadonlyPaths." [
                  "/proc/bus."
                  "/proc/fs."
                  "/proc/irq."
                  "/proc/sys."
                  "/proc/sysrq-trigger"
              ]
          },
          "GraphDriver." {
              "Data." {
                  "LowerDir": "/var/lib/docker/overlay2/7ebf817bfc93f412448a4e804d2f149b25d4072c6985ab185216648194786889-init/diff. /var/lib/docker/overlay2/8dac1ac5277e9c3bf4e3d7111d947bf2f4553dd85764077b0ed057d3e1b93022/diff: /var/lib/docker/overlay2/897edb9e383005a310bb7685eda9b259c5c0b7740d2d65e7d1c44f228dc73ce9/diff:/var/lib/docker/overlay2/bc1b6b3a839591c8870d5a8ad328af83c5325b82a88163986a0186b11016921/diff: /var/lib/docker/overlay2/11810c8b5bbff1b9b14089bcef62d0029a39ae0686c51a5ce0e616e71f2573bf/diff",
                  "MergedDir": "/var/lib/docker/overlay2/7ebf817bfc93f412448a4e804d2f149b25d4072c6985ab185216648194786889/merged",
                  "UpperDir": "/var/lib/docker/overlay2/7ebf817bfc93f412448a4e804d2f149b25d4072c6985ab185216648194786889/diff",
                  "WorkDir": "/var/lib/docker/overlay2/7ebf817bfc93f412448a4e804d2f149b25d4072c6985ab185216648194786889/work."
              },
              "Name": "overlay2" # https://docs.docker.com/storage/storagedriver/overlayfs-driver/#how-the-overlay2-driver-works
          },
          "Mounts." [], # Specification for mounts that was added to containers created as part of the service.
          "Config": {
              "Hostname": "03a9eea159ef", # Host name
              "Domainname": "", # Domain
              "User." "", # The user inside the container
              "AttachStdin": true, # Attached to stdin
              "AttachStdout": true, # Attached to stdout
              "AttachStderr": true, # Attached to stderr
              "Tty": true, # Standart streams attached to tty
              "OpenStdin": true,
              "StdinOnce": true,
              "Env." [ # A list of environment in the form of ["VAR=value",...]
                  "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"...
              ],
              "Cmd." [ # CMD runned in container
                  "bash"
              ],
              "Image": "ubuntu:16.04", # The container image name
              "Volumes": null, # An object mapping mount point paths (strings) inside the container to empty objects.
              "WorkingDir": "", # string specifying the working directory for commands to run in.
              "Entrypoint": null, # ENTRYPOINT of a container
              "OnBuild": null,
              "Labels." {} # A map of labels of a container
          },
          "NetworkSettings." { # Container network settings.
              "Bridge": ""
              "SandboxID": "b8b58bb4f3a477aca4a6d05ee397e6cb62859afa30d8806e64e8e8e130af9e05."
              "HairpinMode": false, # https://en.wikipedia.org/wiki/Hairpinning
              "LinkLocalIPv6Address." "",
              "LinkLocalIPv6PrefixLen": 0,
              "Ports." {}, # Mapped ports
              "SandboxKey": "/var/run/docker/netns/b8b58bb4f3a4",
              "SecondaryIPAddresses": null,
              "SecondaryIPv6Addresses": null,
              "EndpointID": "e7f60af3ade6a1ecba41456c0f3252f8edd502287c826a214c6318ef74f8efdf",
              "Gateway": "172.17.0.1", # Network gateway
              "GlobalIPv6Address." "",
              "GlobalIPv6PrefixLen": 0,
              "IPAddress." "172.17.0.2", # Container's ip address
              "IPPrefixLen." 16,
              "IPv6Gateway": "",
              "MacAddress." "02:42:ac:11:00:02", # mac-address
              "Networks." {"Networks and a container
                  "bridge." {
                      "IPAMConfig": null,
                      "Links": null,
                      "Aliases": null,
                      "NetworkID": "156780e8135120a2650a4d34c2a0aee35cd4d3cde3d98fb0e3b1ebfd3a797bfd",
                      "EndpointID": "e7f60af3ade6a1ecba41456c0f3252f8edd502287c826a214c6318ef74f8efdf",
                      "Gateway": "172.17.0.1",
                      "IPAddress." "172.17.0.2",
                      "IPPrefixLen." 16,
                      "IPv6Gateway": "",
                      "GlobalIPv6Address." "",
                      "GlobalIPv6PrefixLen": 0,
                      "MacAddress." "02:42:11:00:02."
                      "DriverOpts": null
                  }
              }
          }
      }
  ]
  ```

  </p>
  </details>
* The file [docker-monolith/docker-1.log] (docker-monolith/docker-1.log) describes the differences between the image and container

### More docker commands

#### Docker kill & stop

Read more about [Signals on Linux](https://ru.wikipedia.org/wiki/Сигналы_(UNIX)).

Description:
* kill immediately sends SIGKILL *
* stop sends SIGTERM, and after 10 seconds (adjustable) sends SIGKILL
* SIGTERM - application stop signal
* SIGKILL - unconditional process completion

Practice:
* `docker ps -q`
  ``log
  cc75429464ba
  03a9eea159ef
  ```
* `docker kill cc75429464ba `
  ``log
  cc75429464ba
  ```
* `docker ps -q` - one container left running *
  ``log
  03a9eea159ef
  ```

#### docker system df

* Displays how much disk space is occupied by images, containers and volumes
* Displays how many of them are not in use and can be removed

`docker system df`
``log
TYPE TOTAL ACTIVE SIZE RECLAIMABLE
Images 4 3 248.8MB 122.6MB (49%)
Containers 5 1 15B 9B (60%)
Local Volumes 0 0B 0B
Build Cache 0 0B 0B
```

#### Docker rm & rmi

* rm deletes the container, you can add -f flag to delete the working container (sigkill will be sent).
* rmi removes the image if the containers that are running do not depend on it

`docker rm $(docker ps -a -q)` # will remove all empty containers
``log
cc75429464ba
5d9a698c4c62
2cf9183503e2
89716fceca99
Error response from daemon: You cannot remove a running container 03a9eea159ef6e417a2e67802c5fa021f4a8d0b634ba377cd0074d6ff5eef511. Stop the container before attempting removal or force removal
```

`docker rmi $(docker images -q)`
``log
Untagged: vscoder/ubuntu-tmp-file:latest
Deleted: sha256:e63bb81dd3f064fb9fe854a1e66ca76e30c79fbc54eb9f09c5ab054a8d0d8cd3
Untagged: nginx:latest
Untagged: nginx@sha256:922c815aa4df050d4df476e92daed4231f466acc8ee90e0e774951b0fd7195a4
Deleted: sha256:540a289bab6cb1bf880086a9b803cf0c4cefe38cbb5cdefa199b69614525199f
Deleted: sha256:ab18af7cee69bfb22c1771e54d5e0e68b1a1bf57b46516142da0380b1771f4a
Deleted: sha256:02f7daf1e14541cd61a3dda1a61cc0f78fee8de2984d488b8ba5bd3cbad9b57
Deleted: sha256:b67d19e65ef653823ed62a5835399c610a40e8205c16f839c5cc567954fcf594
Untagged: hello-world:latest
Untagged: hello-world@sha256:c3b4ada4687bbaa170745b3e4dd8ac3f194ca95b2d0518b417fb47e5879d9b5f
Deleted: sha256:fce289e99eb9bca977dae136fbe2a82b6b7d4c372474c9235adc1741675f587e
Deleted: sha256:af0b15c8625bb1938f1d7b17081031f649fd14e6b233688eea3c5483994a6a3
Error response from daemon: conflict: unable to delete 5f2bf26e3524 (cannot be forced) - image is being used by running container 03a9eea159ef
```


### Docker containers

#### GCE

* A new project _docker_ id `docker-257914` has been created.
* gcloud SDK installed earlier
* Done `gcloud init` with the new _otus-devops-docker_ configuration.
* Executed `gcloud auth application-default login` to get a file with authorization data for docker-machine.
  The file is saved in the path `/home/<myuser>/.config/gcloud/application_default_credentials.json`.

#### Docker machine

Installation on Linux https://docs.docker.com/machine/install-machine/

* docker-machine is a built-in docker tool for creating and installing docker engine on hosts. It supports clouds and virtualization systems (Virtualbox, GCP, etc.).
* docker-machine create command - `docker-machine create <name>`. Names can be many, switching between them through `eval $(docker-machine env <name>)`. Switch to local docker - `eval $(docker-machine env --unset)`. Deletion - `docker-machine rm <name>.
* docker-machine creates a host for the daemon docker with --googlemachine-image, ubuntu-16.04 is used in RS. The images used to build the container docker have nothing to do with this.
* All docker commands that run in the same console after `eval $(docker-machine env <name>)` work with a remote docker daemon in GCP.

* The file [env](env) is created with the environment variables needed to work with docker-machine.
* For the project it is allowed to use the API as it was said at the first attempt to create the machine
* A machine is created
  ``shell
  docker-machine create --driver google \.
  --google-machine-image https://www.googleapis.com/compute/v1/projects/ubuntu-os-cloud/global/images/family/ubuntu-1604-lts \.
  --google-machine-type n1-standard-1 \.
  --google-zone europe-west1-b \
  docker-host
  ```
  ``log
  Running pre-create checks...
  (docker-host) Check that the project exists
  (docker-host) Check if the instance already exists
  Creating machine...
  (docker-host) Generating SSH Key
  (docker-host) Creating host...
  (docker-host) Opening firewall ports
  (docker-host) Creating instance
  (docker-host) Waiting for Instance
  (docker-host) Uploading SSH Key
  Waiting for machine to be running, this may take a few minutes...
  Detecting operating system of created instance...
  Waiting for SSH to be available...
  Detecting the provisioner...
  Provisioning with ubuntu(systemd)...
  Installing Docker...
  Copying certs to the local machine directory...
  Copying certs to the remote machine...
  Setting Docker configuration on the remote daemon...
  Checking connection to Docker...
  Docker is up and running!
  To see how to connect your Docker Client to the Docker Engine running on this virtual machine, run: docker-machine env docker-host
  ```
* docker-machine successfully created `docker-machine ls `
  ``log
  NAME ACTIVE DRIVER STATE URL SWARM DOCKER
  docker-host - google Running tcp://34.76.188.197:2376 v19.03.4
  ```
* Switching to the created machine `eval $(docker-machine env docker-host)` is made.

#### Working with namespaces

#### PID namespace

* By default, the container runs in a separate PID namespace
  The command `docker run --rm -ti tehbilly/htop` shows only the running htop process.
  Team `docker run --rm -ti ubuntu:16.04 ps auxf` returns a similar result.
  ``log
  USER PID %CPU %MEM VSZ RSS TTY STAT START TIME COMMAND
  root 1 0.0 0.0 25976 1456 pts/0 Rs+ 18:29 0:00 ps auxf
  ```
* Running the container in the PID namespace host
  The `docker run --rm --pid host -ti tehbilly/htop` command returns all host system processes.
  Team `docker run --rm --pid host -ti ubuntu:16.04 ps auxf` returns a similar
  <details><summary> the result</summary>.
  <p>

  ``log
  USER PID %CPU %MEM VSZ RSS TTY STAT START TIME COMMAND
  root 2 0.0 0 0.0 0 0 ?        S 15:27 0:00 [kthreadd]
  root 4 0.0 0 0.0 0 0 ?        I< 15:27 0:00 \_ [kworker/0:
  root 6 0.0 0.0 0 0 ?        I< 15:27 0:00 \_ [mm_percpu_
  root 7 0.0 0 0.0 0 0 ?        S 15:27 0:00 \_ [ksoftirqd/
  root 8 0.0 0 0.0 0 0 ?        I 15:27 0:00 \_ [rcu_sched]
  root 9 0.0 0.0 0 0 ?        I 15:27 0:00 \_ [rcu_bh]
  root 10 0.0 0 0.0 0 0 ?        S 15:27 0:00 \_ [migration/
  root 11 0.0 0 0.0 0 0 ?        S 15:27 0:00 \_ [watchdog/0
  root 12 0.0 0 0.0 0 0 ?        S 15:27 0:00 \_ [cpuhp/0]
  root 13 0.0 0 0.0 0 0 ?        S 15:27 0:00 \_ [kdevtmpfs]
  root 14 0.0 0 0.0 0 0 ?        I< 15:27 0:00 \_ [netns]
  root 15 0.0 0 0.0 0 0 ?        S 15:27 0:00 \_ [rcu_tasks_
  root 16 0.0 0 0.0 0 0 ?        S 15:27 0:00 \_ [kauditd]
  root 17 0.0 0 0.0 0 0 ?        S 15:27 0:00 \_ [khungtaskd
  root 18 0.0 0 0.0 0 0 ?        S 15:27 0:00 \_ [oom_reaper
  root 19 0.0 0 0.0 0 0 ?        I< 15:27 0:00 \_ [writeback]
  root 20 0.0 0 0.0 0 0 ?        S 15:27 0:00 \_ [kcompactd0
  root 21 0.0 0 0.0 0 0 ?        SN 15:27 0:00 \_ [ksmd]
  root 22 0.0 0 0.0 0 0 ?        SN 15:27 0:00 \_ [khugepaged
  root 23 0.0 0 0.0 0 0 ?        I< 15:27 0:00 \_ [crypto]
  root 24 0.0 0 0.0 0 0 ?        I< 15:27 0:00 \_ [kintegrity
  root 25 0.0 0 0.0 0 0 ?        I< 15:27 0:00 \_ [kblockd]
  root 26 0.0 0 0.0 0 0 ?        I< 15:27 0:00 \_ [ata_sff]
  root 27 0.0 0.0 0 0 ?        I< 15:27 0:00 \_ [md]
  root 28 0.0 0 0.0 0 0 ?        I< 15:27 0:00 \_ [edac-polle
  root 29 0.0 0.0 0 0 ?        I< 15:27 0:00 \_ [devfreq_wq
  root 30 0.0 0 0.0 0 0 ?        I< 15:27 0:00 \_ [watchdogd]
  root 34 0.0 0 0.0 0 0 ?        S 15:27 0:00 \_ [kswapd0]
  root 35 0.0 0 0.0 0 0 ?        I< 15:27 0:00 \_ [kworker/u3
  root 36 0.0 0 0.0 0 0 ?        S 15:27 0:00 \_ [ecryptfs-k
  root 78 0.0 0.0 0 0 ?        I< 15:27 0:00 \_ [kthrotld]
  root 79 0.0 0.0 0 0 ?        I< 15:27 0:00 \_ [acpi_therm
  root 80 0.0 0.0 0 0 ?        S 15:27 0:00 \_ [scsi_eh_0]
  root 81 0.0 0.0 0 0 ?        I< 15:27 0:00 \_ [scsi_tmf_0
  root 87 0.0 0 0.0 0 0 ?        I< 15:27 0:00 \_ [ipv6_addrc
  root 97 0.0 0.0 0 0 ?        I< 15:27 0:00 \_ [kstrp]
  root 99 0.0 0 0.0 0 0 ?        I< 15:27 0:00 \_ [kworker/0:
  root 115 0.0 0.0 0 0 ?        I< 15:27 0:00 \_ [charger_ma
  root 268 0.0 0 0.0 0 0 ?        I< 15:27 0:00 \_ [raid5wq]
  root 321 0.0 0 0.0 0 0 ?        S 15:27 0:00 \_ [jbd2/sda1- ?
  root 322 0.0 0 0.0 0 0 ?        I< 15:27 0:00 \_ [ext4-rsv-c
  root 393 0.0 0 0.0 0 0 ?        I< 15:27 0:00 \_ [iscsi_eh]
  root 403 0.0 0 0.0 0 0 ?        I< 15:27 0:00 \_ [ib-comp-wq
  root 404 0.0 0 0.0 0 0 ?        I< 15:27 0:00 \_ [ib_mcast]
  root 405 0.0 0 0.0 0 0 ?        I< 15:27 0:00 \_ [ib_nl_sa_w
  root 408 0.0 0 0.0 0 0 ?        I< 15:27 0:00 \_ [rdma_cm]
  root 7628 0.0 0.0 0 0 ?        I 17:41 0:00 \_ [kworker/u2
  root 7678 0.0 0 0.0 0 0 ?        I 17:44 0:00 \_ [kworker/0:
  root 8019 0.0 0.0 0 0 ?        I 18:10 0:00 \_ [kworker/0:
  root 8094 0.0 0.0 0 0 ?        I 18:15 0:00 \_ [kworker/u2
  root 8189 0.0 0 0.0 0 0 ?        I 18:23 0:00 \_ [kworker/u2
  root 8254 0.0 0 0.0 0 0 ?        I 18:27 0:00 \_ [kworker/u2
  root 8385 0.0 0 0.0 0 0 ?        I 18:27 0:00 \_ [kworker/0:
  root 8601 0.0 0.0 0 0 ?        I 18:29 0:00 \_ [kworker/0:
  root 1 0.0 0.1 37732 5844 ?        Ss 15:27 0:02 /sbin/init
  root 402 0.0 0.1 31808 4304 ?        Ss 15:27 0:00 /lib/systemd/sy
  root 423 0.0 0 0.0 94772 1580 ?        Ss 15:27 0:00 /sbin/lvmetad -
  root 449 0.0 0.1 43068 4264 ?        Ss 15:27 0:00 /lib/systemd/sy
  root 910 0.0 0.0 16120 2864 ?        Ss 15:27 0:00 /sbin/dhclient 
  root 1133 0.0 0 0.0 5220 148 ?        Ss 15:27 0:00 /sbin/iscsid
  root 1135 0.0 0 0.0 5720 3504 ?        S<Ls 15:27 0:01 /sbin/iscsid
  root 1150 0.0 0.0 28620 3024 ?        Ss 15:27 0:00 /lib/systemd/sy
  root 1169 0.0 0.1 272944 5796 ?        Ssl 15:27 0:00 /usr/lib/accoun
  root 1179 0.0 0 0.0 26068 2492 ?        Ss 15:27 0:00 /usr/sbin/cron 
  root 1207 0.0 0 0.0 4396 1304 ?        Ss 15:27 0:00 /usr/sbin/acpid
  107 1249 0.0 0.0 42892 3744 ?        Ss 15:27 0:00 /usr/bin/dbus-d
  daemon 1265 0.0 0 0.0 26044 2184 ?        Ss 15:27 0:00 /usr/sbin/atd -
  root 1297 0.0 0 0.0 95368 1524 ?        Ssl 15:27 0:00 /usr/bin/lxcfs 
  root 1312 0.0 0.0 81068 2212 ?        Ssl 15:27 0:00 /usr/sbin/sshgu
  root 1351 0.0 0.5 171696 19376 ?        Ssl 15:27 0:00 /usr/bin/python
  root 1357 0.0 0.1 277180 6020 ?        Ssl 15:27 0:00 /usr/lib/policy
  root 1406 0.0 0 0.0 13372 156 ?        Ss 15:27 0:00 /sbin/mdadm --m
  112 1550 0.0 0.1 40268 4840 ?        Ss 15:27 0:00 /usr/sbin/ntpd 
  root 1553 0.0 0.5 65388 21424 ?        Ss 15:27 0:00 /usr/bin/python
  root 1580 0.0 0.5 65452 21540 ?        Ss 15:27 0:01 /usr/bin/python
  root 1581 0.0 0.5 65368 21264 ?        Ss 15:27 0:00 /usr/bin/python
  root 1595 0.0 0.1 65512 6160 ?        Ss 15:27 0:00 /usr/sbin/sshd 
  root 1602 0.0 0.0 14656 1804 ?        Ss+ 15:27 0:00 /sbin/agetty --
  root 1635 0.0 0.0 12840 1780 ?        Ss+ 15:27 0:00 /sbin/agetty --
  root 4552 0.1 1.2 440504 46512 ?        Ssl 15:28 0:11 /usr/bin/contai
  root 9754 0.0 0.1 108976 6044 ?        Sl 18:32 0:00 \\.
  root 9784 20.0 0.0 34560 2904 pts/0 Rs+ 18:32 0:00 \_ ps auxf
  root 9817 0.0 0.0 0 0 ?        Z 18:32 0:00 \_ [runc] 
  root 5528 0.0 2.9 502264 109968 ?       Ssl 15:28 0:06 /usr/bin/docker
  _apt 8014 0.0 0.0 256392 3204 ?        Ssl 18:10 0:00 /usr/sbin/rsysl
  ```

  </p>
  </details>

##### NET namespace

Found an article on the topic: https://platform9.com/blog/container-namespaces-deep-dive-container-networking/.

* Ran container nginx `docker run --rm --name wwweb -d nginx *
* Connected by ssh to _docker-machine_ `gcloud compute ssh docker-host *
* `docker ps`
  ``log
  CONTAINER ID IMAGE COMMAND CREATED STATUS PORTS NAMES
  0e2ba62df689 nginx "nginx -g 'daemon of..."   4 seconds ago Up 3 seconds 80/tcp wwweb
  ```
* By default, the docker does not add container network neimscapes to `/var/run'. To do so, you need to run a sequence of commands:
  ``shell
  CONTAINER_PID="$(docker inspect -f '{{.State.Pid}}' wwweb)".
  echo $CONTAINER_PID
  sudo mkdir -p /var/run/netns
  sudo ln -sf /proc/$CONTAINER_PID/ns/net "/var/run/netns/wwweb"
  ```
* after that you can view and access the network namespace container
  * Neimscapes are now added to the list *
    ``shell
    # sudo ip netns list
    wwweb (id: 0)
    ```
* ip addresses
  * view ip-addresses of the interfaces in the neumscape
    ``shell
    # sudo ip netns exec wwweb ip addr
    1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
        link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00:00
        inet 127.0.0.1/8 scope host lo
           valid_lft forever preferred_lft forever
    29: eth0@if30: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
        link/ether 02:42:ac:11:00:02 brd ff:ff:ff:ff:ff:link-netnsid 0
        inet 172.17.0.2/16 brd 172.17.255.255 scope global eth0
           valid_lft forever preferred_lft forever
    ```
  * ip-address list inside wwweb container (iproute2 package had to be installed in the container beforehand)
    ``shell
    # docker exec -ti wwweb ip addr
    1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
        link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00:00
        inet 127.0.0.1/8 scope host lo
           valid_lft forever preferred_lft forever
    29: eth0@if30: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
        link/ether 02:42:ac:11:00:02 brd ff:ff:ff:ff:ff:link-netnsid 0
        inet 172.17.0.2/16 brd 172.17.255.255 scope global eth0
           valid_lft forever preferred_lft forever
    ```
    As you can see, it matches the list inside net namespace.
  * List of ip addresses of host interfaces
    ``shell
    # ip addr
    1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
        link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00:00
        inet 127.0.0.1/8 scope host lo
           valid_lft forever preferred_lft forever
        inet6 ::1/128 scope host 
           valid_lft forever preferred_lft forever
    2: ens4: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1460 qdisc pfifo_fast state UP group default qlen 1000
        link/ether 42:01:0a:84:00:02 brd ff:ff:ff:ff:ff:ff:ff
        inet 10.132.0.2/32 brd 10.132.0.2 scope global ens4
           valid_lft forever preferred_lft forever
        inet6 fe80::4001:aff:fe84:2/64 scope link 
           valid_lft forever preferred_lft forever
    4: docker0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
        link/ether 02:42:4c:d3:0b:bb brd ff:ff:ff:ff:ff:ff
        inet 172.17.0.1/16 brd 172.17.255.255 scope global docker0
           valid_lft forever preferred_lft forever
        inet6 fe80::42:4cff:fed3:bbb/64 scope link 
           valid_lft forever preferred_lft forever
    30: veth602f36b@if29: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master docker0 state UP group default 
        link/ether 16:c8:f2:fc:08:ce brd ff:ff:ff:ff:ff:ff:link-netnsid 0
        inet6 fe80::14c8:f2ff:fefc:8ce/64 scope link 
           valid_lft forever preferred_lft forever
    ```
    It's different from the list inside the nymespace. It also has a loopback-interface with the name `lo`.
* Routing tables
  * Inside the Neimscape
    ``shell
    # sudo ip netns exec wwweb ip route
    default via 172.17.0.1 dev eth0 
    172.17.0.0/16 dev eth0 proto kernel scope link src 172.17.0.2
    ```
  * Inside the container
    ``shell
    # docker exec -ti wwweb ip route
    default via 172.17.0.1 dev eth0 
    172.17.0.0/16 dev eth0 proto kernel scope link src 172.17.0.2
    ```
  * Host route list
    ``shell
    # ip route
    default via 10.132.0.1 dev ens4 
    10.132.0.1 dev ens4 scope link 
    172.17.0.0/16 dev docker0 proto kernel scope link src 172.17.0.1
    ```
    The routing table is different
* Open ports
  * Inside the Neimscape
    ``shell
    # sudo ip netns exec wwweb netstat -an
    Active Internet connections (servers and established)
    Proto Recv-Q Send-Q Local Address Foreign Address State      
    tcp 0 0.0.0.0:80 0.0.0:* LISTEN     
    Active UNIX domain sockets (servers and established)
    Proto RefCnt Flags Type State I-Node Path
    unix 3 [ ] STREAM CONNECTED 54759    
    unix 3 [ ] STREAM CONNECTED 54758
    ```
  * On the host system
    ``shell
    # netstat -an
    Active Internet connections (servers and established)
    Proto Recv-Q Send-Q Local Address Foreign Address State      
    tcp 0 0.0.0.0:22 0.0.0.0:* LISTEN     
    tcp 0 0 10.132.0.2:47508 169.254.169.254:80 CLOSE_WAIT 
    tcp 0 0 10.132.0.2:47514 169.254.169.254:80 ESTABLISHED
    tcp 0 0 10.132.0.2:47512 169.254.169.254:80 ESTABLISHED
    tcp 0 316 10.132.0.2:22 176.62.181.4:36416 ESTABLISHED
    tcp 0 0 10.132.0.2:47510 169.254.169.254:80 ESTABLISHED
    tcp6 0 0 :::2376 :::* LISTEN     
    tcp6 0 0 :::22 :::* LISTEN     
    udp 0 0.0.0.0:68 0.0.0.0:*                          
    udp 0 0 172.17.0.1:123 0.0.0.0:*                          
    udp 0 0 10.132.0.2:123 0.0.0.0:*                          
    udp 0 0 127.0.0.1:123 0.0.0.0:*                          
    udp 0 0.0.0.0:123 0.0.0.0:*                          
    udp6 0 0 fe80::14c8:f2ff:fef:123 :::*                               
    udp6 0 0 fe80::42:4cff:fed3::123 :::*                               
    udp6 0 0 fe80::4001:aff:fe84:123 :::*                               
    udp6 0 0 ::1:123 :::*                               
    udp6 0 0 :::123 :::*                               
    ...
    ```
* A container is running with a `--network host` that doesn't use separate net namespace
  ``shell
  # docker run --rm --name wwwhost --network host -d nginx
  168c62352a51bcda9457f11480f935275202f51bab6232dd55e2edf8ee8f5245
  # docker ps
  CONTAINER ID IMAGE COMMAND CREATED STATUS PORTS NAMES
  168c62352a51 nginx "nginx -g 'daemon of..."   3 seconds ago Up 2 seconds wwwhost
  0e2ba62df689 nginx "nginx -g 'daemon of..."   38 minutes ago Up 38 minutes 80/tcp wwweb
  ```
  * List of open ports on the host system
    ``shell
    # netstat -pan
    Active Internet connections (servers and established)
    Proto Recv-Q Send-Q Local Address Foreign Address State PID/Program name
    tcp 0 0.0.0.0:80 0.0.0:* LISTEN 13390/nginx: master
    tcp 0 0.0.0.0:22 0.0.0.0:* LISTEN 1595/sshd       
    tcp 0 0 10.132.0.2:47556 169.254.169.254:80 CLOSE_WAIT 1581/python3    
    tcp 0 10.132.0.2:47562 169.254.169.254:80 ESTABLISHED 1581/python3    
    tcp 0 0 10.132.0.2:47560 169.254.169.254:80 ESTABLISHED 1553/python3    
    tcp 0 0 10.132.0.2:47558 169.254.169.254:80 ESTABLISHED 1580/python3    
    tcp 0 332 10.132.0.2:22 176.62.181.4:36416 ESTABLISHED 10854/sshd: vscoder
    tcp6 0 0 :::2376 :::* LISTEN 5528/dockerd    
    tcp6 0 0 :::22 :::* LISTEN 1595/sshd       
    udp 0 0.0.0.0:68 0.0.0.0:* 910/dhclient    
    udp 0 0 172.17.0.1:123 0.0.0.0:* 1550/ntpd       
    udp 0 0 10.132.0.2:123 0.0.0.0:* 1550/ntpd       
    udp 0 0 127.0.0.1:123 0.0.0.0:* 1550/ntpd       
    udp 0 0.0.0.0:123 0.0.0.0:* 1550/ntpd       
    udp6 0 0 fe80::14c8:f2ff:fef:123 :::* 1550/ntpd       
    udp6 0 0 fe80::42:4cff:fed3::123 :::* 1550/ntpd       
    udp6 0 0 fe80::4001:aff:fe84:123 :::* 1550/ntpd       
    udp6 0 0 ::1:123 :::* 1550/ntpd       
    udp6 0 0 :::123 :::* 1550/ntpd
    ...
    ```
    you can see that the nginx process is running on port 80.
  * Same command from the container
    ``shell
    # docker exec -ti wwwhost netstat -pan
    Active Internet connections (servers and established)
    Proto Recv-Q Send-Q Local Address Foreign Address State PID/Program name    
    tcp 0 0.0.0.0:80 0.0.0:* LISTEN 1/nginx: master pro 
    tcp 0 0.0.0.0:22 0.0.0.0:* LISTEN -                   
    tcp 0 0 10.132.0.2:47608 169.254.169.254:80 ESTABLISHED -                   
    tcp 0 0 10.132.0.2:35058 217.196.149.233:80 TIME_WAIT -                   
    tcp 0 0 10.132.0.2:39352 151.101.120.204:80 TIME_WAIT -                   
    tcp 0 0 10.132.0.2:39340 151.101.120.204:80 TIME_WAIT -                   
    tcp 0 0 10.132.0.2:52780 130.89.148.77:80 TIME_WAIT -                   
    tcp 0 0 10.132.0.2:47578 169.254.169.254:80 CLOSE_WAIT -                   
    tcp 0 0 10.132.0.2:34988 149.20.4.15:80 TIME_WAIT -                   
    tcp 0 0 10.132.0.2:39358 151.101.120.204:80 TIME_WAIT -                   
    tcp 0 0 10.132.0.2:47594 169.254.169.254:80 ESTABLISHED -                   
    tcp 0 0 10.132.0.2:39338 151.101.120.204:80 TIME_WAIT -                   
    tcp 0 0 10.132.0.2:39344 151.101.120.204:80 TIME_WAIT -                   
    tcp 0 0 10.132.0.2:22 176.62.181.4:36416 ESTABLISHED -                   
    tcp 0 0 10.132.0.2:34996 149.20.4.15:80 TIME_WAIT -                   
    tcp 0 0 10.132.0.2:34974 149.20.4.15:80 TIME_WAIT -                   
    tcp 0 0 10.132.0.2:35072 217.196.149.233:80 TIME_WAIT -                   
    tcp 0 0 10.132.0.2:47580 169.254.169.254:80 ESTABLISHED -                   
    tcp 0 0 10.132.0.2:39354 151.101.120.204:80 TIME_WAIT -                   
    tcp6 0 0 :::2376 :::* LISTEN -                   
    tcp6 0 0 :::22 :::* LISTEN -                   
    udp 0 0.0.0.0:68 0.0.0.0:* -                   
    udp 0 0 172.17.0.1:123 0.0.0.0:* -                   
    udp 0 0 10.132.0.2:123 0.0.0.0:* -                   
    udp 0 0 127.0.0.1:123 0.0.0.0:* -                   
    udp 0 0.0.0.0:123 0.0.0.0:* -                   
    udp6 0 0 fe80::14c8:f2ff:fef:123 :::* -                   
    udp6 0 0 fe80::42:4cff:fed3::123 :::* -                   
    udp6 0 0 fe80::4001:aff:fe84:123 :::* -                   
    udp6 0 0 ::1:123 :::* -                   
    udp6 0 0 :::123 :::* -
    ...
    ```
    You can see all the open ports of the host.

* Trying to intercept traffic
  * Two nginx containers were created
    ``shell
    docker run --rm --name wwweb1 -d nginx
    docker run --rm --name wwweb2 -d nginx
    ```
  * In the wwweb1 content, the periodic `curl` on wwweb2 is running.
    wwweb1:
    ``shell
    while sleep 1; do curl 172.17.0.2; done
    Ctrl+p Ctrl+q
    ```
  * The host system performs packet capturing on docker0 interface
    <details><summary><b>tcpdump</b></summary>.
    <p>

    ``shell
    # tcpdump -ni docker0 
    tcpdump: verbose output suppressed, use -v or -v for full protocol decode
    listening on docker0, link-type EN10MB (Ethernet), capture size 262144 bytes
    19:55:33.578680 IP 172.17.0.3.54102 > 172.17.0.2.80: Flags [S], seq 2237485892, win 29200, options [mss 1460,sackOK,TS val 4136154315 ecr 0,nop,wscale 7], length 0
    19:55:33.578763 IP 172.17.0.2.80 > 172.17.0.3.54102: Flags [S.], seq 3234450953, ack 2237485893, win 28960, options [mss 1460,sackOK,TS val 1810839543 ecr 4136154315,nop,wscale 7], length 0.
    19:55:33.578783 IP 172.17.0.3.54102 > 172.17.0.2.80: Flags [.], ack 1, win 229, options [nop,nop,TS val 4136154315 ecr 1810839543], length 0
    19:55:33.579042 IP 172.17.0.3.54102 > 172.17.0.2.80: Flags [P.], seq 1:75, ack 1, win 229, options [nop,nop,TS val 4136154315 ecr 1810839543], length 74: HTTP: GET / HTTP/1.1
    19:55:33.579059 IP 172.17.0.2.80 > 172.17.0.3.54102: Flags [.], ack 75, win 227, options [nop,nop,TS val 1810839543 ecr 4136154315], length 0
    19:55:33.579146 IP 172.17.0.2.80 > 172.17.0.3.54102: Flags [P.], seq 1:239, ack 75, win 227, options [nop,nop,TS val 1810839543 ecr 4136154315], length 238: HTTP: HTTP/1.1 200 OK
    19:55:33.579410 IP 172.17.0.2.80 > 172.17.0.3.54102: Flags [P.], seq 239:851, ack 75, win 227, options [nop,nop,TS val 1810839543 ecr 4136154315], length 612: HTTP
    19:55:33.582222 IP 172.17.0.3.54102 > 172.17.0.2.80: Flags [F.], seq 75, ack 851, win 247, options [nop,nop,TS val 4136154318 ecr 1810839543], length 0
    19:55:33.582351 IP 172.17.0.2.80 > 172.17.0.3.54102: Flags [F.], seq 851, ack 76, win 227, options [nop,nop,TS val 1810839546 ecr 4136154318], length 0
    19:55:33.582364 IP 172.17.0.3.54102 > 172.17.0.2.80: Flags [.], ack 852, win 247, options [nop,nop,TS val 4136154318 ecr 1810839546], length 0
    19:55:34.593306 IP 172.17.0.3.54104 > 172.17.0.2.80: Flags [S], seq 3311237005, win 29200, options [mss 1460,sackOK,TS val 4136155329 ecr 0,nop,wscale 7], length 0
    19:55:34.593393 IP 172.17.0.2.80 > 172.17.0.3.54104: Flags [S.], seq 1172657176, ack 3311237006, win 28960, options [mss 1460,sackOK,TS val 1810840557 ecr 4136155329,nop,wscale 7], length 0.
    19:55:34.593414 IP 172.17.0.3.54104 > 172.17.0.2.80: Flags [.], ack 1, win 229, options [nop,nop,TS val 4136155329 ecr 1810840557], length 0
    19:55:34.593738 IP 172.17.0.3.54104 > 172.17.0.2.80: Flags [P.], seq 1:75, ack 1, win 229, options [nop,nop,TS val 4136155330 ecr 1810840557], length 74: HTTP: GET / HTTP/1.1
    19:55:34.593754 IP 172.17.0.2.80 > 172.17.0.3.54104: Flags [.], ack 75, win 227, options [nop,nop,TS val 1810840558 ecr 4136155330], length 0
    19:55:34.593911 IP 172.17.0.2.80 > 172.17.0.3.54104: Flags [P.], seq 1:239, ack 75, win 227, options [nop,nop,TS val 1810840558 ecr 4136155330], length 238: HTTP: HTTP/1.1 200 OK
    19:55:34.594329 IP 172.17.0.2.80 > 172.17.0.3.54104: Flags [P.], seq 239:851, ack 75, win 227, options [nop,nop,TS val 1810840558 ecr 4136155330], length 612: HTTP
    19:55:34.594439 IP 172.17.0.3.54104 > 172.17.0.2.80: Flags [.], ack 239, win 237, options [nop,nop,TS val 4136155330 ecr 1810840558], length 0
    19:55:34.594493 IP 172.17.0.3.54104 > 172.17.0.2.80: Flags [.], ack 851, win 247, options [nop,nop,TS val 4136155330 ecr 1810840558], length 0
    19:55:34.597087 IP 172.17.0.3.54104 > 172.17.0.2.80: Flags [F.], seq 75, ack 851, win 247, options [nop,nop,TS val 4136155333 ecr 1810840558], length 0
    19:55:34.597247 IP 172.17.0.2.80 > 172.17.0.3.54104: Flags [F.], seq 851, ack 76, win 227, options [nop,nop,TS val 1810840561 ecr 4136155333], length 0
    19:55:34.597261 IP 172.17.0.3.54104 > 172.17.0.2.80: Flags [.], ack 852, win 247, options [nop,nop,TS val 4136155333 ecr 1810840561], length 0
    19:55:35.608138 IP 172.17.0.3.54106 > 172.17.0.2.80: Flags [S], seq 3998885043, win 29200, options [mss 1460,sackOK,TS val 4136156344 ecr 0,nop,wscale 7], length 0
    19:55:35.608228 IP 172.17.0.2.80 > 172.17.0.3.54106: Flags [S.], seq 1711094452, ack 3998885044, win 28960, options [mss 1460,sackOK,TS val 1810841572 ecr 4136156344,nop,wscale 7], length 0.
    19:55:35.608247 IP 172.17.0.3.54106 > 172.17.0.2.80: Flags [.], ack 1, win 229, options [nop,nop,TS val 4136156344 ecr 1810841572], length 0
    19:55:35.608587 IP 172.17.0.3.54106 > 172.17.0.2.80: Flags [P.], seq 1:75, ack 1, win 229, options [nop,nop,TS val 4136156344 ecr 1810841572], length 74: HTTP: GET / HTTP/1.1
    19:55:35.608602 IP 172.17.0.2.80 > 172.17.0.3.54106: Flags [.], ack 75, win 227, options [nop,nop,TS val 1810841573 ecr 4136156344], length 0
    19:55:35.608776 IP 172.17.0.2.80 > 172.17.0.3.54106: Flags [P.], seq 1:239, ack 75, win 227, options [nop,nop,TS val 1810841573 ecr 4136156344], length 238: HTTP: HTTP/1.1 200 OK
    19:55:35.609098 IP 172.17.0.2.80 > 172.17.0.3.54106: Flags [P.], seq 239:851, ack 75, win 227, options [nop,nop,TS val 1810841573 ecr 4136156344], length 612: HTTP
    19:55:35.609252 IP 172.17.0.3.54106 > 172.17.0.2.80: Flags [.], ack 239, win 237, options [nop,nop,TS val 4136156345 ecr 1810841573], length 0
    19:55:35.609309 IP 172.17.0.3.54106 > 172.17.0.2.80: Flags [.], ack 851, win 247, options [nop,nop,TS val 4136156345 ecr 1810841573], length 0
    19:55:35.611656 IP 172.17.0.3.54106 > 172.17.0.2.80: Flags [F.], seq 75, ack 851, win 247, options [nop,nop,TS val 4136156348 ecr 1810841573], length 0
    19:55:35.611775 IP 172.17.0.2.80 > 172.17.0.3.54106: Flags [F.], seq 851, ack 76, win 227, options [nop,nop,TS val 1810841576 ecr 4136156348], length 0
    19:55:35.611788 IP 172.17.0.3.54106 > 172.17.0.2.80: Flags [.], ack 852, win 247, options [nop,nop,TS val 4136156348 ecr 1810841576], length 0
    ^C
    34 packets captured
    36 packets received by filter
    2 packets dropped by kernel
    ```

    </p>
    </details>
    As a result, we see the periodic queries to 172.17.0.2.80 of 172.17.0.3, and the answers.
    Conclusion: the following possibility may be useful for diagnostics


#### USER namespace

Documentation on the topic https://docs.docker.com/engine/security/userns-remap/.
Known limitations https://docs.docker.com/engine/security/userns-remap/#user-namespace-known-limitations

One of the limitations:
This re-mapping is transparent to the container, but introduces some complexity in situations where the container needs access to resources on the Docker host, such as bind mounts into areas of the filesystem that the system user cannot write to.

Important about RHEL/CentOS
The way the namespace remapping is handled on the host is using two files, `/etc/subuid` and `/etc/subgid`. These files are typically managed automatically when you add or remove users or groups, but on a few distributions such as RHEL and CentOS 7.3, you may need to manage these files manually.

Example `/etc/subuid`:
```
testuser:231072:65536
```
This means that user-namespaced processes started by testuser are owned by host UID 231072 (which looks like UID 0 inside the namespace) through 296607 (231072 + 65536 - 1). These ranges should not overlap, to ensure that namespaced processes cannot access each other's namespaces.

About access to resources `/var/lib/docker`:
Enabling userns-remap effectively masks existing image and container layers, as well as other Docker objects within /var/lib/docker/. This is because Docker needs to adjust the ownership of these resources and actually stores them in a subdirectory within /var/lib/docker/. This is because Docker needs to adjust the ownership of these resources and actually stores them in a subdirectory within /var/lib/docker/. It is best to enable this feature on a new Docker installation rather than an existing one.

Along the same lines, if you disable userns-remap you can't access any of the resources created while it was enabled.


* In `/etc/docker/daemon.json, added `userns-remap' *
  `json
  {
    "userns-remap": "testuser"
  }
  ```
* docker restarted `systemctl restart docker *
* automatically created user `dockremap`
  ``shell
  # id dockremap
  uid=113(dockremap) gid=117(dockremap) groups=117(dockremap)
  # grep dockremap /etc/subuid
  dockremap:362144:65536
  # grep dockremap /etc/subgid
  dockremap:362144:65536
  ```
* previously uploaded images are not available
  ``shell
  # docker image ls
  REPOSITORY TAG IMAGE ID CREATED SIZE
  ```
* the container `hello-world` is running *
  ``shell
  # docker run hello-world
  Unable to find image 'hello-world:latest' locally
  latest: Pulling from library/hello-world
  1b930d010525: Pull complete 
  Digest: sha256:c3b4ada4687bbaa170745b3e4dd8ac3f194ca95b2d0518b417fb47e5879d9b5f
  Status: Downloaded newer image for hello-world:latest
  ...
  ```
  reload
* check for the namspace directory
  ``shell
  # sudo ls -ld /var/lib/docker/362144.362144/
  drwx-------- 14 362144 362144 4096 Nov 3 20:21 /var/lib/docker/362144.362144/
  ```
  and its contents
  ``shell
  # sudo ls -l /var/lib/docker/362144.362144/
  total 48
  drwx------ 2 root root 4096 Nov 3 20:21 builder
  drwx--x--x 4 root root 4096 Nov 3 20:21 buildkit
  drwx------ 3 362144 362144 4096 Nov 3 20:25
  drwx------ 3 root root 4096 Nov 3 20:21 image
  drwxr-x--- 3 root root 4096 Nov 3 20:21 network
  drwx------ 6 362144 362144 4096 Nov 3 20:25 overlay2
  drwx------ 4 root root 4096 Nov 3 20:21 plugins
  drwx------ 2 root root 4096 Nov 3 20:21 runtimes
  drwx------ 2 root root 4096 Nov 3 20:21 swarm
  drwx------ 2 362144 362144 4096 Nov 3 20:25 tmp
  drwx------ 2 root root 4096 Nov 3 20:21 trust
  drwx------ 2 362144 362144 4096 Nov 3 20:21
  ```
* Disable user ns for the content provider: `--userns=host' *
  There is a side effect when using this flag: user remapping will not be enabled for that container but, because the read-only (image layers) are shared between containers, the container filesystem will still be remapped.
  What this means is that the whole container filesystem will belong to the user specified in the `--userns-remap` daemon config (362144 in the example above). This can lead to unexpected behavior of programs inside the container. For instance sudo (which checks that its binaries belong to user 0) or binaries with a setuid flag.


#### Dockerfile

* The MongoDB config was created [docker-monolith/mongod.conf](docker-monolith/mongod.conf)
* The application launch script [docker-monolith/start.sh](docker-monolith/start.sh) is created
* The script with environment variable `DBATABASE_URL` [docker-monolith/db_config](docker-monolith/db_config) is created.

* Created by [docker-monolith/Dockerfile] (docker-monolith/Dockerfile)
  * Based on `ubuntu:16.04``
    ``dockerfile
    FROM ubuntu:16.04
    ```
  * Setting up the required packages
    ``dockerfile
    RUN apt-get update
    RUN apt-get install -y mongodb-server ruby-full ruby-dev build-essential git
    RUN gem install bundler
    ```
  * Application download
    ``dockerfile
    RUN git clone -b monolith https://github.com/express42/reddit.git
    ```
  * Copying the necessary files to the container
    ``dockerfile
    COPY mongod.conf /etc/mongod.conf
    COPY db_config /reddit/db_config
    COPY start.sh /start.sh
    ```
  * Setting application dependencies
    ``dockerfile
    RUN cd /reddit && bundle install
    RUN chmod 0777 /start.sh
    ```
  * application launcher
    ``dockerfile
    CMD ["/start.sh"]
    ```

* In [Makefile](Makefile) added a target that creates docker-machine instance
* The image was collected by `cd docker-monolith && docker build -t reddit:latest .` (you can also perform `docker build -t reddit:latest -f docker-monolith/Dockerfile ./docker-monolith` from the root of the repository).
* List of all images (including intermediate ones)
  ``shell
  # docker images -a 
  REPOSITORY TAG IMAGE ID CREATED SIZE
  reddit latest 0d1864425483 7 minutes ago 689MB
  <none> <none> 29597f97cbd2 7 minutes ago 689MB
  <none> <none> 6094762c8147 7 minutes ago 689MB
  <none> <none> 1030f7038c6a 8 minutes ago 645MB
  <none> <none> 1218af463fd2 8 minutes ago 645MB
  <none> <none> 8a7e652e5f9c 8 minutes ago 645MB
  <none> <none> f3eeecf3fe0f 8 minutes ago 645MB
  <none> <none> f7f5048a5c4c 8 minutes ago 645MB
  <none> <none> 6985497bf7cd 8 minutes ago 642MB
  <none> <none> e08fb2f1ff85 9 minutes ago 148MB
  ubuntu 16.04 5f2bf26e3524 3 days ago 123MB
  ```

#### Starting the container

* Container from image reddit `docker run --name reddit -d --network=host reddit:latest ` is started.
* Checking for application availability
  ``shell
  # docker-machine ls
  NAME ACTIVE DRIVER STATE URL SWARM DOCKER
  docker-host * google Running tcp://35.233.86.180:2376 v19.03.4
  ```
* When I tried to go to [http://35.233.86.180:9292/] (http://35.233.86.180:9292/), I couldn't open the page.
* A firewall rule has been created
  ``shell
  gcloud compute firewall-rules create reddit-app \
   --allow tcp:9292 \
   --target-tags=docker-machine \.
   -description="Allow PUMA connections" \
   --direction=INGRESS
  ```
  ``log
  Creating firewall... ⠶Created [https://www.googleapis.com/compute/v1/projects/docker-257914/global/firewalls/reddit-app].
  Creating firewall...done.
  NAME NETWORK DIRECTION PRIORITY ALLOW DENY DISABLED
  reddit-app default INGRESS 1000 tcp:9292 False
  ```
* Trying to open a site was a success *

### Docker hub

* Entered https://hub.docker.com/.
* Docker authorization on dockerhub `docker login ` is executed.
* docker-image uploaded to docker hub *
  ``shell
  # docker tag reddit:latest vscoder/otus-reddit:1.0
  # docker push vscoder/otus-reddit:1.0

  The push refers to repository [docker.io/vscoder/otus-reddit].
  9c56f25ab809: Pushed 
  9964405a2b79: Pushed 
  f3e1d374270d: Pushed 
  87badc7881a7: Pushed 
  dcc1149e9964: Pushed 
  bbeefc7b2d69: Pushed 
  038504099637: Pushed 
  28567395a615: Pushed 
  3c326a42d554: Pushed 
  bc72fb2e7b74: Mounted from library/ubuntu 
  903669ee7207: Mounted from library/ubuntu 
  a5a5f8c62487: Mounted from library/ubuntu 
  788b17b748c2: Mounted from library/ubuntu 
  1.0: digest: sha256:54828cee832eefa1a0379e4b128f7ce92ba0278c488686d8ba4ff3bdf2fc0c9d size: 3034
  ```
* An attempt has been made to run the image on the local docker
  ``shell
  docker run --name reddit -d -p 9292:9292 vscoder/otus-reddit:1.0
  ```
* The image was successfully downloaded from the docker hub and the application was launched
  ``shell
  curl 127.0.0.1:9292
  ```
* A number of checks have been carried out
  * `docker logs reddit -f ` follow the container logs
  * `docker exec -it reddit bash * run bash in the running container
    * `ps aux' process list
    * `killall5 1` send a SIGHUP signal to all applications
  * `docker start reddit' run the previously created container named `reddit'.
  * `docker stop reddit && docker rm reddit ` stop and remove container `reddit `
  * `docker run --name reddit --rm -it vscoder/otus-reddit:1.0 bash` download and start container `vscoder/otus-reddit:1.0` from docker hub, delete after stopping, in container start `bash` instead of instruction `CMD`.
    * `ps aux' process list
    * `exit' come out `bash' *
  # Checking that the container has been stopped and removed #
    ``shell
    # docker container ps -a
    CONTAINER ID IMAGE COMMAND CREATED STATUS PORTS NAMES
    03a9eea159ef ubuntu:16.04 "bash" 41 hours ago Up 21 hours wonderful_blackwell
    ```
* And also
  * `docker inspect vscoder/otus-reddit:1.0` see detailed image information
  * `docker inspect vscoder/otus-reddit:1.0 -f '{{{.ContainerConfig.Cmd}}'`default command at container start (directive `CMD` Dockerfile)
  * `docker run --name reddit -d -p 9292:9292 vscoder/otus-reddit:1.0` start container
  * `docker exec -it reddit bash * run bash in a container already running
    * `mkdir /test1234' create directory /test1234 (inside the container)
    * `touch /test1234/testfile` create the file /test1234/testfile
    * `rmdir /opt` remove the lyrics /opt
    * `exit' out of the container *
  * `docker diff reddit` to see the changes in the rewritable container layer
    ``shell
    C /tmp
    A /tmp/mongodb-27017.sock
    C /var
    C /var/log
    A /var/log/mongod.log
    C /var/lib
    C /var/lib/mongodb
    A /var/lib/mongodb/_tmp
    A /var/lib/mongodb/journal
    A /var/lib/mongodb/journal/j._0
    A /var/lib/mongodb/local.0
    A /var/lib/mongodb/local.ns
    A /var/lib/mongodb/mongod.lock
    C /root
    A /root/.bash_history
    A /test1234
    A /test1234/testfile
    D /opt
    ```
  * `docker stop reddit && docker rm reddit` stop and remove container
  * `docker run --name reddit --rm -it vscoder/otus-reddit:1.0 bash` restart container
  * `ls /` see the contents of the root directory.
    Since the container has been recreated, /test1234 is missing and /opt is in place.


### Task from \ ##: IaC using docker

#### Packer

* Necessary targets have been prepared in the [Makefile](Makefile).
* The [packer template](docker-monolith/packer/docker.json) and [wrapper script](docker-monolith/packer/scripts/ansible-playbook.sh) are created to prepare the base image.
* Created ansible-playbook [docker.yml] (docker-monolith/ansible/playbooks/docker.yml) for seeing through the packer image.
  Used galaxy-role `geerlingguy.docker`.
* The necessary files have been created
  * Updated dependencies in [requirements.txt](requirements.txt)
  * The configuration [ansible.cfg](docker-monolith/ansible/ansible.cfg) is created.
  * Added file with external dependencies ansible [requirements.yml](docker-monolith/ansible/inventory/requirements.yml)
* By means of packer prepared base image `make monolith_packer_build`

#### Terraform

#### Project-wide objects

* Added the required targets to the [Makefile](Makefile)
* With a terraform:
  * Created bucket to store the state of terraform
  * The projeckt-wide ssh key is set up
    ``shell
    make monolith_terraform_apply ENV=""
    ```

#### Modules

Created module [instance](docker-monolith/terraform/modules/instance/) describing abstract Goocle Compute Instance

Description of variables:

| Variable | Description | Default value | Type |
| ------------------- | --------------------------- | --------------------- | ------ |
| project | project ID | | string |
| region | region | europe-west1 | string |
| Zone | Zone | europe-west1-d | string |
| instance_disk_image | Instance base disk image | | string |.
| vpc_network_name | Network name | default | string |
| environment | environment name | | string |
| machine_type | Machine type | g1-small | string |
| tags | Tags list | [] | list |
| instance_count | instances count | 1 | int |
| name_prefix | Name prefix of instance | instance | strint |
| tcp_ports | TCP ports list to open list | [] | list |.


##### Stage environment

The stage infrastructure is in place. Features:
* The number of instances is taken from the variable `docker_app_instance_count`.
* Instance name prefix `docker_app_name_prefix`
* Tag list `docker_app_tags `
* List of tcp ports for firewall `docker_app_tcp_ports`

The description of other variables can be found in [variables.tf] (docker-monolith/terraform/stage/variables.tf).

#### Starting the container by means of ansible

* The role [docker-monolith/ansible/roles/reddit-monolith-docker] is created.
  Details in [docker-monolith/ansible/roles/reddit-monolith-docker/README.md] (docker-monolith/ansible/roles/reddit-monolith-docker/README.md)
* The use of a dynamic inverter `gcp_compute` is built.
* Dependencies `requirements.yml` are moved to [docker-monolith/ansible/environments/stage/requirements.yml](docker-monolith/ansible/environments/stage/requirements.yml).
* In [docker-monolith/terraform/modules/instance/main.tf] (docker-monolith/terraform/modules/instance/main.tf) added `labels` to `google_compute_instance`.
* Added playbook [reddit-app.yml](docker-monolith/ansible/playbooks/reddit-app.yml) for container deposition
* Added [Makefile](Makefile) targets
  
  | Purpose | Description |
  | ------------------------------- | ---------------------------------------------------- |
  | monolith_ansible_inventory_list | Show content of ansible-inventory in json format |.
  | monolith_ansible_lint | Run ansible-lint for all playbooks |.
  | monolith_ansible_syntax | Check the syntax of all playbooks |.
* Added [Makefile] [Makefile] target
  
  | Purpose | Description |
  | --------------------------- | ---------------------------------- |
  | monolith_ansible_reddit_app | Expand reddit-app in the container |.
* Added [Makefile](Makefile) targets
  
  | Purpose | Description |
  | ----------------------- | ----------------------------------------------------------------------------- |
  | monolith_docker_build | Collect a container from [docker-monolith/Dockerfile] |.
  | monolith_docker_publish | Download image `vscoder/otus-reddit:${IMAGE_VERSION}` to docker-hub |.
* In [README.md](README.md) added table of contents
* In [README.md](README.md) added test status for travis-ci

**IMPORTANT!!** To the file `.travis.yml` Was tokenized for slack notifications. To prevent spam notifications in the chat, the slack token was re-generated and written in `.travis.yml` in an encrypted form, as described in [instructions] (https://docs.travis-ci.com/user/notifications#configuring-slack-notifications).
``shell
travis encrypt "<account>:<token>" --add notifications.slack.rooms
```
Also, all brands were cleaned with `git filter-branch`.
``shell
# git filter-branch --tree-filter "sed -e's#slackchannel:slacktoken#faketoken#' -i .travis.yml" HEAD
### Got error, cuz in 1st commit .travis.yml does not exist!
Rewrite 9339a0dd566e037f747c991df6436dfb4ae6ee5 (1/59) (0 seconds passed, remaining 0 predicted) sed: you cannot read .travis.yml: No such file or directory.
tree filter failed: sed -e's#slackchannel:slacktoken#faketoken#' -i .travis.yml
# git filter-branch --tree-filter "sed -e's#slackchannel:slacktoken#faketoken#' -i .travis.yml || true" HEAD
### It WORKS!
Rewrite 9339a0dd566e037f747c991df6436dfb4ae6ee5 (1/59) (0 seconds passed, remaining 0 predicted) sed: you cannot read .travis.yml: No such file or directory.
Rewrite 4eb535e678dc189fb7fc8d6f0a0e967e2db2853d (59/59) (3 seconds passed, remaining 0 predicted)    
Ref 'refs/heads/docker-2' was rewritten
# git filter-branch --tree-filter "sed -e's#slackchannel:slacktoken#slackchannel:faketoken#' -i README.md || true" HEAD  
### Got error!
Cannot create a new backup.
A previous backup already exists in refs/original/
Force overwriting the backup with -f
# git filter-branch -f --tree-filter "sed -e's#slackchannel:slacktoken#slackchannel:faketoken#' -i README.md || true" HEAD
### It WORKS!
Rewrite 72dd8d0f6648a3432c086c0e803ade075c62d862 (53/59) (3 seconds passed, remaining 0 predicted)    
Ref 'refs/heads/docker-2' was rewritten
# git reflog expire --expire=now --all && git gc --prune=now --aggressive 
Counting objects: 569, it's done.
Delta compression using up to 12 threads.
Object compression: 100% (547/547), done.
Recording objects: 100% (569/569), done.
Total 569 (delta 323), reused 3 (delta 0).
# git push origin --force --all
Counting objects: 289, it's done.
Delta compression using up to 12 threads.
Object compression: 100% (188/188), done.
Recording objects: 100% (289/289), 68.17 KiB | 22.72 MiB/s, ready.
Total 289 (delta 140), reused 223 (delta 79)
Resolving deltas: 100% (140/140), done.
To github.com:Otus-DevOps-2019-08/vscoder_microservices.git.
 + 4eb535e...5503b94 docker-2 -> docker-2 (forced update)
```
After that, when trying to create a PR in the master, github generated an error There isn't anything to compare. **master** and **docker-2** are entirely different commit histories.
To fix the error, `git rebase master` was executed in the branch **docker-2**.
<details><summary> the result</summary>.
<p>

``log
First, rewinding head to replay your work on top of it...
Applying: Add PR template and travis checks
Applying: Update README.md. Add slack-integration description
Applying: Provide travis-ci notifications to slack
Applying: Add .gitignore
Applying: Add Makefile
Applying: Update README.md. Describe docker installation
Applying: Update README.md. Add descrioption
Applying: Update README.md. Add Makefile description
Applying: Describe some useful docker commands
Applying: Add output of dokcer inspect commands
Applying: Update README.md. Describe results docker inspect image
Applying: Update README.md. Describe dockker inspect container output
Applying: Describe image and container
Applying: Update README.md. Describe docker kill
Applying: Update README.md. Describe docker system df
Applying: Update README.md. Describe docker rm and rmi
Applying: Update README.md. Describe GCE initialisation
Applying: Update README.md. Describe docker-machine
Applying: Update README.md Describe PID and NET namespaces
Applying: Update README.md. Describe tcpdump
Applying: Update README.md. Describe USER namespaces
Applying: Fix README.md syntax
Applying: Move example json output files to examples/
Applying: Add files, to Dockerfile
Applying: Add Dockerfile
Applying: Update Makefile. Add target docker_machine_create
Applying: Update README.md. Describe docker image creation
Applying: Update README.md. Describe container run
Applying: Update README.md. Describe log in to docker hub
Applying: Update DEADME.md. Push image to docker hub
Applying: Update README.md. Describe some checks
Applying: Update MAkefile. Add target docker_machine_rm
Applying: Update .gitignore. Ignore all roles
Applying: Add packer-related Makefile
Applying: Add packer json template
Applying: Add an optional playbook to provide packer image
Applying: Add terraform-related Makefile
Applying: Add project-wide terraform infra
Applying: Add terraform module instance
Applying: Add terraform stage environment
Applying: Add role dreddit-monolith-docker
Applying: Use dynamic inventory gcp_plugin
Applying: Move requirements.yml
Applying: Add labels to terraform-created instances
Applying: Add playbook reddit-app.yml
Applying: Add ansible-related Makefile
Applying: Update README.md. Add security TODO
Applying: Update READEM.md. Docker bench security
Applying: Update README.md. Add useful link
Applying: Add Makefile target monolith_ansible_reddit_app
Applying: Add Makefile monolith_docker_build and monolith_docker_publish
Applying: Fix README.md syntax
Applying: Add TOC to README.md
Applying: Add travis-ci badger to README.md
Applying: Fix README.md syntax
Applying: Fix README.md syntax
Applying: Update Makefile target monolith_terraform_init
Applying: Regenerate and encrypt slack's travis-ci token
Applying: Update README.md. Describe git filter-branch
Applying: Add Makefile target install_requirements_dev
Applying: Add Makefile target install_requirements_virtualenv
Applying: Fix Makefile target install_requirements_virtualenv
Applying: Fix requirements.txt Install latest versions of docker-compose and ansible-lint
Applying: Add packer variables example
Applying: Add travis-ci tests
```

</p>
</details>

Then again `git push-force`

``log
Counting objects: 311, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (147/147), done.
Writing objects: 100% (311/311), 73.70 KiB | 10.53 MiB/s, done.
Total 311 (delta 156), reused 221 (delta 141)
Resolving deltas: 100% (156/156), done.
To github.com:Otus-DevOps-2019-08/vscoder_microservices.git.
 + 557c2fa...a1dbeab docker-2 -> docker-2 (forced update)
```

After that, it was possible to create a PR

Links to the subject:
- https://git-scm.com/docs/git-filter-branch
- https://habr.com/ru/post/76084/
- https://pro-prof.com/forums/topic/git-%D1%83%D0%B4%D0%B0%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5-%D1%84%D0%B0%D0%B9%D0%BB%D0%BE%D0%B2-%D0%B8%D0%B7-%D0%B2%D1%81%D0%B5%D1%85-%D0%BA%D0%BE%D0%BC%D0%BC%D0%B8%D1%82%D0%BE%D0%B2


### Outside of remote control: security

https://habr.com/ru/company/flant/blog/474012/

#### TODO:

[Docker Security Benchmark](https://github.com/docker/docker-bench-security)
- [ ] ! Automate the execution of Docker Security Benchmark in a separate role.
- [ ] Host operating system
- [ ] ?Audit rules.
- [ ] FIPS mode.
- [ ] [Docker Secrets] (https://docs.docker.com/engine/swarm/secrets/)
- [ ] ! The Docker configuration file (logging to the remote server) of the feature in a separate role
- [ ] Transport layer security (TLS when accessing API from outside)
- [ ] [Authorization plug-ins] (https://docs.docker.com/engine/extend/plugins_authorization/)
- [ ] !Daemon parameters -- check for startup.
  - [ ] `-live-restore''.
  - [ ] `--userland-proxy=false ]
  - [ ] ?-no-new-privileges?
  - [ ] `--seccomp-profile /path/to/profile'.
- [ ] [Seccomp](https://docs.docker.com/engine/security/seccomp/)

Configuration of containers and assembly files
- [ ] !User creation
- [ ] Remote access (deny access from the outside or protect with certificates)
- Isolate the username space.
- [ ] !Healthcheck!
- [ ] ?SELinux (AppArmor)
- [ ] !Network interfaces
- [ ] ?Cached versions of the images.
- [ ]Network bridge.
- [ ] ! Warning about the Docker socket.

- [Play with Docker] (https://training.play-with-docker.com/ops-stage2/) - see. section "Security".
- Found the role on ansible-galaxy [haxorof.docker_ce] (https://galaxy.ansible.com/haxorof/docker_ce). Take a look at it!
- Another article about [running the container under a current user] (https://medium.com/redbubble/running-a-docker-container-as-a-non-root-user-7d2e00f8ee15).

#### Docker Security Benchmark

The first run on the created host:
``shell
docker run -it --net host --pid host --userns host --cap-add audit_control \.
    -e DOCKER_CONTENT_TRUST=$DOCKER_CONTENT_TRUST \.
    -v /etc:/etc:ro \
    -v /usr/bin/docker-containerd:/usr/bin/docker-containerd:ro \.
    -v /usr/bin/docker-runc:/usr/bin/docker-runc:ro \.
    -v /usr/lib/systemd:/usr/lib/systemd:ro \.
    -v /var/lib:/var/lib:ro \.
    -v /var/run/docker.sock:/var/run/docker.sock:ro \.
    --label docker_bench_security \
    docker/docker-bench-security
```
<details><summary>CLICK ME</summary>.
<p>

``log
$ sudo docker run -it --net host --pid host --userns host --cap-add audit_control \.
> -e DOCKER_CONTENT_TRUST=$DOCKER_CONTENT_TRUST \.
> -v /etc:/etc:ro \.
> -v /usr/bin/docker-containerd:/usr/bin/docker-containerd:ro \.
> -v /usr/bin/docker-runc:/usr/bin/docker-runc:ro \.
> -v /usr/lib/systemd:/usr/lib/systemd:ro \.
> -v /var/lib:/var/lib:ro \.
> -v /var/run/docker.sock:/var/run/docker.sock:ro \.
> --label docker_bench_security \.
> docker/docker-bench-security
Unable to find image 'docker/docker-bench-security:latest' locally
Oh, yeah: Pulling from docker/docker-bench-security
cd784148e348: Pull complete 
48fe0d48816d: Pull complete 
164e5e0f48c5: Pull complete 
378ed37ea5ff: Pull complete 
Digest: sha256:ddbdf4f86af4405da4a8a7b7cc62bb63bfeb75e85bf22d2ece70c204d7cfabb8
Status: Downloaded newer image for docker/docker-bench-security:latest
# ------------------------------------------------------------------------------
# Docker Bench for Security v1.3.4
#
# Docker, Inc. (c) 2015-
#
# Checks for dozens of common best-practices around deploying Docker containers in production. #
# Inspired by the CIS Docker Community Edition Benchmark v1.1.0.
# ------------------------------------------------------------------------------

Initializing Sat Nov 9 06:52:32 UTC 2019


[INFO] 1 - Host Configuration
[WARN] 1.1 - Ensure a separate partition for containers has been created
[NOTE] 1.2 - Ensure the container host has been Hardened
[INFO] 1.3 - Ensure Docker is up to date
[INFO] * Using 19.03.4, verify it is up to date as deemed
[INFO] * Your operating system vendor can provide support and security maintenance for Docker
[INFO] 1.4 - Ensure only trusted users are allowed to control Docker daemon
[INFO] * docker:x:999
[WARN] 1.5 - Ensure auditing is configured for the Docker daemon
[WARN] 1.6 - Ensure auditing is configured for Docker files and directories - /var/lib/docker
[WARN] 1.7 - Ensure auditing is configured for Docker files and directories - /etc/docker
[INFO] 1.8 - Ensure auditing is configured for Docker files and directories - docker.service.
[INFO] * File not found
[INFO] 1.9 - Ensure auditing is configured for Docker files and directories - docker.socket.
[INFO] * File not found
[WARN] 1.10 - Ensure auditing is configured for Docker files and directories - /etc/default/docker
[INFO] 1.11 - Ensure auditing is configured for Docker files and directories - /etc/docker/daemon.json
[INFO] * File not found
[INFO] 1.12 - Ensure auditing is configured for Docker files and directories - /usr/bin/docker-containerd
[INFO] * File not found
[INFO] 1.13 - Ensure auditing is configured for Docker files and directories - /usr/bin/docker-runc
[INFO] * File not found


[INFO] 2 - Docker daemon configuration
[WARN] 2.1 - Ensure network traffic is restricted between containers on the default bridge
[PASS] 2.2 - Ensure the logging level is set to 'info'
[PASS] 2.3 - Ensure Docker is allowed to make changes to iptables
[PASS] 2.4 - Ensure insecure registries are not used
[PASS] 2.5 - Ensure aufs storage driver is not used
[INFO] 2.6 - Ensure TLS authentication for Docker daemon is configured
[INFO] * Docker daemon not listening on TCP
[INFO] 2.7 - Ensure the default ulimit is configured appropriately
[INFO] * Default ulimit doesn't appear to be set
[WARN] 2.8 - Enable user namespace support
[PASS] 2.9 - Ensure the default cgroup usage has been confirmed
[PASS] 2.10 - Ensure base device size is not changed until needed
[WARN] 2.11 - Ensure that authorization for Docker client commands is enabled
[WARN] 2.12 - Ensure centralized and remote logging is configured
[INFO] 2.13 - Ensure operations on legacy registry (v1) are Disabled (Deprecated)
[WARN] 2.14 - Ensure live restoration is Enabled
[WARN] 2.15 - Ensure Userland Proxy is Disabled
[PASS] 2.16 - Ensure daemon-wide custom seccomp profile is applied, if needed
[PASS] 2.17 - Ensure experimental features are avoided in production
[WARN] 2.18 - Ensure containers are restricted from acquiring new privileges


[INFO] 3 - Docker daemon configuration files
[INFO] 3.1 - Ensure that docker.service file is set to root:root
[INFO] * File not found
[INFO] 3.2 - Ensure that docker.service file permissions are set to 644 or more restrictive
[INFO] * File not found
[INFO] 3.3 - Ensure that docker.socket file is set to root:root
[INFO] * File not found
[INFO] 3.4 - Ensure that docker.socket file permissions are set to 644 or more restrictive
[INFO] * File not found
[PASS] 3.5 - Ensure that /etc/docker directory ownership is set to root:root
[PASS] 3.6 - Ensure that /etc/docker directory permissions are set to 755 or more restrictive
[INFO] 3.7 - Ensure that registry certificate file is set to root:root
[INFO] * Directory not found
[INFO] 3.8 - Ensure that registry certificate file permissions are set to 444 or more restrictive
[INFO] * Directory not found
[INFO] 3.9 - Ensure that TLS CA certificate file is set to root:root
[INFO] * No TLS CA certificate found
[INFO] 3.10 - Ensure that TLS CA certificate file permissions are set to 444 or more restrictive
[INFO] * No TLS CA certificate found
[INFO] 3.11 - Ensure that the Docker server certificate file is set to root:root
[INFO] * No TLS Server certificate found
[INFO] 3.12 - Ensure that Docker server certificate file permissions are set to 444 or more restrictive
[INFO] * No TLS Server certificate found
[INFO] 3.13 - Ensure that the Docker server certificate key file ownership is set to root:root
[INFO] * No TLS Key found
[INFO] 3.14 - Ensure that Docker server certificate key file permissions are set to 400
[INFO] * No TLS Key found
[PASS] 3.15 - Ensure that the Docker socket file ownership is set to root:docker
[PASS] 3.16 - Ensure that Docker socket file permissions are set to 660 or more restrictive
[INFO] 3.17 - Ensure that daemon.json file ownership is set to root:root
[INFO] * File not found
[INFO] 3.18 - Ensure that daemon.json file permissions are set to 644 or more restrictive
[INFO] * File not found
[PASS] 3.19 - Ensure that /etc/default/docker file is set to root:root
[PASS] 3.20 - Ensure that /etc/default/docker file permissions are set to 644 or more restrictive


[INFO] 4 - Container Images and Build File
[INFO] 4.1 - Ensure a user for the container has been created
[INFO] * No containers running
[NOTE] 4.2 - Ensure that containers use trusted base images
[NOTE] 4.3 - Ensure unnecessary packages are not installed in the container
[NOTE] 4.4 - Ensure images are scanned and rebuilt to include security patches
[WARN] 4.5 - Ensure Content trust for Docker is Enabled
[PASS] 4.6 - Ensure HEALTHCHECK instructions have been added to the container image
[PASS] 4.7 - Ensure update instructions are not used alone in the Dockerfile
[NOTE] 4.8 - Ensure setuid and setgid permissions are removed in the images
[INFO] 4.9 - Ensure COPY is used instead of ADD in Dockerfile
[INFO] * ADD in image history: [docker/docker-bench-security:latest]
[NOTE] 4.10 - Ensure secrets are not stored in Dockerfiles
[NOTE] 4.11 - Ensure verified packages are only Installed


[INFO] 5 - Container Runtime
[INFO] * No containers running, skipping Section 5


[INFO] 6 - Docker Security Operations
[INFO] 6.1 - Avoid image sprawl
[INFO] * There are now: 1 images
[INFO] 6.2 - Avoid container sprawl
[INFO] * There are currently a total of 1 containers, with 1 of them currently running


[INFO] 7 - Docker Swarm Configuration
[PASS] 7.1 - Ensure swarm mode is not Enabled, if not needed
[PASS] 7.2 - Ensure the minimum number of manager nodes have been created in a swarm (Swarm mode not enabled)
[PASS] 7.3 - Ensure swarm services are binded to a specific host interface (swarm mode not enabled)
[PASS] 7.4 - Ensure data exchanged between containers are encrypted on different nodes on the overlay network
[PASS] 7.5 - Ensure Docker's secret management commands are used for managing secrets in a Swarm cluster (Swarm mode not enabled)
[PASS] 7.6 - Ensure swarm manager is run in auto-lock mode (Swarm mode not enabled)
[PASS] 7.7 - Ensure swarm manager auto-lock key is rotated periodically (Swarm mode not enabled)
[PASS] 7.8 - Ensure node certificates are rotated as appropriate (Swarm mode not enabled)
[PASS] 7.9 - Ensure CA certificates are rotated as appropriate (Swarm mode not enabled)
[PASS] 7.10 - Ensure management plane traffic has been separated from data plane traffic (Swarm mode not enabled)

[INFO] Checks: 74
[INFO] Score: 12
appuser@reddit-docker-stage-001:~$
```

</p>
</details>

## HomeWork 13: Docker Images and Microservices

### Preparations

- Makefile target `install_hadolint` was created.

#### Dockerfile best practices (collapsed)

<details><summary>Dockerfile best practices</summary>.
<p>

https://docs.docker.com/develop/develop-images/dockerfile_best-practices/

#### FROM

https://docs.docker.com/develop/develop-images/#from

We recommend the Alpine image as it is tightly controlled and small in size (currently under 5 MB), while still being a full Linux distribution.

##### LABEL

https://docs.docker.com/develop/develop-images/#label

For each label, add a line beginning with LABEL and with one or more key-value pairs.

##### RUN

https://docs.docker.com/develop/develop-images/#run

Always combine RUN apt-get update with apt-get install in the same RUN statement. For example:
``Dockerfile
RUN apt-get update && apt-get install -y \.
    package-bar \
    package-baz \
    package-foo
```

You can also achieve cache-busting by specifying a package version. This is known as version pinning, for example:
``Dockerfile
RUN apt-get update && apt-get install -y \.
    package-bar \
    package-baz \
    package-foo=1.3.*
```

If you want the command to fail due to an error at any stage in the pipe, prepend set -o pipefail && to ensure that an unexpected error prevents the build from inadvertently succeeding. For example:
```Dockerfile
RUN set -o pipefail && wget -O - https://some.site | wc -l > /number
```

#### CMD

https://docs.docker.com/develop/develop-images/#cmd

`CMD` should almost always be used in the form of `CMD ["executable", "param1", "param2"...]`. Thus, if the image is for a service, such as Apache and Rails, you would run something like `CMD ["apache2", "-DFOREGROUND"]`.

`CMD` should rarely be used in the manner of `CMD ["param", "param"]` in conjunction with `ENTRYPOINT`.

#### EXPOSE

https://docs.docker.com/develop/develop-images/#expose

you should use the common, traditional port for your application
For example, an image containing the Apache web server would use `EXPOSE 80`, while an image containing MongoDB would use `EXPOSE 27017` and so on.
For container linking, Docker provides environment for the path from the recipient container back to the source (ie, `MYSQL_PORT_3306_TCP`).


##### ENV

https://docs.docker.com/develop/develop-images/#env

For example, `ENV PATH /usr/local/nginx/bin:$PATH` ensures that `CMD ["nginx"]` just works.

The `ENV` instruction is also useful for providing required environment specific to services you wish to containerize, such as Postgres's `PGDATA`.

Lastly, `ENV` instruction is also useful for providing required environment variables specific to services you wish to containerize, such as Postgres's `PGDATA` can also be used to set commonly used version numbers so that version bumps are easier to maintain. Similar to having constant variables in a program (as opposed to hard-coding values), this approach lets you change a single ENV instruction to auto-magically bump the version of the software in your container.

Each `ENV` line creates a new intermediate layer, just like `RUN` commands. This means that even if you unset the environment variable in a future layer, it still persists in this layer and its value can be dumped. To prevent this, and really unset the environment variable, use a RUN command with shell commands.

#### ADD or COPY

https://docs.docker.com/develop/develop-images/#add-or-copy

Although `ADD` and `COPY` are functionally similar, generally speaking, `COPY` is preferred. That's because it's more transparent than ADD. COPY only supports the basic copying of local files into the container, while ADD has some features (like local-only tar and remote URL support) that are not immediately obvious. 
Consequently, the best use for ADD is local tar file auto-extraction into the image, as in `ADD rootfs.tar.xz /`.

If you have multiple `Dockerfile` steps that use different files from your context, `COPY` them individually, rather than all at once.
For example:
``Dockerfile``.
COPY requirements.txt /tmp/
RUN pip install --requirement /tmp/requirements.txt
COPY . /tmp/
```
Results in fewer cache invalidations for the `RUN` step, than if you put the `COPY . /tmp/` before it.

Because image size matters, using ADD to fetch packages from remote URLs is strongly discouraged; you should use curl or wget instead. That way you can delete the files you no longer need after they've been extracted and you don't have to add another layer to your image.
do something like:
``Dockerfile
RUN mkdir -p /usr/src/things \.
    && curl -SL http://example.com/big.tar.xz \
    | tar -xJC /usr/src/things \.
    && make -C /usr/src/things all
```

#### ENTRYPOINT

https://docs.docker.com/develop/develop-images/#entrypoint

The best use for ENTRYPOINT is to set the image's main command, allowing that image to run as though it was that command (and then use CMD as the default flags).
```Dockerfile
ENTRYPOINT ["s3cmd"]
CMD ["--help"]
```

Postgres official image `ENTRYPOINT`
``shell
#!/bin/bash
set -e

if ["$1" = 'postgres' ]; then
    chown -R postgres "$PGDATA"

    if [ -z "$(ls -A "$PGDATA")" ]; then
        gosu postgres initdb
    fi

    exec gosu postgres "$@"
fi

exec "$@"
```

Configure app as PID 1
This script uses [the `exec` Bash command] (http://wiki.bash-hackers.org/commands/builtin/exec) so that the final running application becomes the container's `PID 1`. This allows the application to receive any Unix sent to the container. For more, see the [`ENTRYPOINT` reference] (https://docs.docker.com/engine/reference/builder/#entrypoint).

##### VOLUME

https://docs.docker.com/develop/develop-images/#volume

The VOLUME instruction should be used to expose any database storage area, configuration storage, or files/folders created by your docker container. You are strongly encouraged to use VOLUME for any mutable and/or user-serviceable parts of your image.

##### USER

https://docs.docker.com/develop/develop-images/dockerfile_best-practices/#user

If a service can run without privileges, use `USER` to change to a non-root user. Start by creating the user and group in the Dockerfile with something like 
``Dockerfile
RUN groupadd -r postgres && useradd --no-log-init -r -g postgres postgres
```

WARNING: [unresolved bug](https://github.com/golang/go/issues/13548)

Avoid installing or using `sudo` as it has unpredictable TTY and signal-forwarding behavior that can cause problems. If you absolutely need functionality similar to `sudo`, such as initializing the daemon as root but running it as non-root, consider using ``gosu`.

#### WORKDIR

https://docs.docker.com/develop/develop-images/#workdir

For clarity and reliability, you should always use absolute paths for your `WORKDIR`. Also, you should use `WORKDIR` instead of proliferating instructions like `RUN cd ... && do-something`, which are hard to read, troubleshoot, and maintain.

##### ONBUILD

https://docs.docker.com/develop/develop-images/#onbuild

An `ONBUILD` command executes after the current `Dockerfile` build completes. `ONBUILD` executes in any child image derived FROM the current image. Think of the `ONBUILD` command as an instruction the parent `Dockerfile` gives to the child `Dockerfile`.
`ONBUILD` is useful for images that are going to be built `FROM` a given image.
[Ruby's ONBUILD variants] (https://github.com/docker-library/ruby/blob/c43fef8a60cea31eb9e7d960a076d633cb62ba8d/2.4/jessie/onbuild/Dockerfile)
Images built with `ONBUILD` should get a separate tag, for example: `Ruby:1.9-onbuild` or `Ruby:2.0-onbuild`.

</p>
</details>

### Starting

#### New application structure

- Downloaded and unpacked archive [microservices.zip] (https://github.com/express42/reddit/archive/microservices.zip).
  ``shell
  wget https://github.com/express42/reddit/archive/microservices.zip && \
    unzip microservices.zip && \
    rm microservices.zip
  ```
- The `reddit-microservices` catalogue has been renamed `src`.
  ``shell
  mv reddit-microservices src
  ```
- The [src/post-py/Dockerfile] file was created.
- In [src/post-py/Dockerfile] (src/post-py/Dockerfile) the working directory is parameterized.
- The [src/comment/Dockerfile] file was created.
- The [src/ui/Dockerfile](src/ui/Dockerfile) file was created.
- Last MongoDB image downloaded
  ``shell
  docker pull mongo:latest
  ```
- Prepared by [Makefile](src/Makefile) with a set of frequently used actions

#### Assembly of images

- The compilation of the `post-py` image ended with an error.
  ``log
  It's impossible to execute 'gcc': No such file or directory
  error: command 'gcc' failed with exit status 1
  ```
- The image of comment `make build_comment` has been collected.
- The image of ui `make build_ui` has been collected.

- The problem with `post-py` has been solved as follows.
  ``Dockerfile
  RUN apk add --no-cache --virtual .build-deps build-base \.
    &&ip install -r $APP_HOME/requirements.txt \
    && apk del .build-deps
  ```
  Before installing `requirements.txt`, the package `build-base` is installed. After installing `requirements.txt`, all packages needed for the build are removed. This all happens within one `RUN` instruction so that you don't create an extra layer with dependencies installed.

Building `ui` didn't start with the first step because the layer with the installed `build-essential` package was already created during the build phase of `comment` and now was taken from build-cache instead of building from scratch.

#### Starting the application

The work is carried out in the directory [src/](src/)

- All the images `make build_all` have been collected.
- In [Makefile](src/Makefile) added target `run_all`, which is
  - Creates a network `${REDDIT_NETWORK_NAME}`.
  - Runs containers in the network `${REDDIT_NETWORK_NAME} ` from images
    - `mongodb:latest`
    - `${DOCKERHUB_LOGIN}/post:${POST_VERSION}`.
    - `${DOCKERHUB_LOGIN}/comment:${COMMENT_VERSION}`.
    - `${DOCKERHUB_LOGIN}/ui:${UI_VERSION}`.
- In [Makefile](src/Makefile) added target `kill_all`, which is
  - Kills all running containers (**WARNING**: everything at all! What the warning with possibility of cancellation is given out).
  - Removes network `${REDDIT_NETWORK_NAME}`.
- The network is created and containers `make run_all` are started.
- Go to http://127.0.0.1:9292.
- We managed to write the post
- All killed `make kill_all`.

### Task from \ ##: Redefining network aliases

#### Theory

https://docs.docker.com/engine/reference/commandline/run/#set-environment-variables--e---env---env-file

Use the `-e, `--env, and `--env-file` flags to set simple (non-array) environment variables in the container you're running, or overwrite variables that are defined in the Dockerfile of the image you're running.

``shell
$ docker run --env VAR1=value1 --env VAR2=value2 ubuntu env | grep VAR
VAR1=value1
VAR2=value2
```

``shell
export VAR1=value1
export VAR2=value2

$ docker run --env VAR1 --env VAR2 ubuntu env | grep VAR
VAR1=value1
VAR2=value2
```

``shell
$ cat env.list
# This is a comment
VAR1=value1
VAR2=value2
USER

$ docker run --env-file env.list ubuntu env | grep VAR
VAR1=value1
VAR2=value2
USER=denis
```

#### Implementation

Creating a network and running containers with other aliases and variable overrides
``shell
docker network create reddit
docker run -d --network=reddit \.
  --network-alias=posts_db1 \.
  --network-alias=comment_db1 \.
  mongo:latest
docker run -d --network=reddit \.
  --network-alias=post1 \.
  --env POST_DATABASE_HOST=posts_db1 \.
  vscoder/post:1.0
docker run -d --network=reddit \
  --network-alias=comment1 \.
  --env COMMENT_DATABASE_HOST=comment_db1 \.
  vscoder/comment:1.0
docker run -d --network=reddit \
  --env POST_SERVICE_HOST=post1 \.
  --env COMMENT_SERVICE_HOST=comment1 \.
  -p 9292:9292 \
  vscoder/ui:1.0
```

The network is set up, the containers are running. The application has been tested.

### Images

List of images `docker images`

``shell
REPOSITORY TAG IMAGE ID CREATED SIZE
vscoder/ui 1.0 aacf973cbc5d About an hour ago 772MB
vscoder/comment 1.0 188232c05d67 About an hour ago 770MB
vscoder/post 1.0 f22acc632909 About an hour ago 109MB
reddit latest fce89963a387 5 days ago 691MB
vscoder/otus-reddit 1.0 fce89963a387 5 days ago 691MB
mongo latest 965553e202a4 2 weeks ago 363MB
ubuntu 16.04 5f2bf26e3524 2 weeks ago 123MB
ruby 2.2 6c8e6f9667b2 18 months ago 715MB
python 3.6.0-alpine cb178ebbf0f2 2 years ago 88.6MB
```

- Reduced `ui`, due to the re-assembly based on `ubuntu:16.04`. New [Dockerfile](src/ui/Dockerfile)
- In [Makefile](src/Makefile) the version ui is changed to 2.0.
- The image was rebuilt by `make build_ui`.

List of images `docker images`

``shell
REPOSITORY TAG IMAGE ID CREATED SIZE
vscoder/ui 2.0 ebb79fd1384f 2 minutes ago 458MB
vscoder/ui 1.0 aacf973cbc5d About an hour ago 772MB
vscoder/comment 1.0 188232c05d67 About an hour ago 770MB
vscoder/post 1.0 f22acc632909 About an hour ago 109MB
reddit latest fce89963a387 5 days ago 691MB
vscoder/otus-reddit 1.0 fce89963a387 5 days ago 691MB
mongo latest 965553e202a4 2 weeks ago 363MB
ubuntu 16.04 5f2bf26e3524 2 weeks ago 123MB
ruby 2.2 6c8e6f9667b2 18 months ago 715MB
python 3.6.0-alpine cb178ebbf0f2 2 years ago 88.6MB
```

### Task from \ ##: Decrease the size of the image.

#### Analysis

References:

- [Official wiki](https://wiki.alpinelinux.org/wiki)
- [Article on habr](https://habr.com/ru/company/digdes/blog/415279/)
- [Article on habr](https://habr.com/ru/company/digdes/blog/440658/)
- [Getting the most from Docker. Microcontainers and Alpine Linux] (https://youtu.be/ClX9jbiVLaY)
- Image Research Utility [dive] (https://github.com/wagoodman/dive)
  Example of use:
  - For interactive analysis
    ``shell
    docker run --rm -it \
      -v /var/run/docker.sock:/var/run/docker.sock \.
      wagoodman/dive:latest <ui image id>
    ```
  - For integration with CI
    ``shell
    docker run --rm -it \
      -v /var/run/docker.sock:/var/run/docker.sock \.
      -e CI=true \
      wagoodman/dive:latest <ui image id>
    ```

Solution options:

- Images based on alpine-linux. 
  - '+' Very efficient (results below) due to a minimalistic base image.
  - '-' Difficulties may occur if there are no packages in the repository.
- Images based on [scratch] (https://hub.docker.com/_/scratch), i.e. on an empty image
  - '+' A few megabytes more efficient than alpine-linux.
  - '-' Makes it very difficult to maintain images.
- Using intermediate images, Multistage assembly.
  - '+' Allows all dependencies needed to build an executable to be contained in a separate image. It is mainly used to compile executable files and then copy them to the final image.
  - '-' Difficult to maintain. Difficult to use in some cases (e.g. for interpreted languages).
  - For the images used (python and ruby), you can set the dependencies needed for the compilation in the intermediate image, set the application dependencies (`pip' or `bundle'), retrieve the added files with `dive' and copy them to the final image. But this ** overwhelmingly** will make it harder to maintain the image, making the possible benefit insignificant.

Conclusions:

The most effective solution would be to use images based on alpine-linux applications

#### Assembly based on alpine linux

##### ui

- The image has been rebuilt on the basis of `Ruby:2.2-alpine`. The installation of dependencies required the installation of `build-base'. Installing `build-base`, setting dependencies and deleting `build-base` is done with one `RUN` instruction to avoid creating unnecessary images.
``Dockerfile`.
FROM ruby:2.2-alpine

ENV POST_SERVICE_HOST post
ENV POST_SERVICE_PORT 5000
ENV COMMENT_SERVICE_HOST comment
ENV COMMENT_SERVICE_PORT 9292
ENV APP_HOME /app

RUN mkdir $APP_HOME
WORKDIR $APP_HOME
COPY Gemfile* $APP_HOME/

RUN apk add --no-cache --virtual .build-deps build-base \.
    && bundle install \
    && apk del .build-deps

COPY . $APP_HOME

CMD ["puma"]
```
- Amount taken reduced `docker images | grep vscoder/ui`.
``log
vscoder/ui 3.0 25f038173527 13 minutes ago 158MB
vscoder/ui 2.0 ebb79fd1384f 4 hours ago 458MB
vscoder/ui 1.0 aacf973cbc5d 6 hours ago 772MB
```
- The result of work `dive `
  ``shell
  make dive_ui
  docker run --rm -it \
          -v /var/run/docker.sock:/var/run/docker.sock \.
          -e CI=true \
          wagoodman/dive:latest $(docker images -q vscoder/ui:3.0)
  ```

<details><summary> the result</summary>.
<p>

``log
Image Source: docker://7d3825b1f360
Fetching image... (this can take a while for large images)
Analyzing image...
  efficiency: 99.4482%

  892115 bytes (892 kB)

  userWastedPercent: 0.5820%

Inefficient Files:
Count Wasted Space File Path
    3 324 kB /lib/apk/db/installed
    2 113 kB /bin/ps
    2 83 kB /usr/bin/top
    2 70 kB /usr/bin/bunzip2
    2 70 kB /usr/bin/bzip2
    2 70 kB /usr/bin/bzcat
    3 32 kB /lib/apk/db/scripts.tar
    2 26 kB /usr/bin/pmap
    2 22 kB /usr/bin/pgrep
    2 22 kB /usr/bin/pkill
    2 18 kB /sbin/sysctl
    2 14 kB /usr/bin/free
    2 10 kB /usr/bin/uptime
    2 9.9 kB /usr/bin/pwdx
    2 3.7 kB /app/Gemfile.lock
    3 500 B /lib/apk/db/triggers
    2 474 B /app/Gemfile
    3 181 B /etc/apk/world
    2 0 B /usr/bin/sort
    2 0 B /usr/bin/test
    2 0 B /usr/bin/fold
    2 0 B /usr/bin/tail
    2 0 B /usr/bin/tac
    2 0 B /usr/bin/sum
    3 0 B /usr/bin/strings
    2 0 B /usr/bin/split
    2 0 B /usr/bin/timeout
    2 0 B /usr/bin/shuf
    2 0 B /usr/bin/sha512sum
    2 0 B /usr/bin/sha256sum
    2 0 B /usr/bin/sha1sum
    2 0 B /usr/bin/seq
    2 0 B /usr/bin/realpath
    2 0 B /usr/bin/readlink
    2 0 B /usr/bin/tr
    2 0 B /usr/bin/printf
    2 0 B /usr/bin/truncate
    2 0 B /usr/bin/tty
    2 0 B /usr/bin/unexpand
    2 0 B /usr/bin/od
    2 0 B /usr/bin/nohup
    2 0 B /usr/bin/mkfifo
    2 0 B /usr/bin/md5sum
    2 0 B /usr/bin/lzma
    2 0 B /usr/bin/lzcat
    2 0 B /usr/bin/install
    2 0 B /usr/bin/id
    2 0 B /usr/bin/hostid
    2 0 B /usr/bin/head
    2 0 B /usr/bin/groups
    2 0 B /usr/bin/uniq
    2 0 B /usr/bin/tee
    2 0 B /usr/bin/expr
    2 0 B /usr/bin/expand
    2 0 B /usr/bin/env
    2 0 B /usr/bin/du
    2 0 B /usr/bin/dirname
    2 0 B /usr/bin/cut
    2 0 B /usr/bin/comm
    2 0 B /usr/bin/cksum
    2 0 B /usr/bin/unlink
    2 0 B /usr/bin/unlzma
    2 0 B /usr/bin/unxz
    2 0 B /usr/bin/basename
    2 0 B /usr/bin/[
    3 0 B /tmp
    2 0 B /usr/bin/wc
    2 0 B /root
    2 0 B /usr/bin/whoami
    2 0 B /usr/bin/xzcat
    3 0 B /lib/apk/db/lock
    2 0 B /usr/bin/yes
    2 0 B /usr/sbin/chroot
    2 0 B /bin/uname
    2 0 B /bin/true
    2 0 B /bin/touch
    2 0 B /bin/tar
    2 0 B /bin/sync
    2 0 B /bin/style
    2 0 B /bin/stat
    2 0 B /bin/sleep
    2 0 B /bin/rmdir
    2 0 B /bin/rm
    2 0 B /bin/pwd
    3 0 B /var/cache/misc
    2 0 B /bin/printenv
    2 0 B /bin/nice
    2 0 B /bin/mv
    2 0 B /bin/mktemp
    2 0 B /bin/mknod
    2 0 B /bin/mkdir
    2 0 B /bin/ls
    2 0 B /bin/ln
    2 0 B /bin/false
    2 0 B /bin/echo
    2 0 B /bin/df
    2 0 B /bin/dd
    2 0 B /bin/date
    2 0 B /bin/cp
    2 0 B /bin/chown
    2 0 B /bin/chmod
    2 0 B /bin/chgrp
    2 0 B /bin/cat
    2 0 B /bin/base64
Results:
  PASS: highestUserWastedPercent
  SKIP: highestWastedBytes: rule disabled
  PASS: lowestEfficiency
Result:PASS [Total:3] [Passed:2] [Failed:0] [Warn:0] [Skipped:1].
```

</p>
</details>

- On step of installation of dependences, cache clearing `bundle clean` has been added that has allowed to reduce the final image on 1Mb.
  ``shell``.
  # docker images vscoder/ui  
  REPOSITORY TAG IMAGE ID CREATED SIZE
  vscoder/ui 3.0-alpine f54689080dbe 17 minutes ago 157MB
  vscoder/ui 3.0 7d3825b1f360 2 hours ago 158MB
  vscoder/ui 2.0 ebb79fd1384f 26 hours ago 458MB
  vscoder/ui 1.0 aacf973cbc5d 28 hours ago 772MB
  ```

#### comment

- Dockerfile
``Dockerfile
FROM ruby:2.2-alpine

ENV COMMENT_DATABASE_HOST comment_db
ENV COMMENT_DATABASE comments
ENV APP_HOME /app

RUN mkdir $APP_HOME
WORKDIR $APP_HOME

# Application requiremets (fat layer)
COPY Gemfile* $APP_HOME/
RUN apk add --no-cache --virtual .build-deps build-base \.
    && bundle install \
    && apk del .build-deps

# Application (frequently changing layer)
COPY . $APP_HOME

CMD ["puma"]
```

- Size `docker images | grep vscoder/comment`
``log
vscoder/comment 2.0 a85ccabc510d 15 seconds ago 156MB
vscoder/comment 1.0 188232c05d67 6 hours ago 770MB
```
- The result of the work `dive`
  ``shell
  # make dive_comment 
  docker run --rm -it \
          -v /var/run/docker.sock:/var/run/docker.sock \.
          -e CI=true \
          wagoodman/dive:latest $(docker images -q vscoder/comment:2.0)
  ```
<details><summary> the result</summary>.
<p>

``log
  Using default CI config
Image Source: docker://a85ccabc510d
Fetching image... (this can take a while for large images)
Analyzing image...
  efficiency: 99.4405 %

  890157 bytes (890 kB)

  userWastedPercent: 0.5898%

Inefficient Files:
Count Wasted Space File Path
    3 324 kB /lib/apk/db/installed
    2 113 kB /bin/ps
    2 83 kB /usr/bin/top
    2 70 kB /usr/bin/bunzip2
    2 70 kB /usr/bin/bzip2
    2 70 kB /usr/bin/bzcat
    3 32 kB /lib/apk/db/scripts.tar
    2 26 kB /usr/bin/pmap
    2 22 kB /usr/bin/pgrep
    2 22 kB /usr/bin/pkill
    2 18 kB /sbin/sysctl
    2 14 kB /usr/bin/free
    2 10 kB /usr/bin/uptime
    2 9.9 kB /usr/bin/pwdx
    2 1.8 kB /app/Gemfile.lock
    3 500 B /lib/apk/db/triggers
    2 364 B /app/Gemfile
    3 181 B /etc/apk/world
    2 0 B /usr/bin/sort
    2 0 B /usr/bin/test
    2 0 B /usr/bin/fold
    2 0 B /usr/bin/tail
    2 0 B /usr/bin/tac
    2 0 B /usr/bin/sum
    3 0 B /usr/bin/strings
    2 0 B /usr/bin/split
    2 0 B /usr/bin/timeout
    2 0 B /usr/bin/shuf
    2 0 B /usr/bin/sha512sum
    2 0 B /usr/bin/sha256sum
    2 0 B /usr/bin/sha1sum
    2 0 B /usr/bin/seq
    2 0 B /usr/bin/realpath
    2 0 B /usr/bin/readlink
    2 0 B /usr/bin/tr
    2 0 B /usr/bin/printf
    2 0 B /usr/bin/truncate
    2 0 B /usr/bin/tty
    2 0 B /usr/bin/unexpand
    2 0 B /usr/bin/od
    2 0 B /usr/bin/nohup
    2 0 B /usr/bin/mkfifo
    2 0 B /usr/bin/md5sum
    2 0 B /usr/bin/lzma
    2 0 B /usr/bin/lzcat
    2 0 B /usr/bin/install
    2 0 B /usr/bin/id
    2 0 B /usr/bin/hostid
    2 0 B /usr/bin/head
    2 0 B /usr/bin/groups
    2 0 B /usr/bin/uniq
    2 0 B /usr/bin/tee
    2 0 B /usr/bin/expr
    2 0 B /usr/bin/expand
    2 0 B /usr/bin/env
    2 0 B /usr/bin/du
    2 0 B /usr/bin/dirname
    2 0 B /usr/bin/cut
    2 0 B /usr/bin/comm
    2 0 B /usr/bin/cksum
    2 0 B /usr/bin/unlink
    2 0 B /usr/bin/unlzma
    2 0 B /usr/bin/unxz
    2 0 B /usr/bin/basename
    2 0 B /usr/bin/[
    3 0 B /tmp
    2 0 B /usr/bin/wc
    2 0 B /root
    2 0 B /usr/bin/whoami
    2 0 B /usr/bin/xzcat
    3 0 B /lib/apk/db/lock
    2 0 B /usr/bin/yes
    2 0 B /usr/sbin/chroot
    2 0 B /bin/uname
    2 0 B /bin/true
    2 0 B /bin/touch
    2 0 B /bin/tar
    2 0 B /bin/sync
    2 0 B /bin/style
    2 0 B /bin/stat
    2 0 B /bin/sleep
    2 0 B /bin/rmdir
    2 0 B /bin/rm
    2 0 B /bin/pwd
    3 0 B /var/cache/misc
    2 0 B /bin/printenv
    2 0 B /bin/nice
    2 0 B /bin/mv
    2 0 B /bin/mktemp
    2 0 B /bin/mknod
    2 0 B /bin/mkdir
    2 0 B /bin/ls
    2 0 B /bin/ln
    2 0 B /bin/false
    2 0 B /bin/echo
    2 0 B /bin/df
    2 0 B /bin/dd
    2 0 B /bin/date
    2 0 B /bin/cp
    2 0 B /bin/chown
    2 0 B /bin/chmod
    2 0 B /bin/chgrp
    2 0 B /bin/cat
    2 0 B /bin/base64
Results:
  PASS: highestUserWastedPercent
  SKIP: highestWastedBytes: rule disabled
  PASS: lowestEfficiency
Result:PASS [Total:3] [Passed:2] [Failed:0] [Warn:0] [Skipped:1].
```

</p>
</details>

- On step of installation of dependences, cache clearing `bundle clean` has been added that has allowed to reduce the final image on 1Mb.
  ``shell``.
  # docker images vscoder/comment
  REPOSITORY TAG IMAGE ID CREATED SIZE
  vscoder/comment 2.0-alpine 333b8da781a5 17 minutes ago 156MB
  vscoder/comment 2.0 a85ccabc510d 22 hours ago 156MB
  vscoder/comment 1.0 188232c05d67 28 hours ago 770MB
  ```

#### post

- The post image was originally alpine based, so no modification was required.
  ``shell
  # docker images vscoder/post
  REPOSITORY TAG IMAGE ID CREATED SIZE
  vscoder/post 1.0 f22acc632909 27 hours ago 109MB
  ```
- The result of work `dive `
  ``shell
  make dive_post 
  docker run --rm -it \
          -v /var/run/docker.sock:/var/run/docker.sock \.
          -e CI=true \
          wagoodman/dive:latest $(docker images -q vscoder/post:1.0)
  ```
<details><summary> the result</summary>.
<p>

``log
  Using default CI config
Image Source: docker://f22acc632909
Fetching image... (this can take a while for large images)
Analyzing image...
  efficiency: 98.7017%

  2357680 bytes (2.4 MB)

  userWastedPercent: 2.2600%

Inefficient Files:
Count Wasted Space File Path
    2 1.1 MB /lib/ld-musl-x86_64.so.1
    2 549 kB /etc/ssl/certs/ca-certificates.crt
    4,465 kB /lib/apk/db/installed
    2 73 kB /usr/bin/getent
    2 63 kB /usr/bin/getconf
    4 45 kB /lib/apk/db/scripts.tar
    2 41 kB /usr/bin/iconv
    4,812 B /lib/apk/db/triggers
    2 786 B /sbin/ldconfig
    4 284 B /etc/apk/world
    2,216 B /app/requirements.txt
    2 0 B /usr/bin/unlzma
    3 0 B /usr/bin/strings
    2 0 B /usr/bin/lzma
    2 0 B /usr/bin/lzcat
    3 0 B /tmp
    2 0 B /root
    2 0 B /usr/bin/xzcat
    2 0 B /bin/tar
    4 0 B /var/cache/misc
    2 0 B /lib/apk/db/lock
    2 0 B /lib/libc.musl-x86_64.so.1
    2 0 B /usr/bin/ldd
    2 0 B /usr/bin/unxz
Results:
  PASS: highestUserWastedPercent
  SKIP: highestWastedBytes: rule disabled
  PASS: lowestEfficiency
Result:PASS [Total:3] [Passed:2] [Failed:0] [Warn:0] [Skipped:1].
```

</p>
</details>

- When setting dependencies, the option `--no-cache-dir' was added to `pip', which reduced the final image by 3MB.
  ``shell
  # docker images vscoder/post
  REPOSITORY TAG IMAGE ID CREATED SIZE
  vscoder/post 2.0-alpine 6cadaa2065a7 2 minutes ago 106MB
  vscoder/post 1.0 f22acc632909 28 hours ago 109MB
  ```

### Next steps

#### Performance check

- To the tags of images added suffix `-alpine `
- All images have been rebuilt `make build_all`.
- Previously running instances `make kill_all` are stopped.
- The containers have been restarted based on fresh images `make run_all`.
- Performance verified. The post was created successfully. Previously created post did not dry up.

#### Creating volume for MongoDB

- In Makefile target run_all added creation of volume in case of absence of
  ``shell
  docker volume inspect ${REDDIT_DB_VOLUME_NAME} 1>/dev/null || docker volume create ${REDDIT_DB_VOLUME_NAME}
  ```
- In the Makefile target run_all when creating a container with mongodb the volume is mounted
  ``Makefile
  -v reddit_db:/data/db
  ```
- The result is that the Makefile target run_all looks like this:
  ```Makefile
  run_all:
	docker network inspect ${REDDIT_NETWORK_NAME} 1>/dev/null || docker network create ${REDDIT_NETWORK_NAME}
	docker volume inspect ${REDDIT_DB_VOLUME_NAME} 1>/dev/null || docker volume create ${REDDIT_DB_VOLUME_NAME}
	docker run -d --network=${REDDIT_NETWORK_NAME} \
		--network-alias=post_db \.
		--network-alias=comment_db \.
		-v reddit_db:/data/db \
		mongo:latest
	docker run -d --network=${REDDIT_NETWORK_NAME} \
		--network-alias=post ${DOCKERHUB_LOGIN}/post:${POST_VERSION}
	docker run -d --network=${REDDIT_NETWORK_NAME} \
		--network-alias=comment ${DOCKERHUB_LOGIN}/comment:${COMMENT_VERSION}
	docker run -d --network=${REDDIT_NETWORK_NAME} \
		-p 9292:9292 ${DOCKERHUB_LOGIN}/ui:${UI_VERSION}
  ```
- Functionality verified

### src/Makefile

#### Variables

| variable | default value | description |


| DOCKERHUB_LOGIN | vscoder | login at hub.docker.com |.
| POST_VERSION | 1.0 | post-py service version |.
| COMMENT_VERSION | 1.0 | version of comment service |.
| UI_VERSION | 1.0 | version of the ui service |.
| REDDIT_NETWORK_NAME | reddit | docker network name |
| REDDIT_DB_VOLUME_NAME | reddit_db | Name of volume for storage mongodb |

#### Targets

| purpose | description |
| ------------- | ------------------------------------------------------------------------------------------------ |
| build_post | collects the container post:${POST_VERSION} from the ./post-py context |.
| dive_post | image analysis post:${POST_VERSION} for efficiency by means of `dive` |.
| build_comment | collects the comment:${COMMENT_VERSION} container from the ./comment context |.
| dive_comment | image analysis comment:${COMMENT_VERSION} on efficiency by `dive` |.
| build_ui | collects the ui:${UI_VERSION} container from the ./ui context |.
| dive_ui | image analysis ui:${UI_VERSION} for efficiency by means of `dive` |.
| build_all | collect all containers |
| run_all | run containers from mongodb images and 3 of our services |.
| kill_all | Kill ** all running** containers and delete the network (volume `${REDDIT_DB_VOLUME_NAME}` is not deleted) |.


## HomeWork 14: Docker: networks, docker-compose

### Networking in Docker

#### Preparations

- We create a new docker-machine and connect to it.
  ``shell
  make docker_machine_create
  docker-machine ls
  ```
  ``log
  NAME ACTIVE DRIVER STATE URL SWARM DOCKER
  docker-host - google Running tcp://35.241.253.37:2376 v19.03.5
  ```
  ``shell
  eval $(docker-machine env docker-host)
  ```

#### Working with the network in Docker

###### none

- Start the container with a network mode `none `
  ``shell
  docker run -ti --rm --network none joffotron/docker-net-tools -c "ifconfig; ping -c4 localhost"
  lo Link encap:Local Loopback  
            inet addr:127.0.0.1 Mask:255.0.0.0
            UP LOOPBACK RUNNING MTU:65536 Metric:1
            RX packets:0:0 dropped:0 overruns:0 frame:0
            TX packets:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

  PING localhost (127.0.0.1): 56 data bytes
  64 bytes from 127.0.0.1: seq=0 ttl=64 time=0.040 ms
  64 bytes from 127.0.0.1: seq=1 ttl=64 time=0.062 ms
  64 bytes from 127.0.0.1: seq=2 ttl=64 time=0.064 ms
  64 bytes from 127.0.0.1: seq=3 ttl=64 time=0.064 ms

  - localhost ping statistics ---
  4 packets transmitted, 4 packets received, 0% packet loss
  round-trip min/avg/max = 0.040/0.057/0.064 ms
  ```
  - We only see the `lo` interface. The network stack inside the container works.
  - Can be used for testing or for fanimulation with files in volume.

#### host

- Launching a container in the network hostname space
  ``shell
  docker run -ti --rm --network host joffotron/docker-net-tools -c ifconfig

  docker0 Link encap:Ethernet HWaddr 02:42:34:B5:56:3D  
            inet addr:172.17.0.1 Bcast:172.17.255.255 Mask:255.255.0.0
            UP BROADCAST MULTICAST MTU:1500 Metric:1
            RX packets:0:0 dropped:0 overruns:0 frame:0
            TX packets:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0 
            RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

  ens4 Link encap:Ethernet HWaddr 42:01:0A:84:00:14  
            inet addr:10.132.0.20 Bcast:10.132.0.20 Mask:255.255.255.255
            inet6 addr: fe80::4001:aff:fe84:14%32617/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST MTU:1460 Metric:1
            RX packets:5504:0 dropped:0 overruns:0 frame:0
            TX packets:4356:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:108677168 (103.6 MiB) TX bytes:447776 (437.2 KiB)

  lo Link encap:Local Loopback  
            inet addr:127.0.0.1 Mask:255.0.0.0
            inet6 addr: ::1%32617/128 Scope:Host
            UP LOOPBACK RUNNING MTU:65536 Metric:1
            RX packets:0:0 dropped:0 overruns:0 frame:0
            TX packets:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
   ```
- By comparison, `ifconfig` on host docker-machine
  ``shell
  docker0 Link encap:Ethernet HWaddr 02:42:34:b5:56:3d  
            inet addr:172.17.0.1 Bcast:172.17.255.255 Mask:255.255.0.0
            UP BROADCAST MULTICAST MTU:1500 Metric:1
            RX packets:0:0 dropped:0 overruns:0 frame:0
            TX packets:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0 
            RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
  ens4 Link encap:Ethernet HWaddr 42:01:0a:84:00:14  
            inet addr:10.132.0.20 Bcast:10.132.0.20 Mask:255.255.255.255
            inet6 addr: fe80::4001:aff:fe84:14/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST MTU:1460 Metric:1
            RX packets:5779:0 dropped:0 overruns:0 frame:0
            TX packets:4570:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:108738036 (108.7 MB) TX bytes:480943 (480.9 KB)
  lo Link encap:Local Loopback  
            inet addr:127.0.0.1 Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING MTU:65536 Metric:1
            RX packets:0:0 dropped:0 overruns:0 frame:0
            TX packets:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
  ```
- We see that they're identical.
- docker machine host re-created due to problems with ssh override
- nginx is running
  ``shell
  docker run --network host -d nginx
  ...
  docker ps
  
  CONTAINER ID IMAGE COMMAND CREATED STATUS PORTS NAMES
  faa0e86c423f nginx "nginx -g 'daemon of..."   6 seconds ago Up 3 seconds distracted_bell
  ```
- another nginx (and another, and another) is running, the result is always the same.
  ``shell
  docker ps

  CONTAINER ID IMAGE COMMAND CREATED STATUS PORTS NAMES
  faa0e86c423f nginx "nginx -g 'daemon of..."   5 minutes ago Up 5 minutes distracted_bell
  ```
- log analysis run attempt
  ``shell
  docker run --network host -d nginx; docker logs $(docker ps -q | head -n1)
  ```
  ``log
  0d82882d485d9678ad273ea048d2b4631652f3feb1bfb5443efb6ffee6bd8fa0
  2019/11/17 13:01:30 [emerg] 1#1: bind() to 0.0.0.0:80 failed (98: Address already in use)
  nginx: [emerg] bind() to 0.0.0.0:80 failed (98: Address already in use)
  2019/11/17 13:01:30 [emerg] 1#1: bind() to 0.0.0.0:80 failed (98: Address already in use)
  nginx: [emerg] bind() to 0.0.0.0:80 failed (98: Address already in use)
  ```
  The log shows that the cause of the fall is already occupied port 80 in the host's neurospace.
- all running containers have been stopped.
  ``shell
  docker kill $(docker ps -q)
  ```

##### network namespaces

- on docker-host there is a symlink that allows you to see the nymspaces with the `sudo ip netns` team.
  ``shell
  sudo ln -s /var/run/docker/netns /var/run/netns
  ```
- nymspaces list without running containers
  ``shell
  $ sudo ip netns
  default
  ```
- the list of neuromapses when the container with the network `none` is running.
  ``shell
  docker run --network none -d nginx
  docker ps
  CONTAINER ID IMAGE COMMAND CREATED STATUS PORTS NAMES
  d227262ccf99 nginx "nginx -g 'daemon of..."   6 seconds ago Up 5 seconds zen_mclean
  ```
  docker-machine
  ``shell
  $ sudo ip netns
  743e31b95726
  default
  ```
  we see there's a new namespace. Running another container.
  ``shell
  docker run --network none -d nginx

  160ca7fec220c182d05a522a1a74143b0114af78220d9ef0370f2bf7be7290c6
  ```
  ``shell
  docker ps                         

  CONTAINER ID IMAGE COMMAND CREATED STATUS PORTS NAMES
  160ca7fec220 nginx "nginx -g 'daemon of..."   2 seconds ago Up 1 second crazy_bardeen
  d227262ccf99 nginx "nginx -g 'daemon of..."   About a minute ago Up About a minute zen_mclean
  ```
  docker-machine
  ``shell
  $ sudo ip netns
  73f504acb923
  743e31b95726
  default
  ```
  see 2 neimspaces
- killed all the containers `docker kill $(docker ps -q)`.
- we use the network `host`
  ``shell
  docker run --network host -d nginx

  7eda8485e28a626e507d310aecaf6e45bc5aa053266ef8338b196f90df93955c
  ```
  docker-machine
  ``shell
  $ sudo ip netns

  default
  ```
  no neimscapes were created. Conclusion - the host's neimscape is used)).
- killed all the containers `docker kill $(docker ps -q)`.

#### bridge

###### Starting an application

- the containers are launched using the bridge network `reddit` and the network aliases assigned to the containers
  ``shell
  # make run_all  
  docker network inspect reddit 1>/dev/null || docker network create reddit
  docker volume inspect reddit_db 1>/dev/null || docker volume create reddit_db
  docker run -d --network=reddit \.
          --network-alias=post_db \.
          --network-alias=comment_db \.
          -v reddit_db:/data/db \
          mongo:latest
  0ba10d8e3d43ce40c15a7b622ad09142f8ea2c9dcbe7e828287db98cc2fd5479
  docker run -d --network=reddit \.
          --network-alias=post vscoder/post:2.0-alpine
  7df2e80b66e19d0335685a78bb07348c3c02124cef97732124cb745615f1d05a
  docker run -d --network=reddit \.
          --network-alias=comment vscoder/comment:2.0-alpine
  37744b362a5838ddda44462e1b9bc580748eaf809c8885ba044f482815c693d2
  docker run -d --network=reddit \.
          -p 9292:9292 vscoder/ui:3.0-alpine
  5281ed3316e3050d16e4c2a7d2a54145ad5d72cc127261f3c2b1169f5f52c728
  ```
  ``shell
  # docker ps
  CONTAINER ID IMAGE COMMAND CREATED STATUS PORTS NAMES
  5281ed3316e3 vscoder/ui:3.0-alpine "puma" 7 minutes ago Up 7 minutes 0.0.0.0:9292->9292/tcp elated_gagarin
  37744b362a58 vscoder/comment:2.0-alpine "puma" 7 minutes ago Up 7 minutes heuristic_murdock
  7df2e80b66e1 vscoder/post:2.0-alpine "python3 post_app.py" 7 minutes ago Up 7 minutes jolly_kirch
  5b04e0482132 mongo:latest "docker-entrypoint.s..."   8 minutes ago Up 8 minutes 27017/tcp modest_proskuriakova
  ```
  the application is available at http://35.241.253.37:9292.
- 2 networks reddit_back and reddit_front are used. 
  - The ui container is connected to the reddit_front network. 
  - The other containers are connected to the reddit_back network. 
  - Since you can specify only one network when creating the container, post and comment are connected to reddit_front after creation.
- Now the Makefile target looks as follows
  ``Makefile
  run_all:
  	docker network inspect ${REDDIT_NETWORK_NAME}_back 1>/dev/null || docker network create ${REDDIT_NETWORK_NAME}_back
  	docker network inspect ${REDDIT_NETWORK_NAME}_front 1>/dev/null || docker network create ${REDDIT_NETWORK_NAME}_front
  	docker volume inspect ${REDDIT_DB_VOLUME_NAME} 1>/dev/null || docker volume create ${REDDIT_DB_VOLUME_NAME}
  	docker run -d \
      --name mongo_db \
  		--network=${REDDIT_NETWORK_NAME}_back \.
  		--network-alias=post_db \.
  		--network-alias=comment_db \.
  		-v reddit_db:/data/db \
  		mongo:latest
  	docker run -d \
      --name post \
  		--network=${REDDIT_NETWORK_NAME}_back \.
  		--network-alias=post \.
  		${DOCKERHUB_LOGIN}/post:${POST_VERSION}
  	docker network connect ${REDDIT_NETWORK_NAME}_front post
  	docker run -d \
      --name comment \
  		--network=${REDDIT_NETWORK_NAME}_back \.
  		--network-alias=comment \.
  		${DOCKERHUB_LOGIN}/comment:${COMMENT_VERSION}
  	docker network connect ${REDDIT_NETWORK_NAME}_front comment
  	docker run -d \
      --name ui \
  		--network=${REDDIT_NETWORK_NAME}_front \.
  		-p 9292:9292 \
  		${DOCKERHUB_LOGIN}/ui:${UI_VERSION}
  ```
- All containers have been launched
  ``shell
  # make run_all
  docker network inspect reddit_back 1>/dev/null || docker network create reddit_back
  docker network inspect reddit_front 1>/dev/null || docker network create reddit_front
  docker volume inspect reddit_db 1>/dev/null || docker volume create reddit_db
  docker run -d \
          --name mongo_db \
          --network=reddit_back \.
          --network-alias=post_db \.
          --network-alias=comment_db \.
          -v reddit_db:/data/db \
          mongo:latest
  596f3227b31e1f90c0ab8fae012659378d7cb99e047be6d9595ab898a2b7e8c
  docker run -d \
          --name post \
          --network=reddit_back \.
          --network-alias=post \.
          vscoder/post:2.0-alpine
  f272a11ca047c347e53e253ce4aafef301aa289e62ad5def39847c27c910578d
  docker network connect reddit_front post
  docker run -d \
          --name comment \
          --network=reddit_back \.
          --network-alias=comment \.
          vscoder/comment:2.0-alpine
  b2ebe7a9d3d8c2e6dbf6169410e8ad61740a6c7564310591ec0a0a023940d8cd
  docker network connect reddit_front comment
  docker run -d \
          --name ui \
          --network=reddit_front \.
          -p 9292:9292 \
          vscoder/ui:3.0-alpine
  82db30416d495c1b590a0cefca7d9e8612cbc4b0564dd0c3937ba757ccc48811
  ```
- Application performance verified

##### Analysis

- List of docker networks on docker-machine
  ``shell
  $ sudo docker network ls
  NETWORK ID NAME DRIVER SCOPE
  0166874dac87 bridge bridge local
  d183b24032cc host local
  2c181ec206b6 none null local
  7e75ed405d47 reddit_back bridge local
  7c243bd0da8a reddit_front bridge local
  ```
- List of br-* interfaces on docker-machine
  ``shell
  $ ifconfig | grep br
  br-7c243bd0da8a Link encap:Ethernet HWaddr 02:42:42:7a:38:6c:0a  
  br-7e75ed405d47 Link encap:Ethernet HWaddr 02:42:b4:2d:1a:09
  ```
  The names of the bridge interfaces match the id networks.
- bridge composition
  ``shell
  $ brctl show br-7c243bd0da8a
  bridge name bridge id STP enabled interfaces
  br-7c243bd0da8a 8000.02427a386c0a no veth234d18b
                                                          vethf4cf7bf
                                                          vethfde16ca
  ```
  ``shell
  $ brctl show br-7e75ed405d47
  bridge name bridge id STP enabled interfaces
  br-7e75ed405d47 8000.0242b42d1a09 no veth257dc23
                                                          veth5af2b40
                                                          veth83d031a
  ```
  veth-interfaces correspond to the container interfaces in the corresponding bridge
- iptables
  ``shell
  $ sudo iptables -vnL -t nat
  Chain PREROUTING (policy ACCEPT 2523 packets, 151K bytes)
   pkts bytes target prot opt in out source destination         
    153 13027 DOCKER all -- * * 0.0.0.0/0 0.0.0/0 ADDRTYPE match dst-type LOCAL

  Chain INPUT (policy ACCEPT 9 packets, 440 bytes)
   pkts bytes target prot opt in out source destination         

  Chain OUTPUT (policy ACCEPT 82 packets, 5229 bytes)
   pkts bytes target prot opt in out source destination         
      0 0 DOCKER all -- * * 0.0.0.0/0 !127.0.0.0/8 ADDRTYPE match dst-type LOCAL

  Chain POSTROUTING (policy ACCEPT 2598 packets, 156K bytes)
   pkts bytes target prot opt in out source destination         
      0 0 MASQUERADE all -- * !br-7c243bd0da8a 172.20.0.0/16 0.0.0.0/0           
      0 0 MASQUERADE all -- * !br-7e75ed405d47 172.19.0.0/16 0.0.0.0/0           
    254 15387 MASQUERADE all -- * !docker0 172.17.0.0/16 0.0.0.0/0           
      0 0 MASQUERADE tcp -- * * 172.20.0.4 172.20.0.4 tcp dpt:9292

  Chain DOCKER (2 references)
   pkts bytes target prot opt in out source destination         
      0 0 RETURN all -- br-7c243bd0da8a * 0.0.0.0/0 0.0.0/0           
      0 0 RETURN all -- br-7e75ed405d47 * 0.0.0.0/0 0.0.0/0           
      0 0 RETURN all -- docker0 * 0.0.0.0/0 0.0.0/0           
      2 120 DNAT tcp -- !br-7c243bd0da8a * 0.0.0.0/0 0.0.0/0 tcp dpt:9292 to:172.20.0.4:9292
  ```
  - You can see here that before determining the route, all the traffic from the `dst-type LOCAL` goes into the `DOCKER` chain in which
    - goes back to ``PREROUTING`` if you come from one of the docker breeds.
    - if it didn't come from `reddit_front` and tcp port 9292, redirect to `172.20.0.4:9292` (ui) is executed.
  - in the chain `POSTROUTING` the traffic coming from docker-networks is masked before exit from other interfaces
    - also masks the traffic between any interfaces with ip 172.20.0.4 to the same ip 172.20.0.4 destination port tcp 9292
      TODO: figure out what it's for.
- docker-proxy
  ``shell
  $ ps ax | grep docker-proxy
  16085 ?        Sl 0:00 /usr/bin/docker-proxy -proto tcp -host-ip 0.0.0.0 -host-port 9292 -container-ip 172.20.0.4 -container-port 9292
  ```
  1 process `cocker-proxy` is running.
- netstat and lsof
  ``shell
  $ sudo lsof -nPi | grep 9292
  docker-pr 16085 root 4u IPv6 102960 0t0 TCP *:9292 (LISTEN)
  ```
  see docker-proxy listening to TCPv6 port 9292.
  ``shell
  $ sudo netstat -apn | grep 9292 
  tcp6 0 0 :::9292 :::* LISTEN 16085/docker-proxy
  ```
  same goes for
  TODO: why ipv6?

### Using docker-compose

#### Installation

- In [requirements.txt](requirements.txt) `docker-compose>=1.24.1` was already added earlier.

### docker-compose.yml

- Created by [src/docker-compose.yml](src/docker-compose.yml)
- In [env](env), add a variable for exports
  ``shell
  export USERNAME=vscoder
  ```
- Assembly of images and start of containers `docker-compose up -d `
  ``log
  ...
  Creating src_post_1 ... done .
  Creating src_ui_1 ... done
  Creating src_comment_1 ... done .
  Creating src_post_db_1 ... done
  ```
- `docker ps`
  ``log
  CONTAINER ID IMAGE COMMAND CREATED STATUS PORTS NAMES
  232065aa859d vscoder/comment:1.0 "puma" 2 minutes ago Up About a minute src_comment_1
  4d18a821d1a6 mongo:3.2 "docker-entrypoint.s..."   2 minutes ago Up About a minute 27017/tcp src_post_db_1
  f7631f5ae799 vscoder/ui:1.0 "puma" 2 minutes ago Up About a minute 0.0.0.0:9292->9292/tcp src_ui_1
  afd5a3874d23 vscoder/post:1.0 "python3 post_app.py" 2 minutes ago Up About a minute src_post_1
  ```
- The browser is open at http://35.240.72.210:9292/.
- everything works, posts are created.

- Description: Removed the superfluous directive `RUN` from `src/*/Dockerfile`, which creates a working directory before the job `WORKDIR`, because it does `WORKDIR` automatically.
  > If the WORKDIR doesn't exist, it will be created even if it's not used in any subsequent Dockerfile instruction.

- The [src/docker-compose.yml](src/docker-compose.yml) file has been changed to use multiple networks.
  ``Yaml
  version: "3.3"
  3.3:
    post_db:
      image: mongo:${MONGO_VERSION-3.2}
      The image:
        - post_db:/data/db
      Networks:
        - reddit_back
    ui:
      build: ./ui
      image: ${USERNAME}/ui:${UI_VERSION-1.0}
      ports:
        - 9292:9292/tcp
      Networks:
        - reddit_front
    Post:
      build: ./post-py
      image: ${USERNAME}/post:${POST_VERSION-1.0}
      networks:
        - reddit_front
        - reddit_back
    comment:
      build: ./comment
      image: ${USERNAME}/comment:${COMMENT_VERSION-1.0}
      networks:
        - reddit_front
        - reddit_back

  Oh..:
    post_db:

  networks:
    reddit_front:
    reddit_back:
  ```

##### Environment Variables

Priority of sources for the value of variables in the container:

When you set the same environment variable in multiple files, here's the priority used by Compose to choose which value to use:

1. Compose file
2. Shell environment variables
3. Environment file
4. Dockerfile
5. Variable is not defined

- Read more about 
  - environment variables https://docs.docker.com/compose/environment-variables/
  - environment variable substitution https://docs.docker.com/compose/compose-file/#variable-substitution
    > Important: The .env file feature only works when you use the docker-compose up command and does not work with docker stack deploy.
  - `docker-compose config` to view the splashed compose file https://docs.docker.com/compose/reference/config/.
  - Compose CLI environment https://docs.docker.com/compose/reference/envvars/
- The file [src/.env](src/.env) with the default values of the variables is created
- The following parameters have been parameterized
  - `MONGO_VERSION=3.2` - mongodb version
  - `UI_VERSION=1.0` - version ui
  - `POST_VERSION=1.0` - post-py version
  - `COMMENT_VERSION=1.0` - comment version
  - `UI_PORT=9292` - publication port ui
  - `USERNAME=vscoder` is the username for the substitution in the image name.
    For example `image: ${USERNAME}/ui:${UI_VERSION}`.
- Checking `docker-compose config`
  ``Yaml
  Networks:
    reddit_back: {}
    reddit_front: {}
  Services:
    comment:
      build:
        context: /mnt/calculate/home/vscoder/projects/otus/devops201908/vscoder_microservices/src/comment
      image: vscoder/comment:1.0
      networks:
        reddit_back: null
        reddit_front: null
    Post:
      build:
        context: /mnt/calculate/home/vscoder/projects/otus/devops201908/vscoder_microservices/src/post-py
      image: vscoder/post:1.0
      networks:
        reddit_back: null
        reddit_front: null
    post_db:
      image: mongo:3.2
      networks:
        reddit_back: null
      Oh..:
      - post_db:/data/db:rw
    ui:
      build:
        context: /mnt/calculate/home/vscoder/projects/otus/devops201908/vscoder_microservices/src/ui
      image: vscoder/ui:1.0
      networks:
        reddit_front: null
      ports:
      - protocol: tcp
        published: 9292
        target: 9292
  version: '3.7'
  Okay:
    post_db: {}
  ```
- The application is launched with publishing the application on port 80 (access to port 80 is allowed in the firewall). `export UI_PORT=80 && docker-compose up -d`.
- The check showed the application is available on port 80.

##### Project name

- https://docs.docker.com/compose/#multiple-isolated-environments-on-a-single-host
- Default project name is taken from `basename` of the project directory.
- You can override the project name 
  - using the [-p command line option](https://docs.docker.com/compose/reference/overview/)
  - using [COMPOSE_PROJECT_NAME environment variable](https://docs.docker.com/compose/reference/envvars/#compose_project_name)

### Task from \*: docker-compose.override.yml

#### Analysis

[Share Compose configurations between files and projects](https://docs.docker.com/compose/extends/)

By default, Compose reads two files, a docker-compose.yml and an optional docker-compose.override.yml file.
If a service is defined in both files, Compose merges the configurations.
To use multiple override files, or an override file with a different name, you can use the -f option to specify the list of files. Compose merges files in the order they're specified on the command line.

#### Implementation

- Added file [src/docker-compose.override.yml](src/docker-compose.override.yml)
- The [src/docker-compose.override.yml](src/docker-compose.override.yml) overrides the following parameters:
  - The local directory of `./post-py` is mounted in the `/app` container.
  - In `/app` container `comment` the local directory `./comment` is mounted.
  - Service `puma` in `ui` starts with parameters `--debug -w 2`.
- In [src/docker-compose.override.yml](src/docker-compose.override.yml) added version of
  ``Yaml
  version: "3.3"
  ```
- In [src/docker-compose.override.yml] (src/docker-compose.override.yml) the description of services is placed in section `services:`.
- For each service, in [src/docker-compose.override.yml](src/docker-compose.override.yml) the directory with the code is mounted to the directory specified in the corresponding environment variable
- Summary contents [src/docker-compose.override.yml](src/docker-compose.override.yml)
  ``Yaml
  ---
  version: "3.3"

  3.3:
    post:
      The following pages:
        - "./post-py:${POST_APP_HOME}".
    comment:
      Ah:
        - "./comment:${COMMENT_APP_HOME}".
    ui:
      I'm sorry:
        - "./ui:${UI_APP_HOME}"
      command: puma --debug -w 2
  ```
- **VERY** doesn't work out of the box with the docker-machine mount, you need to magic with [docker-machine mount](https://docs.docker.com/machine/reference/mount/).
- The dock file format version has been changed from `3.7` to `3.3` due to the fact that travis-ci does not support a higher version of the

### Off Tasks

- In order to improve readability, the commands from [.travis.yml] have been moved from [.travis.yml] to shell scripts.
  - `install` in [.travis-scripts/install.sh](.travis-scripts/install.sh)
  - `before_script` in [.travis-scripts/before_script.sh](.travis-scripts/before_script.sh)


## HomeWork 15: Gitlab CI device. Building a continuous supply process

### Deploying gitlab

#### Host preparation

- The [gitlab](gitlab) directory was created.
- Created by [Makefile] (gitlab-ci/Makefile) with a set of targets for deploying infrastructure under gitlab using packer, teraform and ansible

#### ansible

- The directory [gitlab-ci/ansible] (gitlab-ci/ansible) is based on [docker-monolith/ansible].
- Deleted unnecessary files and directories.
- Only the playbook [gitlab-ci/ansible/playbooks/docker.yml](gitlab-ci/ansible/playbooks/docker.yml) needed to deploy the docker in the packer image is left.
- External ansible-rolls are installed

#### packer

- The directory [gitlab-ci/packer](gitlab-ci/packer) was created on the basis of [docker-monolith packer](docker-monolith/packer).
- Added the file with examples of [gitlab-ci/packer/variables.json.example](gitlab-ci/packer/variables.json.example).
  `json
  {
    "project_id": "docker-ID",
    "source_image_family": "ubuntu-1604-lts",
    "machine_type": "n1-standart-1."
    "disk_size": "60"
  }
  ```
- Filled in variables [gitlab-ci/packer/variables.json](gitlab-ci/packer/variables.json)
- Packer configuration checked
  ``shell
  # make packer_validate
  ~/bin/packer --version
  1.4.4
  ~/bin/packer validate -var-file=packer/variables.json packer/docker.json
  Template validated successfully.
  ```
- Collected image ``"image_family": "gitlab-docker-base" `.
  ``shell
  # make packer_build
  ...
  ==> Builds finished. The artifacts of successful builds are:
  --> googlecompute: A disk image was created: gitlab-docker-base-1574589582.
  ```

#### terraform

- The directory [docker-monolith/terraform] (docker-monolith/terraform) is copied to [gitlab-ci/terraform] (gitlab-ci/terraform).
- In [gitlab-ci/terraform/stage/backend.tf] (gitlab-ci/terraform/stage/backend.tf) the value of `prefix` is set to ``"terraform/gitlab/stage``.
- In [gitlab-ci/terraform/stage/terraform.tfvars.example] (gitlab-ci/terraform/stage/terraform.tfvars.example) the values of the following variables were changed
  ``hcl
  docker_app_disk_image = "gitlab-docker-base"
  docker_app_tags = ["gitlab-docker-app"]
  docker_app_tcp_ports = ["80", "443"]
  ```
- Also added are the variables
  ``hcl
  docker_app_name_prefix = "gitlab"
  docker_app_machine_type = "n1-standard-1"
  ```
- The same variables were added/modified in [gitlab-ci/terraform/terraform.tfvars](gitlab-ci/terraform/terraform.tfvars).
- Terraform initialization carried out
  ``shell
  # make terraform_init
  ...
  Terraform has been successfully initialized!
  ...
  ```
- Validation `make terraform_validate` has been performed.
- Linting `make terraform_tflint` has been performed.
- The infrastructure `make terraform_apply` is created.
  `json
  Apply complete! Resources: 2 added, 0 changed, 0.

  Outputs:

  docker_app_external_ip = [
    "34.76.206.37",
  ]
  ```

#### Deploying gitlab

All actions are performed on the remote machine deployed in the previous paragraph

- The necessary directories have been created
  ``shell
  sudo mkdir -p /srv/gitlab/config /srv/gitlab/data /srv/gitlab/logs
  cd /srv/gitlab/
  sudo touch docker-compose.yml
  ```
- Contents `docker-compose.yml`
``Yaml
web:
  image: 'gitlab/gitlab-ce:latest'.
  restart: always
  hostname: 'gitlab.example.com'.
  Environment:
    GITLAB_OMNIBUS_CONFIG: |
      external_url 'http://34.76.206.37'
      gitlab_rails['gitlab_shell_ssh_port'] = 2222.
  ports:
    - '80:80'
    - '443:443'
    - '2222:22'
  Oh..:
    - '/srv/gitlab/config:/etc/gitlab'.
    - '/srv/gitlab/logs:/var/log/gitlab'.
    - '/srv/gitlab/data:/var/opt/gitlab'.
```
- Deployment launched `sudo docker-compose up -d `
- After a few minutes, the installation is complete
- Password set for user `root` (default user)
- Successfully entered.

#### Initial setting

- Cancelled the ability to register new users
  *settings -> general -> sign-up restrictions ->sign-up enabled = false*, *save changes*
- Changed *Administrator* user login to make it harder to brute force password selection

##### Working with the repository via ssh

- Added public ssh key to user
- In [gitlab-ci/terraform/stage/terraform.tfvars] (gitlab-ci/terraform/stage/terraform.tfvars) port `2222` is allowed.
  ``hcl
  docker_app_tcp_ports = ["80", "443", "2222"]
  ```
- In `docker-comnpose.yml` added parameter `gitlab_rails['gitlab_shell_ssh_port'] = 2222` to work with git repository via ssh on port `2222`.

### project creation

- The private group `Homework` is created.
- The private project `example` is created.
- In a repository `vscoder_microservices` the remote repository of the created project is added
``shell
git remote add gitlab ssh://git@34.76.206.37:2222/otus/example.git
git push gitlab gitlab-ci-1
```

#### CI/CD Pipeline

- Added [.gitlab-ci.yml](.gitlab-ci.yml) containing the Pipeline template
``Yaml
(Sighs)
  - build
  - test
  -

build_job:
  stage: build
  script:
    - echo 'Building'

test_unit_job:
  stage: test
  script:
    - echo 'Testing 1'

test_integration_job:
  stage: test_integration_job: test
  script:
    - echo 'Testing 2'

deploy_job:
  stage: deploy
  script:
    - echo 'Deploy'
```

### Runner

- The gitlab host is running a ranner
``shell
docker run -d --name gitlab-runner --restart always \.
  -v /srv/gitlab-runner/config:/etc/gitlab-runner \.
  -v /var/run/docker.sock:/var/run/docker.sock \.
  gitlab/gitlab-runner:latest
```
- Ranner is registered at gitlab
``shell
docker exec -it gitlab-runner gitlab-runner register --run-untagged --locked=false
```
``shell
> Runtime platform arch=amd64 os=linux pid=13 revision=577f813d version=12.5.0
> Running in system-mode.                            
>                                                    
> Please enter the gitlab-ci coordinator URL (e.g. https://gitlab.com/):
http://34.76.206.37/
> Please enter the gitlab-ci token for this runner:
here_is_token
> Please enter the gitlab-ci description for this runner:
[b1ae79ee8481]: gce-docker-runnel
> Please enter the gitlab-ci tags for this runner (comma separated):
linux,xenial,ubuntu,docker
> Registering runner... register runner=QW4GxkHHH
> Please enter the executor: parallels, shell, virtualbox, docker+machine, docker-ssh+machine, custom, docker, docker-ssh, ssh, kubernetes:
docker
> Please enter the default Docker image (e.g. ruby:2.6):
alpine:latest
> Runner registered successfully. Feel free to start it, but if it's running already the config should be automatically reloaded!
```
- Pipeline was automatically started and executed successfully.

### Testing Reddit

- The application code is cloned from the repository
``shell
git clone https://github.com/express42/reddit.git && rm -rf ./reddit/.git
git add reddit/
git commit -m "Add reddit app"
git push gitlab gitlab-ci-1
```
- In [.gitlab-ci.yml](.gitlab-ci.yml) added Pipeline elements to test the application. New Content
``Yaml
---
image: ruby:2.4.2

stages:
  - build
  - test
  -

It's not:
  DATABASE_URL: "mongodb://mongo/user_posts"

before_script:
  - cd reddit
  - bundle install

build_job:
  stage: build
  script:
    - echo 'Building'

test_unit_job:
  stage: test
  Services:
    - mongo:latest
  script:
    - ruby simpletest.rb
    # - echo 'Testing 1'

test_integration_job:
  stage: test_integration_job: test
  script:
    - echo 'Testing 2'

deploy_job:
  stage: deploy
  script:
    - echo 'Deploy'
```
- In [reddit/simpletest.rb](reddit/simpletest.rb) added a simple test
``Ruby
require_relative './app'
require 'test/unit'
require 'rack/test'

set :environment, :test

class MyAppTest < Test::Unit::TestCase
  include Rack::Test::Methods

  def app
    Sinatra::Application
  end

  def test_get_request
    get '/'
    assert last_response.okay?
  end
end
```
- In [reddit/Gemfile](reddit/Gemfile) added library for testing
``Ruby
gem 'rack-test'
```
- Changes are uploaded and running in gitlab
``shell
git add .
git ci -m "Add reddit app tests to pipeline."
git push gitlab gitlab-ci-1
```
- Job succeeded

### Working with environments

#### dev

- In [.gitlab-ci.yml](.gitlab-ci.yml) stage `deploy' is renamed `review'.
``Yaml
Oh:
  - build
  - test
  - review
```
- Job `deploy_job' has been renamed `deploy_dev_job' and is listed as follows
``Yaml
deploy_dev_job:
  stage: review
  script:
    - echo 'Deploy'
  Environment:
    name: dev
    url: http://dev.example.com
```
- Done and push
``shell
git add .
git ci -m "Add deploy dev environment."
git push gitlab gitlab-ci-1
```
- The project in *operations* -> *environments* has an environment **dev**.
- Clicking on *View deployment* will switch to the specified url

#### staging and production

- In [.gitlab-ci.yml](.gitlab-ci.yml) added jobs `staging` and `production`.
``Yaml
Staging:
  stage: stage
  when: manual # manual start
  script:
    - echo 'Deploy'
  Environment:
    name: stage
    url: https://beta.example.com

production:
  stage: production
  when: manual # manual start
  script:
    - echo 'Deploy'
  Environment:
    name: production
    url: https://example.com
```
- The stage and production stages were started manually
- In both stages the condition of possibility to start only with the tag corresponding to three numbers separated by a point is added
``Yaml
Only:
  - /^\d+\.\d+\.\d+/
```
- After a Tag-On-Tag, stage and production stages are not available.
- Push with tag is done.
``shell
git add .
git commit -m "Add tag and push"
git tag 2.4.10
git push gitlab gitlab-ci-1
git push gitlab gitlab-ci-1 --tags
```
- The stage and prod stages are again available for the tagged job.

#### Dynamic environments

- Added job `branch review`
``Yaml
It's a branch review:
  stage: review # stage name
  script: echo "Deploy to $CI_ENVIRONMENT_SLUG"
  Environment:
    name: branch/$CI_COMMIT_REF_NAME # brand name in environment name
    url: http://$CI_ENVIRONMENT_SLUG.example.com # brand name in url
  Only:
    - branches # start for each branch of the repository
  except:
    - master # do not run for master
```
This job defines the dynamic environment for each branch in the repository, except for the master branch.
- It is checked: the branch `new-feature` has been created. Two environments were created.
  - `branch/gitlab-ci-1` for the current brand
  - `branch/new-feature` for the created brand


### Off Tasks: Improvements

- Added [gitlab-ci/README.md](gitlab-ci/README.md) with description of Makefile targets and variables

### Task from \ ##: Automated build of reddit application

Add a container assembly with the reddit application to the build step. Deposit the container from reddit to the server created for the branch.

#### Plan

- [x] Configure [gitlab registry] (https://docs.gitlab.com/ee/user/packages/container_registry/index.html)
  - [x] Enable integration with [Let's Encrypt] (https://docs.gitlab.com/omnibus/settings/ssl.html#lets-encrypt-integration).
    - [x] Create a binding to the domain name
      - [x] Create a permanent ip using terraform tools
      - [x] Subsequently, to solve the problem with the formation of url for `environment.url` in `.gitlab-ci.yml`.
  - [x] registry has been enabled automatically [GitLab Container Registry administration] (https://docs.gitlab.com/ee/administration/packages/container_registry.html).
- [x] Configure in `.gitlab-ci.yml` the automated assembly of images using [docker build] (https://docs.docker.com/engine/reference/commandline/build/).
  - [x] solve the problem of assembling images with an early docker type image https://docs.gitlab.com/сe/ci/docker/using_docker_build.html.
- [x] The next step is to upload the image to the registry as configured earlier
- [x] Prepare the infrastructure:
  - [x] create a server with docker for terraform deposition installed
- [x] create ansible-playbook for depositing the application on the created server by docker-compose means
- [x] implement a deploy in `.gitlab-ci.yml'.

#### Implementation

**WARNING** Perhaps you should use `google_dns_managed_zone` more correctly to control dns records in gitlab and branch environments. **TODO:** figure it out

As part of this RS, Let's Encrypt integration will use the permanent IP and its own domain `vscoder.ru`.

##### Setting up terraform module instance

- The [gitlab-ci/terraform/modules/instance/main.tf](gitlab-ci/terraform/modules/instance/main.tf) has been configured to use static ip
``hcl
resource "google_compute_instance" "instance" {
  ...
  network_interface {
    ...
    access_config {
      nat_ip = var.use_static_ip ? google_compute_address.instance_ip[0].address : null
    }
  }
}
...
resource "google_compute_address" "instance_ip" {
  name = "reddit-app-ip-${var.environment}"
  count = var.use_static_ip ? 1 : 0
}
```
- In [gitlab-ci/terraform/modules/instance/variables.tf](gitlab-ci/terraform/modules/instance/variables.tf) added a description of variable `use_static_ip`.
``hcl
variable use_static_ip {
  description = "Need to create static ip for instance?"
  default = false
}
```

##### Setting up a terraform stage environment

- [gitlab-ci/terraform/stage/main.tf] (gitlab-ci/terraform/stage/main.tf) includes the use of static ip for gitlab instance
``hcl
# GitLab instance
module "docker-app" {
  instance_count = 1 # Number 1 as we have the only instance gitlab
  ...
  use_static_ip = true
}
```

##### infrastructure application

- Application
``shell
cd gitlab && make terraform_apply
```
``log
module.docker-app.google_compute_address.instance_ip[0]: Creating...
module.docker-app.google_compute_address.instance_ip[0]: Creation complete after 4s [id=docker-257914/europe-west1/reddit-app-ip-stage].
module.docker-app.google_compute_instance.instance[0]: Modifying... [id=gitlab-stage-001]
module.docker-app.google_compute_instance.instance[0]: Still modifying... [id=gitlab-stage-001, 10s elapsed]
module.docker-app.google_compute_instance.instance[0]: Modifications complete after 16s [id=gitlab-stage-001].

Apply complete! Resources: 1 added, 1 changed, 0.

Outputs:

docker_app_external_ip = [
  "35.195.25.130",
]
```
- The domain record `gitlab.vscoder.ru A 35.195.25.130` is created.
- After the timeout, GitLab is available at http://gitlab.vscoder.ru.
- Forgot your password. Restore https://docs.gitlab.com/ee/security/reset_root_password.html
``shell
ssh -i ~/.ssh/<private_key> appuser@35.195.25.130.
cd /srv/gitlab
sudo docker-compose exec web bash
gitlab-rails console -e production
```
``Ruby
user = User.where(id: 1).first
user.password = 'secret_pass'
user.password_confirmation = 'secret_pass'
user.save!
```
- Login successfully completed.

#### Integration with Let's Encrypt

- On the host with gitlab, `/srv/gitlab/docker-compose.yml' enabled [integration with Let's Encrypt] (https://docs.gitlab.com/omnibus/settings/ssl.html#primary-gitlab-instance).
``Yaml
...
" web...
  ...
  environment:
    GITLAB_OMNIBUS_CONFIG: |
      gitlab_rails['gitlab_shell_ssh_port'] = 2222
      letsencrypt['enable'] = true
      external_url "https://gitlab.vscoder.ru"
```
- Hitlab has been restarted
`sh
sudo docker-compose down; sudo docker-compose up -d && sudo docker-compose logs -f
# wait ~3-5min for ditlab starts
```
``log
...
Recipe: letsencrypt::enable
   * crond_job[letsencrypt-renew] action create
     * file[/var/opt/gitlab/crond/letsencrypt-renew] action create
       - create new file /var/opt/gitlab/crond/letsencrypt-renew
       - update content in file /var/opt/gitlab/crond/letsencrypt-renew from none to d7e87c
       --- /var/opt/gitlab/crond/letsencrypt-renew 2019-11-27 16:19:49.916624624 +0000.
       +++ /var/opt/gitlab/crond/.chef-letsencrypt-renew20191127-22-k2j9ix 2019-11-27 16:19:49.916624624 +000000
       @@ -1 +1,2 @@
       +18 0 */4 * * root /opt/gitlab/bin/gitlab-ctl renew-le-certs
       - change owner from '' to 'root'.
       - change group from '' to 'root'.
   
   * ruby_block[display_le_message] action nothing (skipped due to action :nothing)
   * ruby_block[save_auto_enabled] action run
     - execute the ruby block save_auto_enabled
...
```
- Successfully signed in to https://gitlab.vscoder.ru/.
- In the Admin Area you can see that the built-in Container Registry has become active.
- Actual `docker-compose.yml`
``Yaml
web:
  image: 'gitlab/gitlab-ce:latest'.
  restart: always
  hostname: 'gitlab.example.com'.
  Environment:
    GITLAB_OMNIBUS_CONFIG: |
      gitlab_rails['gitlab_shell_ssh_port'] = 2222.
      letsencrypt['enable'] = true
      external_url "https://gitlab.vscoder.ru"
  ports:
    - '80:80'
    - '443:443'
    - '2222:22'
  Oh..:
    - '/srv/gitlab/config:/etc/gitlab'.
    - '/srv/gitlab/logs:/var/log/gitlab'.
    - '/srv/gitlab/data:/var/opt/gitlab'.
```

##### Setting up image assembly in .gitlab-ci.yml

##### Trying to solve a problem on the forehead (unsuccessful)

- Deleted the call to the fake tests previously added as an example
- In [.gitlab-ci.yml](.gitlab-ci.yml) in `build_job` task added assembly of all containers
- In the repository `vscoder_microservices` the remote repository of the created project has been changed
``shell
git remote rm gitlab
git remote add gitlab ssh://git@gitlab.vscoder.ru:2222/otus/example.git
git push gitlab gitlab-ci-1
```
- In [gitlab-ci/Makefile] (gitlab-ci/Makefile) we added a `push_gitlab` target for remote named _gitlab_.
- Push to Hitlab.
- An earlier running ran ranner was inactive due to a change in the gitlab URL at https://gitlab.vscoder.ru.
- Connection to container `sudo docker exec -it gitlab-runner bash ` is made.
- In the config of the earlier `/etc/gitlab-runner/gitlab.toml` the url has been changed from `url = "http://34.76.206.37/"` to `url = "https://gitlab.vscoder.ru/"`.
- Container restarted.
``shell
sudo docker restart gitlab-runner
```
- gitlab-rrunner `gce-docker-runnel` has become active again.
- pipeline error
``shell
$ cd src && make build_all
docker build -t vscoder/post:2.0-alpine ./post-py
make: docker: command not found
```
  - Cause - assembly in image `image: ruby:2.4.2`.
- Solution attempt: using [image] (https://hub.docker.com/_/docker) `docker:stable` for `build_job`.
- Error `/bin/sh: eval: line 87: make: not found `
- In [.gitlab-ci.yml](.gitlab-ci.yml) added `make` installation.
``Yaml
script:
  - echo 'Building'
  - sudo apt install make
  - cd src && make build_all
```
- Error
``log
$ sudo apt install make
/bin/sh: eval: line 87: sudo: not found
```
- took out the sudo
``Yaml
script:
  - echo 'Building'
  - apt install make
  - cd src && make build_all
```
- error `/bin/sh: eval: line 87: apt: not found`
- We in alpine linux)) replaced `apt` with `apk`.
``Yaml
script:
  - echo 'Building'
  - apk install make
  - cd src && make build_all
```
- error `ERROR: 'install' is not an apk command. See 'apk --help'.`.
not to look into your old code (e.g. building alpine-based images)))
- has replaced `install` with `add`.
``Yaml
script:
  - echo 'Building'
  - apk add make
  - cd src && make build_all
```
- mistake
``log
docker build -t vscoder/post:2.0-alpine ./post-py
time="2019-11-27T17:53:26Z" level=error msg="failed to dial gRPC: cannot connect to the Docker daemon. Is 'docker daemon' running on this host?: dial tcp: lookup docker on 169.254.169.254:53: no such host".
error at connect: Post http://docker:2375/v1.40/build?buildargs=%7B%7D&cachefrom=%5B%5D&cgroupparent=&cpuperiod=0&cpuquota=0&cpusetcpus=&cpusetmems=&cpushares=0&dockerfile=Dockerfile&labels=%7B%7D&memory=0&memswap=0&networkmode=default&rm=1&session=d831lkik8627vo4jczmd2jqvm&shmsize=0&t=vscoder%2Fpost%3A2.0-alpine&target=&ulimits=null&version=1: context canceled
make: *** [Makefile:11: build_post] Error 1
```
- Solution attempt: specify `DOCKER_HOST: unix:///var/run/docker.sock` since we do not use docker-in-docker service.
- did not work `Cannot connect to the Docker daemon at unix:///var/run/docker. Is the docker daemon running?``

##### Analysis

- End of dancing with a tambourine, time to read the documentation: https://docs.gitlab.com/сe/ci/docker/using_docker_build.html.
- The easiest way -- [use shell executor] (https://docs.gitlab.com/ce/ci/docker/using_docker_build.html#use-shell-executor).
  - separate host is assumed
  - By adding gitlab-runner to the docker group you are effectively granting gitlab-runner full root permissions
- It is also possible to use [docker-in-docker workflow with Docker executor] (https://docs.gitlab.com/ce/ci/docker/using_docker_build.html#use-docker-in-docker-workflow-with-docker-executor).
  - Read https://jpetazzo.github.io/2015/09/03/do-not-use-docker-in-docker-for-ci/ before the enlightenment, why it's better not to.
- The third way -- [Use Docker socket binding] (https://docs.gitlab.com/ce/ci/docker/using_docker_build.html#use-docker-socket-binding)
  - **WARNING** Docker in privileged mode

The minuses of the solution **docker-in-docker**
- Problems when using SElinux or AppArmor
- Problems when using DeviceMapper (DM not namespaced)
- Either refuse to use the image cache, or the possibility of data corruption if the host cache is used
  > But try to do something more involved... and watch the world burn.
- Recommendations from the author of the article
  > And the simplest way is to just expose the Docker socket to your CI container, by bind-mounting it with the -v flag.
  > ...
  > And the simplest way is to just expose the Docker socket to your CI container, by bind-mounting it with the -v flag.

The minuses of the docker sockert binding

> By sharing the docker daemon, you are effectively disabling all the security mechanisms of containers and exposing your host to privilege escalation which can lead to container breakout. For example, if a project ran docker rm -f $(docker ps -a -q) it would remove the GitLab Runner containers.

> Concurrent jobs may not work; if your tests create containers with specific names, they may conflict with each other.

> Sharing files and directories from the source repo into containers may not work as expected since volume mounting is done in the context of the host machine, not the build container. > Sharing files and directories from the source repo to containers may not work as expected since the volume mounting is done in the context of the host machine, not the building container:

A decision was made to raise a ranner on a separate host...

##### Preparing the host for docker runner

- In [gitlab-ci/packer/docker.json](gitlab-ci/packer/docker.json) the parameter `image_family` is parameterized.
- Created file [gitlab-ci/packer/variables-gitlab-runner.json](gitlab-ci/packer/variables-gitlab-runner.json) with values for the image with gitlab-runner.
- **Note** variable `project_id` remains in file `variables.json`.
- In [gitlab-ci/packer/docker.json](gitlab-ci/packer/docker.json) parameter `playbook_file` is parameterized for image rendering. It is necessary to specify the playbook file name relative to the directory `gitlab-ci/ansible/playbooks/docker.yml`. By default `docker.yml`.
- The [gitlab-ci/packer/docker.json](gitlab-ci/packer/docker.json) sets the default values for the variables
`json
{
  ...
  "source_image_family": "ubuntu-1604-lts",
  "image_family": "docker-base",
  ...
}
```
- Variables related to the gitlab server image are placed in a separate file [gitlab-ci/packer/variables-gitlab.json](gitlab-ci/packer/variables-gitlab.json).
- Created playbook [gitlab-ci/ansible/playbooks/packer-gitlab-runner.yml](gitlab-ci/ansible/playbooks/packer-gitlab-runner.yml) that installs docker and hitlab-runner.
``Yaml
---
- name: Provision image with docker and gitlab-runner
  hosts: all
  become: true
  I'm sorry:
    - role: geerlingguy.docker
    - role: riemers.gitlab-runner
```
- Added role dependency on [gitlab-ci/ansible/environments/stage/requirements.yml](gitlab-ci/ansible/environments/stage/requirements.yml). 
- Ansible `make ansible_install_requirements` dependencies are set.
- In Makefile targets `packer_build` and `packer_validate` added use of variable from `packer/variables.json`.
- In Makefile targets `packer_build` and `packer_validate`, in addition to the previous item, added the use of variables from `PACKER_VAR_FILE?=packer/variables-gitlab-runner.json`.
`json
{
  "source_image_family": "ubuntu-1604-lts",
  "image_family": "gitlab-runner-base",
  "machine_type": "n1-standard-1."
  "disk_size": "40",
  "playbook_name": "packer-gitlab-runner.yml"
}
```
- In [gitlab-ci/packer/scripts/ansible-playbook.sh] (gitlab-ci/packer/scripts/ansible-playbook.sh) the path to the executable file `ansible` has been fixed.
- The assembly of the packer-image gitlab-runner `make packer_build PACKER_VAR_FILE=packer/variables-gitlab-runner.json` has been completed.
  - **Error** `Version '12.5.2' for 'gitlab-runner' was not found`.
  - from [gitlab-ci/ansible/playbooks/packer-gitlab-runner.yml](gitlab-ci/ansible/playbooks/packer-gitlab-runner.yml) the version parameter `gitlab_runner_package_version` has been removed.
  - assembly was successful
- In [gitlab-ci/terraform/stage/main.tf](gitlab-ci/terraform/stage/main.tf) another host is created.
``hcl
# Gitlab Runner
module "gitlab-runner" {
  instance_count = 1
  source = ".../modules/instance"
  project = var.project
  zone = var.zone
  environment = var.environment
  name_prefix = "gitlab-runner"
  machine_type = "g1-small"
  instance_disk_image = "gitlab-runner-base"
  tags = ["gitlab-runner"]
  tcp_ports = ["22"]
  vpc_network_name = var.vpc_network_name
  use_static_ip = false
}
```
- In [gitlab-ci/terraform/stage/main.tf](gitlab-ci/terraform/stage/main.tf) some host parameters are set explicitly, not from variables
- The host instance for gitlab-runner `make terraform_apply` is created.
``log
Outputs:

docker_app_external_ip = [
  "35.195.25.130",
]
```
- Checking to see if the ancible saw the host
``shell
make ansible_inventory_list
```
`json
...
    "all." {
        "children." [
            "env_stage."
            "gitlab_docker_app."
            "gitlab_runner."
            "ungrouped"
        ]
    },
    "env_stage." {
        "hosts." [
            "gitlab-runner-stage-001."
            "gitlab-stage-001"
        ]
    },
    "gitlab_docker_app." {
        "hosts." [
            "gitlab-stage-001"
        ]
    },
    "gitlab_runner." {
        "hosts." [
            "gitlab-runner-stage-001"
        ]
    }
...
```

##### prepared docker-runner

- A playbook has been created [gitlab-ci/ansible/playbooks/gitlab-runner.yml](gitlab-ci/ansible/playbooks/gitlab-runner.yml), which starts and registers the earlier ones
``Yaml
---
- name: Provision image with docker and gitlab-runner
  hosts: gitlab_runner
  become: true
  I'm sorry:
    - role: riemers.gitlab-runner
```
- Create a file [gitlab-ci/ansible/environments/stage/group_vars/gitlab_runner] (gitlab-ci/ansible/environments/stage/group_vars/gitlab_runner) that contains the variables needed for the playbook to work. In this case, the token value is taken from the environment variable
``Yaml
gitlab_runner_registration_token: "{{{lookup('env', 'GITLAB_RUNNER_REGISTRATION_TOKEN') }}".
```

- Playback application ends with an error
``log
TASK [riemers.gitlab-runner : Register runner to GitLab] *********************************************************************
[gitlab-runner-stage-001]: FAILED! => {"censored": "the output has been hidden due to the fact that 'no_log: true' was specified for this result", "changed": true}.
```
- Launch in debug mode `ANSIBLE_DEBUG=true ansible-playbook -i environments/stage/inventory.gcp.yml playbooks/gitlab-runner. yml` helped to detect an error: in the [config](gitlab-ci/ansible/environments/stage/group_vars/gitlab_runner) of ranners with `docker` type no default image was specified (parfm `docker_image: `).
- New Error
``log
TASK [riemers.gitlab-runner : Assemble new config.toml] *****************************************************************
[gitlab-runner-stage-001]: FAILED! => {"changed": false, "msg": "failed to validate: rc:1 error:Runtime platform \u001b[0;m arch\u001b[0;m=amd64 os\u001b[0;m=linux pid\u001b[0;m=14766 revision\u001b[0;m=577f813d version\u001b[0;m=12.5.0\nRunning in system-mode.                           \u001b[0;m \n \u001b[0;m \n\u001b[31;1mFATAL: Near line 29 (last key parsed 'runners.docker.sysctls'): bare keys cannot contain '.'\u001b[0;m \n"}.
```
problem in the presence of points in the parameters `runners.docker.sysctls: `
  - the attempt to place the parameters in quotes failed
  - The decision was made to remove these parameters from the config because they were not necessary.
- new fault
``log
TASK [riemers.gitlab-runner : Assemble new config.toml] *****************************************************************
[gitlab-runner-stage-001]: FAILED! => {"changed": false, "msg": "failed to validate: rc:1 error:Runtime platform \u001b[0;m arch\u001b[0;m=amd64 os\u001b[0;m=linux pid\u001b[0;m=24632 revision\u001b[0;m=577f813d version\u001b[0;m=12.5.0\nRunning in system-mode.                           \u001b[0;m \n \u001b[0;m \n\u001b[31;1mFATAL: toml: cannot load TOML value of type map[string]interface {} into a Go string\u001b[0;m \n"}.
```
- the problem was in the early `GitLab Runner shell`.
``Yaml
  - name: "GitLab Runner shell"
    executor: shell
    tags:
      - shell
    run_untagged: false
```
this ranner was removed from the list, and then the playbook was successfully applied.
- two early warning signs were eventually reserved. 
  - `GitLab Runner dind` for docker-image assembly.
  - `GitLab Runner docker` to run everything else.
- **Value** it has been revealed that the GitLab Runner docker is not available. After explicitly specifying the image tag in the config of the ranner and restarting the gitlab-runner.service, the ranner contacted the server again. Corresponding changes were made to the variables of the group gitlab-runner[gitlab-ci/ansible/environments/stage/group_vars/gitlab_runner](gitlab-ci/ansible/environments/stage/group_vars/gitlab_runner).

##### Automated image assembly

- In [.gitlab-ci.yml](.gitlab-ci.yml) the parameter `build_job` has been added with `tags: ["dind"]` so that the build is launched at the right early stage. It's the same:
  - removed punk `image: ruby:2.4.2`.
- Assembly of images ** was successful**!

##### Uploading images to the gitlab registry

https://docs.gitlab.com/ee/user/packages/container_registry/index.html

https://docs.gitlab.com/ee/ci/variables/predefined_variables.html#variables-reference

- Check that the registry is enabled for project _Packages_ > _Container Registry_ [documentation] (https://docs.gitlab.com/ee/user/packages/container_registry/index.html#enable-the-container-registry-for-your-project).
- Login, for this purpose we add `docker login` to `build_job` `before_script`.
``Yaml
...
build_job:
  stage: build
  before_script:
    - docker info
    - docker login -u $CI_REGISTRY_USER -p $CI_REGISTRY_PASSWORD $CI_REGISTRY
...
```
- after reading the documentation at https://docs.gitlab.com/ee/ci/yaml/#before_script-and-after_script, the login in the login was transferred to the `script` section.
``Yaml
...
build_job:
  ...
  script:
    # login
    - docker info
    - docker login -u $CI_REGISTRY_USER -p $CI_REGISTRY_PASSWORD $CI_REGISTRY
    ...
...
```
- The assembly of images has been changed. They are now built manually, without using make. **HERE** in order to avoid swelling of the make-file, the Hitlab images assembly has not been added to it.
```yaml
build_job:
  ...
  script:
    # login
    ...
    # build
    - cd src && docker build -t ${CI_REGISTRY_IMAGE}/post:${CI_COMMIT_REF_NAME} ./post
    - cd src && docker build -t ${CI_REGISTRY_IMAGE}/comment:${CI_COMMIT_REF_NAME} ./comment
    - cd src && docker build -t ${CI_REGISTRY_IMAGE}/ui:${CI_COMMIT_REF_NAME} ./ui
```
- Added image upload to gitlab registry
``Yaml
build_job:
  ...
  script:
    # login
    ...
    # build
    ...
    # push
    - docker push ${CI_REGISTRY_IMAGE}/post:${CI_COMMIT_REF_NAME}
    - docker push ${CI_REGISTRY_IMAGE}/comment:${CI_COMMIT_REF_NAME}
    - docker push ${CI_REGISTRY_IMAGE}/ui:${CI_COMMIT_REF_NAME}
```
- Pipeline attempted run: bug
``log
Error response from daemon: Get https://gitlab.vscoder.ru:5050/v2/: net/http: request cancelled while waiting for connection (Client.Timeout exceeded while awaiting headers)
```
firewall suspicion
- In [gitlab-ci/terraform/stage/main.tf](gitlab-ci/terraform/stage/main.tf) port `5050` is added to the list of allowed ports for the gitlab server. Configuration applied is `make terraform_apply`. **FORTHERE** It is correct to create a separate rule that allows access to register only from raster. But such rules are more convenient to use at flat (without using modules) structure of terraform project.
- Changes in [.gitlab-ci.yml](.gitlab-ci.yml) that remove the `make` installation from `build_job` are saved.
- Next attempt to execute a Pipeline `make push_gitlab`
``log
Error response from daemon: Get https://gitlab.vscoder.ru:5050/v2/: dial tcp 35.195.25.130:5050: connect: connection refused
```
it looks like the registry port wasn't triggered when gitlab-server was running
- port mapping `5050:5050` is added to `docker-compose.yml` on host _gitlab.flexline.ru_. Hitlab restarted `cd /srv/gitlab && sudo docker-compose restart`.
- Try again... same error
- gitlab-server restarted through `sudo docker-compose down; docker-compose up -d` and login was successful!
- new bug:
``log
No way to prepare context: path "./post" not found
```
  - added a little debaag to the Pipeline... more debag)))
  ``Yaml
  # debug
  - pwd
  - ls -la
  - ls -la ./src
  - apk add tree
  - tree
  ```
  - When assembling the images, relative paths with `./src` instead of `src` are used.
  - The reason for the problem was that the directory with the `post` application is not called `post`, but `post-py`. B - pay attention! It should have been copied or checked normally.
  - Removed the debug.
  - Fixed path on `./post-py`.
- When you start the Pipeline, there's an error.
``log
Successfully tagged gitlab.vscoder.ru:5050/otus/example/post:gitlab-ci-1
$ cd ./src && docker build -t ${CI_REGISTRY_IMAGE}/comment:${CI_COMMIT_REF_NAME} ./comment
$ cd ./src && docker build -t ${CI_REGISTRY_IMAGE}/ui:${CI_COMMIT_REF_NAME} ./ui
$ docker push ${CI_REGISTRY_IMAGE}/post:${CI_COMMIT_REF_NAME}
/bin/sh: cd: line 92: can't cd to ./src: No such file or directory
/bin/sh: cd: line 94: can't cd to ./src: No such file or directory
...
$ docker push ${CI_REGISTRY_IMAGE}/comment:${CI_COMMIT_REF_NAME}
The push refers to repository [gitlab.vscoder.ru:5050/otus/example/comment]
An image does not exist locally with the tag: gitlab.vscoder.ru:5050/otus/example/comment
```
this is not a Makefile! All `script` commands are executed in one shell.
  - Pipeline's been changed. `cd` is executed only once.
    ``Yaml
      # build
      - cd ./src
      - docker build
    ```
- THE ASSEMBLY WAS A SUCCESS.
- The final `build_job`
``Yaml
build_job:
  stage: build
  It's not:
    DOCKER_HOST: unix:///var/run/docker.sock
  script:
    # login
    - docker info
    - docker login -u $CI_REGISTRY_USER -p $CI_REGISTRY_PASSWORD $CI_REGISTRY
    # build
    - cd ./src
    - docker build -t ${CI_REGISTRY_IMAGE}/post:${CI_COMMIT_REF_NAME} ./post-py
    - docker build -t ${CI_REGISTRY_IMAGE}/comment:${CI_COMMIT_REF_NAME} ./comment
    - docker build -t ${CI_REGISTRY_IMAGE}/ui:${CI_COMMIT_REF_NAME} ./ui
    # push
    - docker push ${CI_REGISTRY_IMAGE}/post:${CI_COMMIT_REF_NAME}
    - docker push ${CI_REGISTRY_IMAGE}/comment:${CI_COMMIT_REF_NAME}
    - docker push ${CI_REGISTRY_IMAGE}/ui:${CI_COMMIT_REF_NAME}
  tags:
    - dind
```

### Task from \ ##: Depleted container on the server created for the branch

Deposit the container from reddit to the server created for the branch.

Approximate plan:
- in packer prepare an image with docker
- in an image-based terraform to describe the host
- to implement the launch of the application using `docker-compose` from previously collected images

#### Implementation

#### Packer

- A playbook is created that installs the docker and the necessary packages [gitlab-ci/ansible/playbooks/packer-stage-server.yml](gitlab-ci/ansible/playbooks/packer-stage-server.yml).
``Yaml
---
- import_playbook: docker.yml

- name: Install docker on all hosts
  hosts: all
  become: true
  vars:
    ansible_python_interpreter: /usr/bin/python3
  I'm sorry:
    - name: Ensure packages are installed
      apt:
        name:
          - python3-pip
          - libffi-dev
          - libssl-dev
        state: present

    - name: Ensure docker-compose and docker is installed
      pip:
        executable: /usr/bin/pip3
        name:
          - docker
          - docker-compose
        state: present
```
- Created [gitlab-ci/packer/variables-stage-server.json](gitlab-ci/packer/variables-stage-server.json) file with variables describing the stage server.
`json
{
  "source_image_family": "ubuntu-1604-lts",
  "image_family": "stage-server-base."
  "machine_type": "g1-small",
  "disk_size": "40",
  "playbook_name": "packer-gitlab-runner.yml"
}
```
- Validation `make packer_validate PACKER_VAR_FILE=packer/variables-stage-server.json` successful
- Collected image `make packer_build PACKER_VAR_FILE=packer/variables-stage-server.json`.

#### Terraform

- To [gitlab-ci/terraform/stage/main.tf](gitlab-ci/terraform/stage/main.tf) added `Stage server`.
``hcl
# Stage server
stage-server" module {
  instance_count = 1
  source = ".../modules/instance"
  project = var.project
  zone = var.zone
  environment = var.environment
  name_prefix = "stage-server"
  machine_type = "g1-small"
  instance_disk_image = "stage-server-base"
  tags = ["stage-server"]
  tcp_ports = ["22", "80", "443"]
  vpc_network_name = var.vpc_network_name
  use_static_ip = false
}
```
- in [gitlab-ci/terraform/stage/outputs.tf](gitlab-ci/terraform/stage/outputs.tf) added display of external ip
``hcl
...
output stage_server_external_ip" {
  value = module.stage-server.instances_external_ip
}
```
- terraform is initialized `make terraform_init `
- The infrastructure is applied `make terraform_apply`.

##### Ansible

##### Searching for a solution

[Ansible Docker Guide] (https://docs.ansible.com/ansible/latest/scenario_guides/guide_docker.html)

You can use modules to implement the task:

- [docker_container](https://docs.ansible.com/ansible/latest/modules/docker_container_module.html)
- [docker_compose](https://docs.ansible.com/ansible/latest/modules/docker_compose_module.html)

After a brief study, it was decided to use `docker_compose` as a simpler solution.

##### implementation

- Playbook created [gitlab-ci/ansible/playbooks/deploy-dev.yml](gitlab-ci/ansible/playbooks/deploy-dev.yml)
- The content of the compose file was copied from [src/docker-compose.yml](src/docker-compose.yml) to [gitlab-ci/ansible/playbooks/deploy-dev.yml](gitlab-ci/ansible/playbooks/deploy-dev.yml).
- When running the `ansible-playbook -i environments/stage/inventory.gcp.yml playbooks/stage-server.yml --check` error:
``log
[stage-server-stage-001]: FAILED! => {"ansible_facts": {"discovered_interpreter_python"}: "/usr/bin/python"}, "changed": false, "msg": "Unable to find any of pip2, pip to use.  pip needs to be installed." }
```
- As a result, the base image was repackaged. Details in the packer description
- Playbook application `cd gitlab-ci/ansible && ansible-playbook -i environments/stage/inventory.gcp.yml playbooks/stage-server.yml`
- Error
``log
[stage-server-stage-001]: FAILED! => {"ansible_facts": {"discovered_interpreter_python"}: "/usr/bin/python"}, "changed": false, "module_stderr": "Shared connection to 35.240.27.254 closed.\r\n", "module_stdout": "\r\nTraceback (most recent call last):\r\n File \"/home/appuser/.ansible/tmp/ansible-tmp-1575154178.6186209-224854152348994/AnsiballZ_docker_compose. py\", line 102, in <module>\r\n _ansiballz_main()\r\n File \"/home/appuser/.ansible/tmp/ansible-tmp-1575154178.6186209-224854152348994/AnsiballZ_docker_compose. py\", line 94, in _ansiballz_main\r\n invoke_module(zipped_mod, temp_path, ANSIBALLZ_PARAMS)\r\n File \"/home/appuser/.ansible/tmp/ansible-tmp-1575154178. 6186209-224854152348994/AnsiballZ_docker_compose.py\", line 40, in invoke_module\r\n runpy.run_module(mod_name='ansible.modules.cloud.docker. docker_compose', init_globals=None, run_name='__main__', alter_sys=True)\r\n File \"/usr/lib/python2.7/runpy.py\", line 188, in runmodule\r\n fname, loader, pkg_name)\r\n File \"/usr/lib/python2. 7/runpy.py\", line 82, in _run_module_code\r\n mod_name, mod_fname, mod_loader, pkg_name)\r\n File \"/usr/lib/python2.7/runpy. py\", line 72, in _run_code\r\n File \"/tmp/ansible_docker_compose_oSfl3K/ansible_docker_compose_payload. zip/ansible/modules/cloud/docker/docker_compose.py\", line 483, in <module>\r\n File \"/usr/local/lib/python2.7/dist-packages/compose/cli/command.py\", line 12, in <module>\r\n from ... import config\r\n File \"/usr/local/lib/python2.7/dist-packages/compose/config/__init__.py\", line 6, in <module>\r\n from .config import ConfigurationError\r\n File \"/usr/local/lib/python2. 7/dist-packages/compose/config.py\", line 50, in <module>\r\n from .config import match_namedvolumes\r\n File \"/usr/local/lib/python2. 7/dist-packages/compose/config/validation.py\", line 12, in <module>\r\n from jsonschema import Draft4Validator\r\n File \"/usr/local/lib/python2. 7/dist-packages/jsonschema/__init__.py\", line 33, in <module>\r\n import import_metadata as metadata\r\n File \"/usr/local/lib/python2. 7/dist-packages/importlib_metadata/__init__.py\", line 9, in <module>\r\n import zipp\r\n File \"/usr/local/lib/python2.7/dist-packages/zipp. py\", line 12, in <module>\r\n import more_itertools\r\n File \"/usr/local/lib/python2.7/dist-packages/more_itertools/__init__. py\", line 1, in <module>\r\n from more_itertools.more import * # noqa\r\n File \"/usr/local/lib/python2.7/dist-packages/more_itertools/more. py\", line 460\r\n yield from iterable\r\n ^\r\nSyntaxError: invalid syntax\r\n", "msg": "MODULE FAILURE\nSee stdout/stderr for the exact error", "rc": 1}
```
  - The problem only showed up for docker-compose on python2.
  - Adapting [gitlab-ci/ansible/playbooks/packer-stage-server.yml](gitlab-ci/ansible/playbooks/packer-stage-server.yml) to work with python3 has been done. For this purpose.
    - The variable `ansible_python_interpreter: /usr/bin/python3` is set in play.
    - The necessary packages for docker-compose are installed
    ``Yaml
    - python3-pip
    - libffi-dev
    - libssl-dev
    ```
    - For the module `pip: `executable: /usr/bin/pip3` parameter is set.
  - Reassembly of the base image and the redeploy host
  ``shell
  make packer_build PACKER_VAR_FILE=packer/variables-stage-server.json
  cd terraform/stage
  terraform taint "module.stage-server.google_compute_instance.instance[0]".
  cd ../../
  make terraform_apply
  yes
  ```
- Trying to roll up a `cd ./ansible && ansible-playbook -i environments/stage/inventory.gcp.yml playbooks/stage-server.yml`.
- HOORAY! New error))
``log
"Error starting project 400 Client Error: Bad Request (\"no such image: comment:: invalid reference format\")".
```
no images are registered or the image name is incorrectly generated
TODO: time for bed 
**PRICK** image loading should be performed on gitlab-runner for correct variable substitution
- In [.gitlab-ci.yml](.gitlab-ci.yml) we will work with `deploy_dev_job: `.

##### Preparations for gitlab-runner.

The challenge is a gitlab-runner-deployable

Solution options:
- Throw ssh keys from an early container into https://www.bevuta.com/en/blog/continuous-delivery-with-gitlab-ci-and-ansible-part-1/.
- Example `.gitlab-ci.yml` where the key is farted to the variable https://github.com/mikhno-s/gitlab-ci-deploy-ansible/blob/master/.gitlab-ci.yml.
- Similar solution, but described in the article https://ealebed.github.io/posts/2017/gitlab-ci-часть-9-этап-deploy-в-.gitlab-ci.yml/ Ansible is not used -- but an interesting way of keying is described.

Learn more about working with gce https://docs.ansible.com/ansible/latest/scenario_guides/guide_gce.html.

The docker-image [cytopia/ansible:2.9] (https://hub.docker.com/r/cytopia/ansible) has been selected for the deposition. Advantages are described on the link. The analysis of the commands (eyes) used for the assembly did not reveal any contraindications. **WARNING**: you could have screwed in the automated security analysis and other buns -- but it's better to leave it to the image developers. The image is quite popular (10M+).

Description `deploy_dev_job`.
- The first thing to do is to install dependencies
``shell
ansible-galaxy install -r environments/stage/requirements.yml
```
- Then we'll display our inventory, but to do this we need to pass gcp `credentials.json` to the earlier.
  - The project created a variable `GCP_SERVICE_ACCOUNT_FILE` of the file type with content `~/.gce/docker-257914-ansible-inventory.json` as a value
  - show `ansible-invfentory -i environments/stage/inventory.gcp.yml list`.
- Parsing error `inventory.gcp.yml` due to lack of necessary libraries.
  - Put the libraries `pip3 install requests google-auth`.
- Error, does not find `/root/.gce/docker-257914-ansible-inventory.json`.
  - Added debugging message `echo GCP_SERVICE_ACCOUNT_FILE=$GCP_SERVICE_ACCOUNT_FILE`.
  - Displays the file name. Looks like an inverter module bug.
  - Commenting `service_account_file` to [gitlab-ci/ansible/environments/stage/inventory.gcp.yml] (gitlab-ci/ansible/environments/stage/inventory.gcp.yml) ** helped**.
  - A separate inventory [gitlab-ci/ansible/environments/stage/runner-inventory.gcp.yml](gitlab-ci/ansible/environments/stage/runner-inventory.gcp.yml) has been created for the earlier one without specifying `service_account_file`.
- Pipeline was a success.
- Playbook `gitlab-ci/ansible/playbooks/stage-server.yml' renamed to [gitlab-ci/ansible/playbooks/deploy-dev.yml](gitlab-ci/ansible/playbooks/deploy-dev.yml)
- The next step is to apply the playbook `ansible-playbook -i environments/stage/runner-inventory.gcp.yml playbooks/deploy-dev.yml -vvvvv`.
  - **Note** no config is used
  ``log
  [WARNING]: Ansible is being run in a world writable directory
  (/builds/otus/example/gitlab/ansible), ignoring it as an ansible.cfg source.
  For more information see
  https://docs.ansible.com/ansible/devel/reference_appendices/config.html#cfg-in-
  world-writable-dir
  enable-playbook 2.9.1
    config file = None
    configured module search path = ['/root/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules'].
    possible python module location = /usr/lib/python3.6/site-packages/ansible
    executable location = /usr/bin/ansible-playbook
    python version = 3.6.9 (default, Oct 17 2019, 11:10:22) [GCC 8.3.0].
  No config file found; using defaults
  ```
- Error `FileNotFoundError: [Errno 2] No such file or directory: b'ssh': b'ssh'. Problem -- no ssh client.
  - Installing the ssh client ``` which ssh-agent || (apk update && apk add openssh-client)``.
- Error `Host key verification failed. `
  - Ignoring the host key `export ANSIBLE_HOST_KEY_CHECKING=False`.
- Error `Permission denied (public key). We need to throw in the key.
  - You have to throw in the key. Link to https://docs.gitlab.com/ce/ci/ssh_keys/.
  - It is possible to use a key with a password, but the password must be passed through a variable. Privants are described [here] (https://unix.stackexchange.com/questions/90853/how-can-i-run-ssh-add-automatically-without-a-password-prompt). But for the production environment, other mechanisms must be used
  - Passwordless key generated (to avoid unnecessary complications)
  ``shell
  ssh-keygen -t rsa -f ~/.ssh/id_rsa_appuser_deploy_stage
  ```
  - In gitlab project added variable `SSH_PRIVATE_KEY`, type `file`, containing private ssh key to connect to stage-server.
  - In [gitlab-ci/ansible/playbooks/packer-stage-server.yml] [gitlab-ci/ansible/playbooks/packer-stage-server.yml] -- the playbook used to burn the packer image is implemented by adding an ssh key for deploying.
  - A new basic VM image has been built
  - terraform-instance has been renamed dev-server
  - Re-created instance `make terraform_apply `
  - The key in [gitlab-ci/ansible/playbooks/packer-stage-server.yml](gitlab-ci/ansible/playbooks/packer-stage-server.yml) is now taken from the file instead of the hardcode.
- Trying to execute a Pipeline
- Error
``shell
$ echo "$SSH_PRIVATE_KEY" | tr -d '\r' | ssh-add -
Error loading key "(stdin)": invalid format
```
The problem is that the type of variable `file`. Fixed it on 
``shell
cat "$SSH_PRIVATE_KEY" | tr -d '\r' | ssh-add -
```
- Trying to execute a Pipeline
- Not successfully fulfilled)) `[WARNING]: Could not match supplied host pattern, ignoring: stage_server`.
  - Fixed playbook target host on `hosts: dev_server`.
- Error: Playbook can't see the ssh key.
  - Instead of using the `ssh-agent`, the path to the ssh key is specified in the environment variable
  ``shell
  export ANSIBLE_SSH_PRIVATE_KEY_FILE="$SSH_PRIVATE_KEY".
  ```
  - Specified user 
  ``shell
  export ANSIBLE_SSH_USER=appuser
  ```
  - Disconnected `become: true`
  - Same mistake
  ``log
  <35.195.42.124> ESTABLISH SSH CONNECTION FOR USER: None
  <35.195.42. 124> SSH: EXEC ssh -vvv -C -o ControlMaster=auto -o ControlPersist=60s -o StrictHostKeyChecking=no -o KbdInteractiveAuthentication=no -o PreferredAuthentications=gssapi-with-mic,gssapi-keyex,hostbased,publickey -o PasswordAuthentication=no -o ConnectTimeout=10 -o ControlPath=/root/. ansible/cp/1ae30ff2c4 35.195.42.124 '/bin/sh -c '"""echo ~ && sleep 0"""
  ```
  It looks like the variables have no effect
  - YOU NEED TO READ THE DOCUMENTATION!!!
  - Variable names have been changed
  ``shell
  export ANSIBLE_REMOTE_USER=appuser
  export ANSIBLE_PRIVATE_KEY_FILE="$SSH_PRIVATE_KEY".
  ```
  - Fixed private key permissions
  ``shell
  chmod 0600 "$SSH_PRIVATE_KEY"
  ```
- The `appuser` user has been parameterized, using the default value (**Value!** added later, not tested. Will have something to do tonight)). Link to [StackOverflow] source (https://stackoverflow.com/questions/2013547/assigning-default-values-to-shell-variables-with-a-single-command-in-bash).
  ``shell
  export ANSIBLE_REMOTE_USER=${ANSIBLE_USER:-appuser}
  ```
- Last Pipeline Result: Error
``log
"msg": "Error connecting: Error while fetching server API version: ('Connection aborted.', PermissionError(13, 'Permission denied')").
```
  - possible reason: inability to connect to docker-demon from under the current user
  - Solution options:
    - [x] grant rights to the appuser user
    - [ ] start the song with `become: yes`.
  - The first option was chosen as the most appropriate from a security point of view
    - In [gitlab-ci/ansible/playbooks/packer-stage-server.yml](gitlab-ci/ansible/playbooks/packer-stage-server.yml) when importing the `docker.yml` playbook, the following variables have been added
      ``Yaml
      - import_playbook: docker.yml
        vars:
          docker_users:
            - appuser
      ...
      ```
  - Reassembly of the packer-image, re-creation of authority
  ``shell
  # packer
  make packer_validate packer_build PACKER_VAR_FILE=packer/variables-stage-server.json
  # terraform
  cd terraform/stage
  terraform state list
  terraform taint "module.dev-server.google_compute_instance.instance[0]".
  cd -
  make terraform_apply
  ```
  - Pipeline launch...
- Error
``log
"msg": "Error starting project 400 Client Error: Bad Request (\"no such image: ui: invalid reference format\")".
```
problem: variable substitution does not work
  - The substitution of variables is done via `lookup('env', 'VAR_NAME')` in [gitlab-ci/ansible/playbooks/deploy-dev.yml](gitlab-ci/ansible/playbooks/deploy-dev.yml).
  ``Yaml
  vars:
    ...
    ci_registry_image: "{{{ lookup('env', 'CI_REGISTRY_IMAGE') }}".
    ci_commit_ref_name: "{{{ lookup('env','CI_COMMIT_REF_NAME') }}".
  ```
  - Added variable value debag
  ``Yaml
  - name: Debug vars
      debug:
        msg: |
          ci_registry_image: {{{ci_registry_image }}.
          ci_commit_ref_name: {{{ci_commit_ref_name }}.
  ```
- Pipeline launch: login is expected to be required.
- As expected, a mistake
``log
"msg": "Error starting project 500 Server Error: Internal Server Error (\ "Get https://gitlab.vscoder.ru:5050/v2/otus/example/ui/manifests/gitlab-ci-1: denied: access forbidden\")".
```
cure: need [docker_login](https://docs.ansible.com/ansible/latest/modules/docker_login_module.html)
- Added login to the docker.
``Yaml
vars:
  ci_registry: "{{{lookup('env', 'CI_REGISTRY') }}".
  ci_registry_user: "{{{lookup('env','CI_REGISTRY_USER') }}".
  ci_job_token: "{{{lookup('env','CI_JOB_TOKEN') }}".
  ...
Oh..:
  - name: Login to gitlab docker registry
    docker_login:
      username: "{{{ci_registry_user }}"
      password: "{{{ci_job_token }}"
      state: present
      #debug: false
      registry_url: "{{{ci_registry }}"
```
- Launch the Pipeline... **HOORAY! HOORAY! HOORAY! HOORAY.
  ``log
  Job succeeded
  ```

##### Checking

I was unable to connect to http://34.76.75.218:9292/. Cause is the firewall.
In [gitlab-ci/terraform/stage/main.tf] `module "dev-server"` the list of ports is given to `tcp_ports = ["22", "9292"]`.

The app has opened, but the comments don't work...

Presumably, the reason is the lack of service (or alias) `comment_db`. The service is created:
```yaml
service:
  ...
  comment_db:
    image: mongo:3.2
    Mongo:3.2:
      - comment_db:/data/db
    Networks:
        - reddit_back
  ...
```

Pipeline launch... error, no description of `comment_db` volume was added to `volumes:`. Fixed.
Pipeline was launched ** successfully**.
Check: http://34.76.75.218:9292.
Comments are created. Comments are visible.

This task **completed successfully**!

###### creating environment

To add a correct link, you can do the following:
- [x] a wildcard entry `*.vscoder.ru A 35.195.25.130' is created in dns, pointing to an ip with a gitlab server.
- [x] during Pipeline on host 35.195.25.130, pick up a container with nginx that will act as reverse-proxy to our dev-server.
  - The ip of dev-server can be obtained from ansible inventory
  - to authorize ansible on gitlab.vscoder.ru, you can use the appuser_docker ssh key, which is added by terraform
  - you can use ansible module `docker_container` or `docker_compose` to deploy the container with nginx. The `docker_compose` module will be used as already tested.

Here we go:

In terraform [gitlab-ci/terraform/stage/main.tf] (gitlab-ci/terraform/stage/main.tf) added tag to gitlab-server and port `8080` is opened.

``hcl
...
"docker-app" {
  ...
  tags = ["gitlab-server", "branch-proxy"]
  tcp_ports = ["80", "443", "22", "2222", "5050", "8080"]
  ...
}
...
```
`make terraform_apply`

In dns the wild card record `*.vscoder.ru A 35.195.25.130 ` is created, pointing to ip with gitlab server.

In [gitlab-ci/ansible/playbooks/deploy-dev.yml](gitlab-ci/ansible/playbooks/deploy-dev.yml) added play
``Yaml
- name: "Provide nginx reverse-proxy for branch {{{ ci_commit_ref_name }}".
  hosts: branch_proxy
  gather_facts: no
  vars:
    ansible_python_interpreter: /usr/bin/python3
    nginx_image_tag: "1.17.6-alpine."
    ci_commit_ref_name: "{{{ lookup('env','CI_COMMIT_REF_NAME') }}".
    ci_registry: "{{{lookup('env', 'CI_REGISTRY') }}".
    ci_registry_user: "{{{lookup('env','CI_REGISTRY_USER') }}".
    ci_job_token: "{{{lookup('env','CI_JOB_TOKEN') }}".
  I'm sorry:
    - name: Debug vars
      debug:
        msg: |
          nginx_image_tag: {{{ nginx_image_tag }}.
          ci_commit_ref_name: {{{ci_commit_ref_name }}.
          ci_registry: {{{ci_registry }}.
          ci_registry_user: {{{ci_registry_user }}.
          ci_job_token: {{{ci_job_token }}.
    - name: Provide nginx config
      copy:
        dest: /etc/nginx.conf
        mode: 0444
        content: |
          events {
            The worker_connections 1024;
          }
          http {
            server {
              listen 80;
              listen [::]:80;

              server_name {{{ ci_commit_ref_name }}-branch.vscoder.ru;

              location / {
                  proxy_pass http://{{{ hostvars['dev-server-stage-001']['ansible_default_ipv4']['address'] }}:9292/;
              }
            }
          }
    - name: Login to gitlab docker registry
      docker_login:
        username: "{{{ci_registry_user }}"
        password: "{{{ci_job_token }}"
        state: present
        #debug: false
        registry_url: "{{{ci_registry}}"
    - name: Deploy nginx
      docker_compose:
        project_name: branchproxy
        debug: yes
        definition:
          version: "3.3"
          services:
            nginx:
              image: "nginx:{{{ nginx_image_tag }}".
              ports:
                - 8080:80
              Ah:
                - /etc/nginx.conf:/etc/nginx/nginx.conf:ro
      register: output

    - debug:
        var: output

    - Assert:
        that:
          - "nginx.branchproxy_nginx_1.state.running".
```

In [.gitlab-ci.yml](.gitlab-ci.yml) added environment
``Yaml
Environment:
  name: dev
  url: http://${CI_COMMIT_REF_NAME}-branch.vscoder.ru
```

Pipeline launch... Error:
``log
"msg": "The task includes an option with an undefined variable. The error was: 'ansible.vars.hostvars.hostVarsVars object' has no attribute 'default_ipv4'\n\nThe error appears to be in '/builds/otus/example/gitlab/ansible/playbooks/deploy-dev. yml': line 103, column 7, but may\nbe elsewhere in the file depending on the exact syntax problem.\n\nThe offending line appears to be:\n\n ci_job_token: {{{ci_job_token}}\n - name: Provide nginx config\n ^ here\n".
```
Assumed reason: the facts about the host `dev-server-stage-001` within the given play are not received.

We receive the facts:
``yaml
- name: "Get facts about {{{ branch_server}}"
  Oh:
  delegate_to: "{{{ branch_server }}"
  delegate_facts: yes
```

Pipeline launch... Same mistake. But debag is a good thing.)

Fixed variable getting ip o fbranch_server
``log
hostvars['dev-server-stage-001']['ansible_default_ipv4']['address'].
```

Pipeline launch... Error
``log
appuser@35.195.25.130: Permission denied (public key).
```
Reason: for gitlab-runner we have our own ssh key without password.

We need to deliver the key to the gitlab-server. At this stage, this will be done by hand, because reassembling the packer image will cause the gitlab instance to be recreated, which in turn will nullify the gitlab configuration. TODO: think about making such changes without losing data.

The key has been added. Run the Pipeline... Error .
``log
TASK [Provide nginx config] ************************************************
...
"msg": "Destination /etc not writable."
```

Add `become: yes` to TASK [Provide nginx config].

Launch the Pipeline... Error:
``log
"msg": "Failed to import the required Python library (Docker SDK for Python: docker (Python >= 2.7) or docker-py (Python 2.6)) on gitlab-stage-001's Python /usr/bin/python3. Please read module documentation and install at the appropriate location. If the required library is installed, but Ansible is using the wrong Python interpreter, please consult the documentation on ansible_python_interpreter, for example via `pip install docker` or `pip install docker-py` (Python 2.6). The error was: No module named 'docker'".
```

Familiar rake))

Removed from [gitlab-ci/ansible/playbooks/packer-stage-server.yml] (but it would be more correct to add to the base image for gitlab-server).
``Yaml
- name: Ensure packages are installed
  apt:
    name:
      - python3-pip
      - libffi-dev
      - libssl-dev
    state: present

- name: Ensure docker-compose and docker is installed
  pip:
    executable: /usr/bin/pip3
    name:
      - docker
      - docker-compose
    state: present
```

Pipeline launch... ...is missing the permish again.

Added `become: yes` to the play level, because appuser on gitlab-server is not in the docker group.

Pipeline launch... **Pipeline's working.

We go to http://gitlab-ci-1-branch.vscoder.ru:8080/ and get a connection reset. Because nginx port 8080 is in config, and we have a redirect to container 80. Fixed the nginx config.

Launching the Pipeline... Same thing.
``shell.
sudo docker ps
```
ain't got no nginx running.
``shell
sudo docker ps -a
```
showed that the container was stopped
``shell
sudo docker logs branchproxy_nginx_1
```
``log
2019/12/03 20:41:39 [emerg] 1#1: "server" directive is not allowed here in /etc/nginx/nginx.conf:1
nginx: [emerg] "server" directive is not allowed here in /etc/nginx/nginx.conf:1
2019/12/03 20:47:09 [emerg] 1#1: "server" directive is not allowed here in /etc/nginx/nginx.conf:1
nginx: [emerg] "server" directive is not allowed here in /etc/nginx/nginx.conf:1
```
Well, yeah, that's a little crooked, I wrote)) Fixed. Described above.

Pipeline launch... Config bug. Corrected.

Run Pipeline... **IT WORKS!!.** the link opened the site)).

Fixed link in `environment:`paipline. The site opens by link.

Refactoring [.gitlab-ci.yml](.gitlab-ci.yml) will not be performed. Variable debar, detailed output and other debug messages remain as an example to be used in the future. The main thing is a working skin and it is documented.

In [.gitlab-ci.yml](.gitlab-ci.yml) `deploy_dev_job` the name environment-is now set to `${CI_COMMIT_REF_NAME}`.
Tested.

### Task from \ #: Automated creation and registration of scanners

Think about automating Gitlab CI Runner deployment and registration. In large organizations, the number of Runners can exceed 50 or more, making it difficult to get your hands on them.
Add implementation functionality to the repository in your gitlab-ci folder;

Implemented as part of the image assembly task.

In order to comply with the RS conditions, the directory `gitlab/` has been renamed to `gitlab-ci/`, with a correction of references in [.gitlab-ci.yml](.gitlab-ci.yml) and [README.md](README.md).

All the pipelins have been checked... successfully!

##### Skyling Ranner Development

In terraform [gitlab-ci/terraform/stage/main.tf] (gitlab-ci/terraform/stage/main.tf) the number of instances `module "gitlab-runner" ` is set to 3.
``hcl
# Gitlab Runner
module "gitlab-runner" {
  instance_count = 3
  ...
```
The infrastructure `make terraform_apply` is applied.
Ranners `cd ./ansible && ansible-playbook -i environments/stage/inventory.gcp.yml playbooks/gitlab-runner.yml`. No errors.

But no new early adopters have been registered. Presumed reason: variable `gitlab_runner_registration_token` is taken from environment variable `$GITLAB_RUNNER_REGISTRATION_TOKEN` on the machine from which the playbook is started. This variable is not set. Treatment:
``hell
export GITLAB_RUNNER_REGISTRATION_TOKEN="hereisatoken"
```

Playbook `ansible-playbook -i environments/stage/inventory.gcp.yml playbooks/gitlab-runner.yml` has been restarted.

The new rangers have appeared on the list.

All the pyramids have been passed successfully. The Pipelins have worked on the new Ranners.

### Task from \*: Sending notifications about pipeline work to Slack

Configure the integration of your Pipeline with the Slack test chat you used earlier. To do this, go to Project Settings > Integrations > Slack notifications. You need to set active, select events and fill in the fields from your Slack webhook URL.
Add a link to the channel in the slack where you can check the notifications in the README.md file;

About slack webhooks https://api.slack.com/messaging/webhooks.

1. Create a Slack app (if you don't have one already). Link is in docs
2. Enable Incoming Webhooks
3. Create an Incoming Webhook
4. webhook is registered in gitlab.
> Slack notifications activated.

Link to the channel: https://devops-team-otus.slack.com/archives/CMZK1KA02


### Passing travis-ci tests

The [.gitlab-ci.yml](.gitlab-ci.yml) returns the previously deleted commands required to run the reddit application's facet test.
The travis-ci tests are passed.

Pipeline in gitlab is launched - error:
``log
ERROR: The ruby:2.4.2 is not presented on a list of allowed images
- docker:*
```
The reason is the restriction at an early stage.

Treatment: build_job is explicitly specified in `image: docker:19.03.1`. 

Pipeline check: `make push_gitlab`.

Error
``log
$ bundle install
/bin/sh: eval: line 94: bundle: not found
ERROR: Job failed: exit code 127
```
Problem: the missing bundler utility in the docker image that runs `before_script`. Since no bundler is needed within our pipeline in `build_job`, we try to redefine `before_script` to `build_job`.
```yaml
before_script:
  - echo 'Before script override for build_job'
```

Pipeline launch... Same error for deploy_dev_job. Fixed:
``yaml
deploy_dev_job:
  before_script:
    - echo 'Before script override for deploy_dev_job'.
...
```

Pipeline gitlab-ci was a success.
Pipeline travis-ci was a success.

TODO: can I also send a link to environment in my message?


### Other

Added [gitlab-ci/docker-compose.yml](gitlab-ci/docker-compose.yml) to deploy the gitlab server.

## HomeWork 16: Introduction to monitoring. Monitoring systems.

### Prometheus: launch, configuration, introduction to Web UI.

#### Starting docker-machine host for prometheus

Let's create a firewall rule for Prometheus and Puma:

``shell
gcloud compute firewall-rules create prometheus-default --allow tcp:9090
gcloud compute firewall-rules create puma-default --allow tcp:9292
```

Create a Docker host in GCE and configure the local environment to work with it
``shell
export GOOGLE_PROJECT=<project_id>

docker-machine create --driver google \.
  --google-machine-image https://www.googleapis.com/compute/v1/projects/ubuntu-os-cloud/global/images/family/ubuntu-1604-lts \.
  --google-machine-type n1-standard-1 \.
  --google-zone europe-west1-b \
  docker-host

eval $(docker-machine env docker-host)
```

#### Starting prometheus

The Prometheus monitoring system will be launched inside the Docker container. For the initial acquaintance we will use the ready image from the DockerHub (the latest version is used - a newer version than in the remote control).
``shell
docker run --rm -p 9090:9090 -d --name prometheus prom/prometheus:v2.14.0
```
``log
Digest: sha256:907e20b3b0f8b0a76a33c088fe9827e8edc180e874bd2173c27089eade63d8b8
Status: Downloaded newer image for prom/prometheus:v2.14.0
ba7f92afa8bc8e3542d60f25faae8f76f1459fa3ea2aeb5c4e954b2bda73957c
```

List of running containers
``shell
docker ps
```
``log
CONTAINER ID IMAGE COMMAND CREATED STATUS PORTS NAMES
ba7f92afa8bc prom/prometheus:v2.14.0 "/bin/prometheus --c..."   49 seconds ago Up 45 seconds 0.0.0.0:9090->9090/tcp prometheus
```

#### Web interface

IP running docker-machine
``shell
docker-machine ip docker-host
```
``log
34.76.241.120
```

The web-interface is open at http://34.76.241.120:9090.

By default, prometheus collects statistics about its work. For example, let's select the metric `prometheus_build_info` and click Execute to see the version information.
``log
prometheus_build_info{branch="HEAD",goversion="go1.13.4",instance="localhost:9090",job="prometheus",revision="edeb7a44cbf745f1d8be4ea6f215e79e651bfe19",version="2.14.0".}	
```

`prometheus_build_info` - metric name - identifier of the collected information.

`branch`, `goversion`, `instance`, etc... - ...label - adds metadata to the metric, clarifies it. Using labels allows us to go beyond just one name of metrics to identify the information we get. Labels are contained in `{}} brackets and are represented by sets of "key=value".

HEAD, go1.13.4, etc... - metric value - the numerical value of the metric, or NaN, if the value is not available


#### Targets

Targets - are the systems or processes that Prometheus monitors. Remember that Prometheus is a pull system, so it constantly makes HTTP requests to its available addresses (endpoints). Let's take a look at the current list of targets:

Status -> Targets

At Targets now we only see Prometheus itself. Each Targets has its own list of _(endpoints)_ addresses to contact for information.

In the web interface we can see the status of each endpoint-(up); the label (`instance="someURL"`) that Prometheus automatically adds to each metric received from that endpoint-(up); and the time that has elapsed since the last information collection operation from the endpoint-(up).

Also, errors are displayed here, if any, and you can filter out only inanimate targettes.

Note the endpoint that we saw on the previous slide.

We can open a web browser page on this HTTP path (host:port/metrics) to see what the information Prometheus collects looks like. **Application** The web interface displays url http://localhost:9090/metrics which refers to localhost instead of ip remote intranet. To view the metrics you need to manually specify ip http://34.76.241.120:9090/metrics.

<details><summary>Metrics Link</summary>.
<p>

#### List of metrics

``log
# HELP go_gc_duration_seconds A summary of the GC invocation durations.
# TYPE go_gc_duration_seconds summary
go_gc_duration_seconds{quantile="0"} 5.955e-06
go_gc_duration_seconds{quantile="0.25"}. 1.6163e-05
go_gc_duration_seconds{quantile="0.5"}. 2.141e-05
go_gc_duration_seconds{quantile="0.75"}. 2.5613e-05
go_gc_duration_seconds{quantile="1"}. 4.4607e-05
go_gc_duration_seconds_sum 0.00047029
go_gc_duration_seconds_count 22
# HELP go_goroutines Number of goroutines that currently exist #
# TYPE go_goroutines gauge
go_goroutines 40
# HELP go_info information about the Go environment.
# TYPE go_info gauge
go_info{version="go1.13.4"} 1
# HELP go_mstemstats_alloc_bytes Number of bytes and still in use.
# TYPE go_memstats_alloc_bytes gauge
go_memstats_alloc_bytes 1.410276e+07
# HELP go_memstats_alloc_bytes_total total number bytes, even if freed.
# TYPE go_memstats_alloc_bytes_total counter
go_memstats_alloc_bytes_total 5.9071968e+07
# HELP go_memstats_buck_hash_sys_bytes Number of bytes used by the profiling bucket hash table.
# TYPE go_memstats_buck_hash_sys_bytes gauge
go_memstats_buck_hash_sys_bytes 1.464544e+06
# HELP go_memstats_frees_total total number of frees.
# TYPE go_memstats_frees_total counter
go_memstats_frees_total 480971
# HELP go_memstats_gc_cpu_fraction The fraction of this program's available CPU time used by the GC since the program started.
# TYPE go_memstats_gc_cpu_fraction gauge
go_memstats_gc_cpu_fraction 1.0147006692597942e-05
# HELP go_memstats_gc_sys_bytes Number of bytes used for garbage collection system metadata.
# TYPE go_memstats_gc_sys_bytes gauge
go_memstats_gc_sys_bytes 2.398208e+06
# HELP go_memstats_heap_alloc_bytes Number of heap bytes and still in use.
# TYPE go_memstats_heap_alloc_bytes gauge
go_memstats_heap_alloc_bytes 1.410276e+07
# HELP go_memstats_heap_idle_bytes Number of heap bytes waiting to be used.
# TYPE go_memstats_heap_idle_bytes gauge
go_memstats_heap_idle_bytes 5.0233344e+07
# HELP go_memstats_heap_inuse_bytes Number of heap bytes that are in use.
# TYPE go_memstats_heap_inuse_bytes gauge
go_memstats_heap_inuse_bytes 1.622016e+07
# HELP go_memstats_heap_objects Number of objects.
# TYPE go_memstats_heap_objects gauge
go_memstats_heap_objects 72304
# HELP go_memstats_heap_released_bytes Number of heap bytes released to OS.
# TYPE go_memstats_heap_released_bytes gauge
go_memstats_heap_released_bytes 4.825088e+07
# HELP go_memstats_heap_sys_bytes Number of heap bytes obtained from system.
# TYPE go_memstats_heap_sys_bytes gauge
go_memstats_heap_sys_bytes 6.6453504e+07
# HELP go_memstats_last_gc_time_seconds Number of seconds since 1970 of last garbage collection.
# TYPE go_memstats_last_gc_time_seconds gauge
go_memstats_last_gc_time_seconds 1.5757971694422157e+09
# HELP go_memstats_lookups_total total number of pointer lookups.
# TYPE go_memstats_lookups_total counter
go_memstats_lookups_total 0
# HELP go_memstats_mallocs_total Total number of mallocs.
# TYPE go_memstats_mallocs_total counter
go_memstats_mallocs_total 553275
# HELP go_memstats_mcache_inuse_bytes Number of bytes in use by mcache structures.
# TYPE go_memstats_mcache_inuse_bytes gauge
go_memstats_mcache_inuse_bytes 1736
# HELP go_memstats_mcache_sys_bytes Number of bytes used for mcache structures obtained from system.
# TYPE go_memstats_mcache_sys_bytes gauge
go_memstats_mcache_sys_bytes 16384
# HELP go_memstats_mspan_inuse_bytes Number of bytes in use by mspan structures.
# TYPE go_memstats_mspan_inuse_bytes gauge
go_memstats_mspan_inuse_bytes 145656
# HELP go_memstats_mspan_sys_bytes Number of bytes used for mspan structures obtained from system.
# TYPE go_memstats_mspan_sys_bytes gauge
go_memstats_mspan_sys_bytes 163840
# HELP go_memstats_next_gc_bytes Number of heap bytes when next garbage collection will take place.
# TYPE go_memstats_next_gc_bytes gauge
go_memstats_next_gc_bytes 2.6305792e+07
# HELP go_memstats_other_sys_bytes Number of bytes used for other system allocations.
# TYPE go_memstats_other_sys_bytes gauge
go_memstats_other_sys_bytes 348184
# HELP go_memstats_stack_inuse_bytes Number of bytes in use by the stack allocator.
# TYPE go_memstats_stack_inuse_bytes gauge
go_memstats_stack_inuse_bytes 655360
# HELP go_memstats_stack_sys_bytes Number of bytes obtained from system for stack allocator.
# TYPE go_memstats_stack_sys_bytes gauge
go_memstats_stack_sys_bytes 655360
# HELP go_memstats_sys_bytes Number of bytes obtained from system.
# TYPE go_memstats_sys_bytes gauge
go_memstats_sys_bytes 7.1500024e+07
# HELP go_threads Number of OS threads created.
# TYPE go_threads gauge
go_threads 9
# HELP net_conntrack_dialer_conn_attempted_total Total number of connections attempted by the given dialer a given name.
# TYPE net_conntrack_dialer_conn_attempted_total counter
net_conntrack_dialer_conn_attempted_total{dialer_name="alertmanager"} 0
net_conntrack_dialer_conn_attempted_total{dialer_name="default"} 0
net_conntrack_dialer_conn_attempted_total{dialer_name="prometheus"} 1
# HELP net_conntrack_dialer_conn_closed_total total number of connections closed which originated from the dialer of a given name.
# TYPE net_conntrack_dialer_conn_closed_total counter
net_conntrack_dialer_conn_closed_total{dialer_name="alertmanager"} 0
net_conntrack_dialer_conn_closed_total{dialer_name="default"} 0
net_conntrack_dialer_conn_closed_total{dialer_name="prometheus"} 0
# HELP net_conntrack_dialer_conn_established_total total number of connections successfully established by the given dialer a given name.
# TYPE net_conntrack_dialer_conn_established_total counter
net_conntrack_dialer_conn_established_total{dialer_name="alertmanager"} 0
net_conntrack_dialer_conn_established_total{dialer_name="default"} 0
net_conntrack_dialer_conn_established_total{dialer_name="prometheus"} 1
# HELP net_conntrack_dialer_conn_failed_total total number of connections failed to dial by the dialer a given name.
# TYPE net_conntrack_dialer_conn_failed_total counter
net_conntrack_dialer_conn_failed_total{dialer_name="alertmanager",reason="refused"}. 0
net_conntrack_dialer_conn_failed_total{dialer_name="alertmanager",reason="resolution"} 0
net_conntrack_dialer_conn_failed_total{dialer_name="alertmanager",reason="timeout"} 0
net_conntrack_dialer_conn_failed_total{dialer_name="alertmanager",reason="unknown"} 0
net_conntrack_dialer_conn_failed_total{dialer_name="default",reason="refused"} 0
net_conntrack_dialer_conn_failed_total{dialer_name="default",reason="resolution"}. 0
net_conntrack_dialer_conn_failed_total{dialer_name="default",reason="timeout"} 0
net_conntrack_dialer_conn_failed_total{dialer_name="default",reason="unknown"} 0
net_conntrack_dialer_conn_failed_total{dialer_name="prometheus",reason="refused"} 0
net_conntrack_dialer_conn_failed_total{dialer_name="prometheus",reason="resolution"} 0
net_conntrack_dialer_conn_failed_total{dialer_name="prometheus",reason="timeout"} 0
net_conntrack_dialer_conn_failed_total{dialer_name="prometheus",reason="unknown"} 0
# HELP net_conntrack_listener_conn_accepted_total Total number of connections opened to the listener of a given name.
# TYPE net_conntrack_listener_conn_accepted_total counter
net_conntrack_listener_conn_accepted_total{listener_name="http"} 15
# HELP net_conntrack_listener_conn_closed_total total number of connections closed that were made to the listener of a given name.
# TYPE net_conntrack_listener_conn_closed_total counter
net_conntrack_listener_conn_closed_total{listener_name="http"} 11
# HELP process_cpu_seconds_total Total user and system CPU time spent in seconds.
# TYPE process_cpu_seconds_total counter
process_cpu_seconds_total 1.42
# HELP process_max_fds Maximum number of open file descriptors.
# TYPE process_max_fds gauge
process_max_fds 1.048576e+06
# HELP process_open_fds Number of open file descriptors.
# TYPE process_open_fds gauge
process_open_fds 14
# HELP process_resident_memory_bytes resident memory size in bytes.
# TYPE process_resident_memory_bytes gauge
process_resident_memory_bytes 5.9609088e+07
# HELP process_start_time_seconds Start time of the process since unix epoch in seconds.
# TYPE process_start_time_seconds gauge
process_start_time_seconds 1.57579509824e+09
# HELP process_virtual_memory_bytes Virtual memory size in bytes.
# TYPE process_virtual_memory_bytes gauge
process_virtual_memory_bytes 1.65691392e+08
# HELP process_virtual_memory_max_bytes Maximum amount of virtual memory available bytes.
# TYPE process_virtual_memory_max_bytes gauge
process_virtual_memory_max_bytes -1
# HELP prometheus_api_remote_read_queries The current number of remote read queries being executed or waiting.
# TYPE prometheus_api_remote_read_queries gauge
prometheus_api_remote_read_queries 0
# HELP prometheus_build_info A metric with a constant '1' value labeled by version, revision, branch, and goverment from which prometheus was built.
# TYPE prometheus_build_info gauge
prometheus_build_info{branch="HEAD",goversion="go1.13.4",revision="edeb7a44cbf745f1d8be4ea6f215e79e651bfe19",version="2.14.0" }. 1
# HELP prometheus_config_last_reload_success_timestamp_seconds Timestamp of the last successful configuration reload.
# TYPE prometheus_config_last_reload_success_timestamp_seconds gauge
prometheus_config_last_reload_success_timestamp_seconds 1.5757950994458635e+09
# HELP prometheus_config_last_reload_successful Whether the last configuration reload attempt was successful.
# TYPE prometheus_config_last_reload_successful gauge
prometheus_config_last_reload_successful 1
# HELP prometheus_engine_queries The current number of queries being executed or waiting.
# TYPE prometheus_engine_queries gauge
prometheus_engine_queries 0
# HELP prometheus_engine_queries_concurrent_max The max number of concurrent queries.
# TYPE prometheus_engine_queries_concurrent_max gauge
prometheus_engine_queries_concurrent_max 20
# HELP prometheus_engine_query_duration_seconds Query timings
# TYPE prometheus_engine_query_duration_seconds summary
prometheus_engine_query_duration_seconds{slice="inner_eval",quantile="0.5"} NaN
prometheus_engine_query_duration_seconds{slice="inner_eval",quantile="0.9"} NaN
prometheus_engine_query_duration_seconds{slice="inner_eval",quantile="0.99" } NaN
prometheus_engine_query_duration_seconds_sum{slice="inner_eval"} 9.1966e-05
prometheus_engine_query_duration_seconds_count{slice="inner_eval"} 5
prometheus_engine_query_duration_seconds{slice="prepare_time",quantile="0.5" } NaN
prometheus_engine_query_duration_seconds{slice="prepare_time",quantile="0.9" } NaN
prometheus_engine_query_duration_seconds{slice="prepare_time",quantile="0.99" } NaN
prometheus_engine_query_duration_seconds_sum{slice="prepare_time"} 0.00018078700000000002
prometheus_engine_query_duration_seconds_count{slice="prepare_time"} 5
prometheus_engine_query_duration_seconds{slice="queue_time",quantile="0.5" } NaN
prometheus_engine_query_duration_seconds{slice="queue_time",quantile="0.9" } NaN
prometheus_engine_query_duration_seconds{slice="queue_time",quantile="0.99" } NaN
prometheus_engine_query_duration_seconds_sum{slice="queue_time"} 2.2108e-05
prometheus_engine_query_duration_seconds_count{slice="queue_time"} 5
prometheus_engine_query_duration_seconds{slice="result_sort",quantile="0.5" } NaN
prometheus_engine_query_duration_seconds{slice="result_sort",quantile="0.9" } NaN
prometheus_engine_query_duration_seconds{slice="result_sort",quantile="0.99" } NaN
prometheus_engine_query_duration_seconds_sum{slice="result_sort"} 0
prometheus_engine_query_duration_seconds_count{slice="result_sort"} 0
# HELP prometheus_http_request_duration_seconds Histogram of latencies for HTTP requests.
# TYPE prometheus_http_request_duration_seconds histogram
prometheus_http_request_duration_seconds_bucket{handler="/",le="0.1"} 1
prometheus_http_request_duration_seconds_bucket{handler="/",le="0.2"} 1
prometheus_http_request_duration_seconds_bucket{handler="/",le="0.4"} 1
prometheus_http_request_duration_seconds_bucket{handler="/",le="1"} 1
prometheus_http_request_duration_seconds_bucket{handler="/",le="3"} 1
prometheus_http_request_duration_seconds_bucket{handler="/",le="8"} 1
prometheus_http_request_duration_seconds_bucket{handler="/",le="20"} 1
prometheus_http_request_duration_seconds_bucket{handler="/",le="60"} 1
prometheus_http_request_duration_seconds_bucket{handler="/",le="120"} 1
prometheus_http_request_duration_seconds_bucket{handler="/",le="+Inf"} 1
prometheus_http_request_duration_seconds_sum{handler="/"} 3.6641e-05
prometheus_http_request_duration_seconds_count{handler="/"} 1
prometheus_http_request_duration_seconds_bucket{handler="/api/v1/label/:name/values",le="0.1"}. 1
prometheus_http_request_duration_seconds_bucket{handler="/api/v1/label/:name/values",le="0.2"}. 1
prometheus_http_request_duration_seconds_bucket{handler="/api/v1/label/:name/values",le="0.4"}. 1
prometheus_http_request_duration_seconds_bucket{handler="/api/v1/label/:name/values",le="1" }. 1
prometheus_http_request_duration_seconds_bucket{handler="/api/v1/label/:name/values",le="3"}. 1
prometheus_http_request_duration_seconds_bucket{handler="/api/v1/label/:name/values",le="8"}. 1
prometheus_http_request_duration_seconds_bucket{handler="/api/v1/label/:name/values",le="20"}. 1
prometheus_http_request_duration_seconds_bucket{handler="/api/v1/label/:name/values",le="60"}. 1
prometheus_http_request_duration_seconds_bucket{handler="/api/v1/label/:name/values",le="120"}. 1
prometheus_http_request_duration_seconds_bucket{handler="/api/v1/label/:name/values",le="+Inf"}. 1
prometheus_http_request_duration_seconds_sum{handler="/api/v1/label/:name/values"}. 0.001905385
prometheus_http_request_duration_seconds_count{handler="/api/v1/label/:name/values"}. 1
prometheus_http_request_duration_seconds_bucket{handler="/api/v1/query",le="0.1"} 5
prometheus_http_request_duration_seconds_bucket{handler="/api/v1/query",le="0.2"} 5
prometheus_http_request_duration_seconds_bucket{handler="/api/v1/query",le="0.4"} 5
prometheus_http_request_duration_seconds_bucket{handler="/api/v1/query",le="1" }. 5
prometheus_http_request_duration_seconds_bucket{handler="/api/v1/query",le="3"}. 5
prometheus_http_request_duration_seconds_bucket{handler="/api/v1/query",le="8"}. 5
prometheus_http_request_duration_seconds_bucket{handler="/api/v1/query",le="20"} 5
prometheus_http_request_duration_seconds_bucket{handler="/api/v1/query",le="60"}. 5
prometheus_http_request_duration_seconds_bucket{handler="/api/v1/query",le="120"}. 5
prometheus_http_request_duration_seconds_bucket{handler="/api/v1/query",le="+Inf"} 5
prometheus_http_request_duration_seconds_sum{handler="/api/v1/query"} 0.0043781110000000005
prometheus_http_request_duration_seconds_count{handler="/api/v1/query"} 5
prometheus_http_request_duration_seconds_bucket{handler="/graph",le="0.1"} 1
prometheus_http_request_duration_seconds_bucket{handler="/graph",le="0.2"} 1
prometheus_http_request_duration_seconds_bucket{handler="/graph",le="0.4"} 1
prometheus_http_request_duration_seconds_bucket{handler="/graph",le="1" } 1
prometheus_http_request_duration_seconds_bucket{handler="/graph",le="3"} 1
prometheus_http_request_duration_seconds_bucket{handler="/graph",le="8"} 1
prometheus_http_request_duration_seconds_bucket{handler="/graph",le="20"} 1
prometheus_http_request_duration_seconds_bucket{handler="/graph",le="60"} 1
prometheus_http_request_duration_seconds_bucket{handler="/graph",le="120"} 1
prometheus_http_request_duration_seconds_bucket{handler="/graph",le="+Inf"} 1
prometheus_http_request_duration_seconds_sum{handler="/graph"} 0.001959785
prometheus_http_request_duration_seconds_count{handler="/graph"} 1
prometheus_http_request_duration_seconds_bucket{handler="/metrics",le="0.1"} 142
prometheus_http_request_duration_seconds_bucket{handler="/metrics",le="0.2"} 142
prometheus_http_request_duration_seconds_bucket{handler="/metrics",le="0.4"} 142
prometheus_http_request_duration_seconds_bucket{handler="/metrics",le="1" } 142
prometheus_http_request_duration_seconds_bucket{handler="/metrics",le="3"} 142
prometheus_http_request_duration_seconds_bucket{handler="/metrics",le="8"} 142
prometheus_http_request_duration_seconds_bucket{handler="/metrics",le="20"} 142
prometheus_http_request_duration_seconds_bucket{handler="/metrics",le="60"} 142
prometheus_http_request_duration_seconds_bucket{handler="/metrics",le="120"} 142
prometheus_http_request_duration_seconds_bucket{handler="/metrics",le="+Inf"} 142
prometheus_http_request_duration_seconds_sum{handler="/metrics"} 0.5661348470000002
prometheus_http_request_duration_seconds_count{handler="/metrics"} 142
prometheus_http_request_duration_seconds_bucket{handler="/static/*filepath",le="0.1"} 23
prometheus_http_request_duration_seconds_bucket{handler="/static/*filepath",le="0.2"} 25
prometheus_http_request_duration_seconds_bucket{handler="/static/*filepath",le="0.4"} 26
prometheus_http_request_duration_seconds_bucket{handler="/static/*filepath",le="1"}. 26
prometheus_http_request_duration_seconds_bucket{handler="/static/*filepath",le="3"}. 26
prometheus_http_request_duration_seconds_bucket{handler="/static/*filepath",le="8"}. 26
prometheus_http_request_duration_seconds_bucket{handler="/static/*filepath",le="20"}. 26
prometheus_http_request_duration_seconds_bucket{handler="/static/*filepath",le="60"}. 26
prometheus_http_request_duration_seconds_bucket{handler="/static/*filepath",le="120"}. 26
prometheus_http_request_duration_seconds_bucket{handler="/static/*filepath",le="+Inf"} 26
prometheus_http_request_duration_seconds_sum{handler="/static/*filepath"} 0.6096292270000001
prometheus_http_request_duration_seconds_count{handler="/static/*filepath"} 26
prometheus_http_request_duration_seconds_bucket{handler="/targets",le="0.1"} 1
prometheus_http_request_duration_seconds_bucket{handler="/targets",le="0.2"} 1
prometheus_http_request_duration_seconds_bucket{handler="/targets",le="0.4"} 1
prometheus_http_request_duration_seconds_bucket{handler="/targets",le="1"} 1
prometheus_http_request_duration_seconds_bucket{handler="/targets",le="3"} 1
prometheus_http_request_duration_seconds_bucket{handler="/targets",le="8"} 1
prometheus_http_request_duration_seconds_bucket{handler="/targets",le="20"} 1
prometheus_http_request_duration_seconds_bucket{handler="/targets",le="60"} 1
prometheus_http_request_duration_seconds_bucket{handler="/targets",le="120"} 1
prometheus_http_request_duration_seconds_bucket{handler="/targets",le="+Inf"} 1
prometheus_http_request_duration_seconds_sum{handler="/targets"} 0.001879882
prometheus_http_request_duration_seconds_count{handler="/targets"} 1
# HELP prometheus_http_requests_total Counter of HTTP requests.
# TYPE prometheus_http_requests_total counter
prometheus_http_requests_total{code="200",handler="/api/v1/label/:name/values"}. 1
prometheus_http_requests_total{code="200",handler="/api/v1/query"}. 5
prometheus_http_requests_total{code="200",handler="/graph"} 1
prometheus_http_requests_total{code="200",handler="/metrics"}. 142
prometheus_http_requests_total{code="200",handler="/static/*filepath"}. 26
prometheus_http_requests_total{code="200",handler="/targets"} 1
prometheus_http_requests_total{code="302",handler="/"}. 1
# HELP prometheus_http_response_size_bytes Histogram of response size for HTTP requests.
# TYPE prometheus_http_response_size_bytes histogram
prometheus_http_response_size_bytes_bucket{handler="/",le="100"} 1
prometheus_http_response_size_bytes_bucket{handler="/",le="1000"} 1
prometheus_http_response_size_bytes_bucket{handler="/",le="10000"} 1
prometheus_http_response_size_bytes_bucket{handler="/",le="100000"} 1
prometheus_http_response_size_bytes_bucket{handler="/",le="1e+06"} 1
prometheus_http_response_size_bytes_bucket{handler="/",le="1e+07"} 1
prometheus_http_response_size_bytes_bucket{handler="/",le="1e+08"} 1
prometheus_http_response_size_bytes_bucket{handler="/",le="1e+09"} 1
prometheus_http_response_size_bytes_bucket{handler="/",le="+Inf"} 1
prometheus_http_response_size_bytes_sum{handler="/"} 29
prometheus_http_response_size_bytes_count{handler="/"} 1
prometheus_http_response_size_bytes_bucket{handler="/api/v1/label/:name/values",le="100"}. 0
prometheus_http_response_size_bytes_bucket{handler="/api/v1/label/:name/values",le="1000"}. 0
prometheus_http_response_size_bytes_bucket{handler="/api/v1/label/:name/values",le="10000"}. 1
prometheus_http_response_size_bytes_bucket{handler="/api/v1/label/:name/values",le="100000"}. 1
prometheus_http_response_size_bytes_bucket{handler="/api/v1/label/:name/values",le="1e+06"}. 1
prometheus_http_response_size_bytes_bucket{handler="/api/v1/label/:name/values",le="1e+07"}. 1
prometheus_http_response_size_bytes_bucket{handler="/api/v1/label/:name/values",le="1e+08"}. 1
prometheus_http_response_size_bytes_bucket{handler="/api/v1/label/:name/values",le="1e+09"}. 1
prometheus_http_response_size_bytes_bucket{handler="/api/v1/label/:name/values",le="+Inf"}. 1
prometheus_http_response_size_bytes_sum{handler="/api/v1/label/:name/values"}. 1397
prometheus_http_response_size_bytes_count{handler="/api/v1/label/:name/values"}. 1
prometheus_http_response_size_bytes_bucket{handler="/api/v1/query",le="100"}. 2
prometheus_http_response_size_bytes_bucket{handler="/api/v1/query",le="1000"} 5
prometheus_http_response_size_bytes_bucket{handler="/api/v1/query",le="10000"}. 5
prometheus_http_response_size_bytes_bucket{handler="/api/v1/query",le="100000"}. 5
prometheus_http_response_size_bytes_bucket{handler="/api/v1/query",le="1e+06" }. 5
prometheus_http_response_size_bytes_bucket{handler="/api/v1/query",le="1e+07"} 5
prometheus_http_response_size_bytes_bucket{handler="/api/v1/query",le="1e+08" } 5
prometheus_http_response_size_bytes_bucket{handler="/api/v1/query",le="1e+09" } 5
prometheus_http_response_size_bytes_bucket{handler="/api/v1/query",le="+Inf"} 5
prometheus_http_response_size_bytes_sum{handler="/api/v1/query"} 700
prometheus_http_response_size_bytes_count{handler="/api/v1/query"} 5
prometheus_http_response_size_bytes_bucket{handler="/graph",le="100"} 0
prometheus_http_response_size_bytes_bucket{handler="/graph",le="1000"} 0
prometheus_http_response_size_bytes_bucket{handler="/graph",le="10000"} 1
prometheus_http_response_size_bytes_bucket{handler="/graph",le="100000"} 1
prometheus_http_response_size_bytes_bucket{handler="/graph",le="1e+06" } 1
prometheus_http_response_size_bytes_bucket{handler="/graph",le="1e+07"} 1
prometheus_http_response_size_bytes_bucket{handler="/graph",le="1e+08" } 1
prometheus_http_response_size_bytes_bucket{handler="/graph",le="1e+09"} 1
prometheus_http_response_size_bytes_bucket{handler="/graph",le="+Inf"} 1
prometheus_http_response_size_bytes_sum{handler="/graph"} 5967
prometheus_http_response_size_bytes_count{handler="/graph"} 1
prometheus_http_response_size_bytes_bucket{handler="/metrics",le="100"} 0
prometheus_http_response_size_bytes_bucket{handler="/metrics",le="1000"} 0
prometheus_http_response_size_bytes_bucket{handler="/metrics",le="10000"} 142
prometheus_http_response_size_bytes_bucket{handler="/metrics",le="100000"} 142
prometheus_http_response_size_bytes_bucket{handler="/metrics",le="1e+06"} 142
prometheus_http_response_size_bytes_bucket{handler="/metrics",le="1e+07"} 142
prometheus_http_response_size_bytes_bucket{handler="/metrics",le="1e+08"} 142
prometheus_http_response_size_bytes_bucket{handler="/metrics",le="1e+09"} 142
prometheus_http_response_size_bytes_bucket{handler="/metrics",le="+Inf"} 142
prometheus_http_response_size_bytes_sum{handler="/metrics"} 971753
prometheus_http_response_size_bytes_count{handler="/metrics"} 142
prometheus_http_response_size_bytes_bucket{handler="/static/*filepath",le="100"}. 0
prometheus_http_response_size_bytes_bucket{handler="/static/*filepath",le="1000"} 3
prometheus_http_response_size_bytes_bucket{handler="/static/*filepath",le="10000"}. 10
prometheus_http_response_size_bytes_bucket{handler="/static/*filepath",le="100000"}. 23
prometheus_http_response_size_bytes_bucket{handler="/static/*filepath",le="1e+06"} 26
prometheus_http_response_size_bytes_bucket{handler="/static/*filepath",le="1e+07"} 26
prometheus_http_response_size_bytes_bucket{handler="/static/*filepath",le="1e+08"} 26
prometheus_http_response_size_bytes_bucket{handler="/static/*filepath",le="1e+09"} 26
prometheus_http_response_size_bytes_bucket{handler="/static/*filepath",le="+Inf"} 26
prometheus_http_response_size_bytes_sum{handler="/static/*filepath"} 993190
prometheus_http_response_size_bytes_count{handler="/static/*filepath"} 26
prometheus_http_response_size_bytes_bucket{handler="/targets",le="100"} 0
prometheus_http_response_size_bytes_bucket{handler="/targets",le="1000"} 0
prometheus_http_response_size_bytes_bucket{handler="/targets",le="10000"} 1
prometheus_http_response_size_bytes_bucket{handler="/targets",le="100000"} 1
prometheus_http_response_size_bytes_bucket{handler="/targets",le="1e+06"} 1
prometheus_http_response_size_bytes_bucket{handler="/targets",le="1e+07"} 1
prometheus_http_response_size_bytes_bucket{handler="/targets",le="1e+08"} 1
prometheus_http_response_size_bytes_bucket{handler="/targets",le="1e+09"} 1
prometheus_http_response_size_bytes_bucket{handler="/targets",le="+Inf"} 1
prometheus_http_response_size_bytes_sum{handler="/targets"} 5850
prometheus_http_response_size_bytes_count{handler="/targets"} 1
# HELP prometheus_notifications_alertmanagers_discovered The number of alertmanagers discovered and active.
# TYPE prometheus_notifications_alertmanagers_discovered gauge
prometheus_notifications_alertmanagers_discovered 0
# HELP prometheus_notifications_dropped_total Total number of alerts dropped due when sent to Alertmanager.
# TYPE prometheus_notifications_dropped_total counter
prometheus_notifications_dropped_total 0
# HELP prometheus_notifications_queue_capacity The capacity of the alert queue.
# TYPE prometheus_notifications_queue_capacity gauge
prometheus_notifications_queue_capacity 10000
# HELP prometheus_notifications_queue_length The number of warnings in the queue.
# TYPE prometheus_notifications_queue_length gauge
prometheus_notifications_queue_length 0
# HELP prometheus_remote_storage_highest_timestamp_in_seconds Highest timestamp that has come into the remote storage via the Appender interface, in seconds since epoch.
# TYPE prometheus_remote_storage_highest_timestamp_in_seconds gauge
prometheus_remote_storage_highest_timestamp_in_seconds 1.57579722e+09
# HELP prometheus_remote_storage_samples_in_total Samples in remote storage, compare to samples out for queue managers.
# TYPE prometheus_remote_storage_samples_in_total counter
prometheus_remote_storage_samples_in_total 64123
# HELP prometheus_remote_storage_string_interner_zero_reference_releases_total The number of times release has been called for strings that are not interned.
# TYPE prometheus_remote_storage_string_interner_zero_reference_releases_total counter
prometheus_remote_storage_string_interner_zero_reference_releases_total 0
# HELP prometheus_rule_evaluation_duration_seconds The duration for a rule to execute.
# TYPE prometheus_rule_evaluation_duration_seconds summary
prometheus_rule_evaluation_duration_seconds{quantile="0.5"} NaN
prometheus_rule_evaluation_duration_seconds{quantile="0.9"} NaN
prometheus_rule_evaluation_duration_seconds{quantile="0.99"} NaN
prometheus_rule_evaluation_duration_seconds_sum 0
prometheus_rule_evaluation_duration_seconds_count 0
# HELP prometheus_rule_evaluation_failures_total The total number of rule evaluation failures.
# TYPE prometheus_rule_evaluation_failures_total counter
prometheus_rule_evaluation_failures_total 0
# HELP prometheus_rule_evaluations_total The total number of rule.
# TYPE prometheus_rule_evaluations_total counter
prometheus_rule_evaluations_total 0
# HELP prometheus_rule_group_duration_seconds The duration of rule group.
# TYPE prometheus_rule_group_duration_seconds summary
prometheus_rule_group_duration_seconds{quantile="0.01"} NaN
prometheus_rule_group_duration_seconds{quantile="0.05"} NaN
prometheus_rule_group_duration_seconds{quantile="0.5"} NaN
prometheus_rule_group_duration_seconds{quantile="0.9"} NaN
prometheus_rule_group_duration_seconds{quantile="0.99"} NaN
prometheus_rule_group_duration_seconds_sum 0
prometheus_rule_group_duration_seconds_count 0
# HELP prometheus_rule_group_iterations_missed_total The total number of rule group missed due to slow rule group evaluation.
# TYPE prometheus_rule_group_iterations_missed_total counter
prometheus_rule_group_iterations_missed_total 1
# HELP prometheus_rule_group_iterations_total The total number of scheduled rule group evaluations, whether executed or missed.
# TYPE prometheus_rule_group_iterations_total counter
prometheus_rule_group_iterations_total 0
# HELP prometheus_sd_consul_rpc_duration_seconds The duration of a Consul RPC call in seconds.
# TYPE prometheus_sd_consul_rpc_duration_seconds summary
prometheus_sd_consul_rpc_duration_seconds{call="service",endpoint="catalog",quantile="0.5" } NaN
prometheus_sd_consul_rpc_duration_seconds{call="service",endpoint="catalog",quantile="0.9" } NaN
prometheus_sd_consul_rpc_duration_seconds{call="service",endpoint="catalog",quantile="0.99"} NaN
prometheus_sd_consul_rpc_duration_seconds_sum{call="service",endpoint="catalog"} 0
prometheus_sd_consul_rpc_duration_seconds_count{call="service",endpoint="catalog"} 0
prometheus_sd_consul_rpc_duration_seconds{call="services",endpoint="catalog",quantile="0.5" } NaN
prometheus_sd_consul_rpc_duration_seconds{call="services",endpoint="catalog",quantile="0.9" } NaN
prometheus_sd_consul_rpc_duration_seconds{call="services",endpoint="catalog",quantile="0.99"} NaN
prometheus_sd_consul_rpc_duration_seconds_sum{call="services",endpoint="catalog"} 0
prometheus_sd_consul_rpc_duration_seconds_count{call="services",endpoint="catalog"} 0
# HELP prometheus_sd_consul_rpc_failures_total The number of Consul RPC call failures.
# TYPE prometheus_sd_consul_rpc_failures_total counter
prometheus_sd_consul_rpc_failures_total 0
# HELP prometheus_sd_discoveredtargets Current number of discovered.
# TYPE prometheus_sd_discovered_targets gauge
prometheus_sd_discovered_targets{config="00592cee302b53b01a6cbb27b6147722",name="notify"}. 0
prometheus_sd_discovered_targets{config="prometheus",name="scrape"} 1
# HELP prometheus_sd_dns_lookup_failures_total The number of DNS-SD lookup failures.
# TYPE prometheus_sd_dns_lookup_failures_total counter
prometheus_sd_dns_lookup_failures_total 0
# HELP prometheus_sd_dns_lookups_total The number of DNS-SD lookups.
# TYPE prometheus_sd_dns_lookups_total counter
prometheus_sd_dns_lookups_total 0
# HELP prometheus_sd_failed_configs Current number of service configurations that failed to load.
# TYPE prometheus_sd_failed_configs gauge
prometheus_sd_failed_configs{name="notify"} 0
prometheus_sd_failed_configs{name="scrape"} 0
# HELP prometheus_sd_file_read_errors_total The number of File-SD read.
# TYPE prometheus_sd_file_read_errors_total counter
prometheus_sd_file_read_errors_total 0
# HELP prometheus_sd_file_scan_duration_seconds The duration of the File-SD scan in seconds.
# TYPE prometheus_sd_file_scan_duration_seconds summary
prometheus_sd_file_scan_duration_seconds{quantile="0.5"} NaN
prometheus_sd_file_scan_duration_seconds{quantile="0.9"} NaN
prometheus_sd_file_scan_duration_seconds{quantile="0.99"} NaN
prometheus_sd_file_scan_duration_seconds_sum 0
prometheus_sd_file_scan_duration_seconds_count 0
# HELP prometheus_sd_kubernetes_cache_last_resource_version Last resource version from the Kubernetes API.
# TYPE prometheus_sd_kubernetes_cache_last_resource_version gauge
prometheus_sd_kubernetes_cache_last_resource_version 0
# HELP prometheus_sd_kubernetes_cache_list_duration_seconds Duration of a Kubernetes API call in seconds.
# TYPE prometheus_sd_kubernetes_cache_list_duration_seconds summary
prometheus_sd_kubernetes_cache_list_duration_seconds_sum 0
prometheus_sd_kubernetes_cache_list_duration_seconds_count 0
# HELP prometheus_sd_kubernetes_cache_list_items Count of items in a list from the Kubernetes API.
# TYPE prometheus_sd_kubernetes_cache_list_items summary
prometheus_sd_kubernetes_cache_list_items_sum 0
prometheus_sd_kubernetes_cache_list_items_count 0
# HELP prometheus_sd_kubernetes_cache_list_total total number of list operations.
# TYPE prometheus_sd_kubernetes_cache_list_total counter
prometheus_sd_kubernetes_cache_list_total 0
# HELP prometheus_sd_kubernetes_cache_short_watches_total total number of short watch operations.
# TYPE prometheus_sd_kubernetes_cache_short_watches_total counter
prometheus_sd_kubernetes_cache_short_watches_total 0
# HELP prometheus_sd_kubernetes_cache_watch_duration_seconds Duration of watches on the Kubernetes API.
# TYPE prometheus_sd_kubernetes_cache_watch_duration_seconds summary
prometheus_sd_kubernetes_cache_watch_duration_seconds_sum 0
prometheus_sd_kubernetes_cache_watch_duration_seconds_count 0
# HELP prometheus_sd_kubernetes_cache_watch_events Number of items in watches on the Kubernetes API.
# TYPE prometheus_sd_kubernetes_cache_watch_events summary
prometheus_sd_kubernetes_cache_watch_events_sum 0
prometheus_sd_kubernetes_cache_watch_events_count 0
# HELP prometheus_sd_kubernetes_cache_watches_total total number of watch operations.
# TYPE prometheus_sd_kubernetes_cache_watches_total counter
prometheus_sd_kubernetes_cache_watches_total 0
# HELP prometheus_sd_kubernetes_events_total The number of Kubernetes events handled.
# TYPE prometheus_sd_kubernetes_events_total counter
prometheus_sd_kubernetes_events_total{event="add",role="endpoints"} 0
prometheus_sd_kubernetes_events_total{event="add",role="ingress"} 0
prometheus_sd_kubernetes_events_total{event="add",role="node"} 0
prometheus_sd_kubernetes_events_total{event="add",role="pod"} 0
prometheus_sd_kubernetes_events_total{event="add",role="service"} 0
prometheus_sd_kubernetes_events_total{event="delete",role="endpoints"} 0
prometheus_sd_kubernetes_events_total{event="delete",role="ingress"} 0
prometheus_sd_kubernetes_events_total{event="delete",role="node"} 0
prometheus_sd_kubernetes_events_total{event="delete",role="pod"} 0
prometheus_sd_kubernetes_events_total{event="delete",role="service"} 0
prometheus_sd_kubernetes_events_total{event="update",role="endpoints"} 0
prometheus_sd_kubernetes_events_total{event="update",role="ingress"} 0
prometheus_sd_kubernetes_events_total{event="update",role="node"} 0
prometheus_sd_kubernetes_events_total{event="update",role="pod"} 0
prometheus_sd_kubernetes_events_total{event="update",role="service"} 0
# HELP prometheus_sd_received_updates_total Total number of update events received from the SD.
# TYPE prometheus_sd_received_updates_total counter
prometheus_sd_received_updates_total{name="notify"} 2
prometheus_sd_received_updates_total{name="scrape"} 2
# HELP prometheus_sd_updates_total Total number of update events sent to the SD consumers.
# TYPE prometheus_sd_updates_total counter
prometheus_sd_updates_total{name="notify"} 1
prometheus_sd_updates_total{name="scrape"} 1
# HELP prometheus_target_interval_length_seconds Actual between scrapes.
# TYPE prometheus_target_interval_length_seconds summary
prometheus_target_interval_length_seconds{interval="15s",quantile="0.01"} 14.999937952
prometheus_target_interval_length_seconds{interval="15s",quantile="0.05"} 14.999957145
prometheus_target_interval_length_seconds{interval="15s",quantile="0.5" } 15.000026261
prometheus_target_interval_length_seconds{interval="15s",quantile="0.9" } 15.000070811
prometheus_target_interval_length_seconds{interval="15s",quantile="0.99"} 15.000122811
prometheus_target_interval_length_seconds_sum{interval="15s"} 2115.003722788
prometheus_target_interval_length_seconds_count{interval="15s"} 141
# HELP prometheus_target_scrape_pool_reloads_failed_total total number of failed scrape loop reloads.
# TYPE prometheus_target_scrape_pool_reloads_failed_total counter
prometheus_target_scrape_pool_reloads_failed_total 0
# HELP prometheus_target_scrape_pool_reloads_total total number of scrape loop reloads.
# TYPE prometheus_target_scrape_pool_reloads_total counter
prometheus_target_scrape_pool_reloads_total 0
# HELP prometheus_target_scrape_pool_sync_total Total number of syncs that were executed on a scrape pool.
# TYPE prometheus_target_scrape_pool_sync_total counter
prometheus_target_scrape_pool_sync_total{scrape_job="prometheus"}. 1
# HELP prometheus_target_scrape_pools_failed_total total number of scrape pool creations that failed.
# TYPE prometheus_target_scrape_pools_failed_total counter
prometheus_target_scrape_pools_failed_total 0
# HELP prometheus_target_scrape_pools_total total number of scrape pool creation attempts.
# TYPE prometheus_target_scrape_pools_total counter
prometheus_target_scrape_pools_total 1
# HELP prometheus_target_scrapes_cache_flush_forced_total How many times a scrape cache was flushed due to getting big while scrapes are failing.
# TYPE prometheus_target_scrapes_cache_flush_forced_total counter
prometheus_target_scrapes_cache_flush_forced_total 0
# HELP prometheus_target_scrapes_exceeded_sample_limit_total Total number of scrapes that hit the sample limit and were rejected.
# TYPE prometheus_target_scrapes_exceeded_sample_limit_total counter
prometheus_target_scrapes_exceeded_sample_limit_total 0
# HELP prometheus_target_scrapes_sample_duplicate_timestamp_total Total number of samples rejected due to duplicate timestamps but different values
# TYPE prometheus_target_scrapes_sample_duplicate_timestamp_total counter
prometheus_target_scrapes_sample_duplicate_timestamp_total 0
# HELP prometheus_target_scrapes_sample_out_of_bounds_total Total number of samples rejected due to timetamp falling outside of the time bounds
# TYPE prometheus_target_scrapes_sample_out_of_bounds_total counter
prometheus_target_scrapes_sample_out_of_bounds_total 0
# HELP prometheus_target_scrapes_sample_out_of_order_total Total number of samples rejected due to not being out of the expected order
# TYPE prometheus_target_scrapes_sample_out_of_order_total counter
prometheus_target_scrapes_sample_out_of_order_total 0
# HELP prometheus_target_sync_length_seconds Actual interval to sync the scrape pool.
# TYPE prometheus_target_sync_length_seconds summary
prometheus_target_sync_length_seconds{scrape_job="prometheus",quantile="0.01" } NaN
prometheus_target_sync_length_seconds{scrape_job="prometheus",quantile="0.05" } NaN
prometheus_target_sync_length_seconds{scrape_job="prometheus",quantile="0.5" } NaN
prometheus_target_sync_length_seconds{scrape_job="prometheus",quantile="0.9" } NaN
prometheus_target_sync_length_seconds{scrape_job="prometheus",quantile="0.99"} NaN
prometheus_target_sync_length_seconds_sum{scrape_job="prometheus"} 0.000126029
prometheus_target_sync_length_seconds_count{scrape_job="prometheus"} 1
# HELP prometheus_template_text_expansion_failures_total The total number of template text expansion failures.
# TYPE prometheus_template_text_expansion_failures_total counter
prometheus_template_text_expansion_failures_total 0
# HELP prometheus_template_text_expansions_total The total number of template text expansions.
# TYPE prometheus_template_text_expansions_total counter
prometheus_template_text_expansions_total 0
# HELP prometheus_treecache_watcher_goroutines The current number of watcher goroutines.
# TYPE prometheus_treecache_watcher_goroutines gauge
prometheus_treecache_watcher_goroutines 0
# HELP prometheus_treecache_zookeeper_failures_total The total number of ZooKeeper failures.
# TYPE prometheus_treecache_zookeeper_failures_total counter
prometheus_treecache_zookeeper_failures_total 0
# HELP prometheus_tsdb_blocks_loaded Number of currently loaded data blocks
# TYPE prometheus_tsdb_blocks_loaded gauge
prometheus_tsdb_blocks_loaded 0
# HELP prometheus_tsdb_checkpoint_creations_failed_total total number of checkpoint creations that failed.
# TYPE prometheus_tsdb_checkpoint_creations_failed_total counter
prometheus_tsdb_checkpoint_creations_failed_total 0
# HELP prometheus_tsdb_checkpoint_creations_total total number of checkpoint creations attempted.
# TYPE prometheus_tsdb_checkpoint_creations_total counter
prometheus_tsdb_checkpoint_creations_total 0
# HELP prometheus_tsdb_checkpoint_deletions_failed_total total number of checkpoint deletions that failed.
# TYPE prometheus_tsdb_checkpoint_deletions_failed_total counter
prometheus_tsdb_checkpoint_deletions_failed_total 0
# HELP prometheus_tsdb_checkpoint_deletions_total Total number of checkpoint deletions attempted.
# TYPE prometheus_tsdb_checkpoint_deletions_total counter
prometheus_tsdb_checkpoint_deletions_total 0
# HELP prometheus_tsdb_compaction_chunk_range_seconds Final time range of chunks on their first compaction
# TYPE prometheus_tsdb_compaction_chunk_range_seconds histogram
prometheus_tsdb_compaction_chunk_range_seconds_bucket{le="100"} 0
prometheus_tsdb_compaction_chunk_range_seconds_bucket{le="400"} 0
prometheus_tsdb_compaction_chunk_range_seconds_bucket{le="1600"} 0
prometheus_tsdb_compaction_chunk_range_seconds_bucket{le="6400"} 0
prometheus_tsdb_compaction_chunk_range_seconds_bucket{le="25600"} 0
prometheus_tsdb_compaction_chunk_range_seconds_bucket{le="102400"} 0
prometheus_tsdb_compaction_chunk_range_seconds_bucket{le="409600"} 0
prometheus_tsdb_compaction_chunk_range_seconds_bucket{le="1.6384e+06"} 0
prometheus_tsdb_compaction_chunk_range_seconds_bucket{le="6.5536e+06"} 0
prometheus_tsdb_compaction_chunk_range_seconds_bucket{le="2.62144e+07"} 0
prometheus_tsdb_compaction_chunk_range_seconds_bucket{le="+Inf"} 0
prometheus_tsdb_compaction_chunk_range_seconds_sum 0
prometheus_tsdb_compaction_chunk_range_seconds_count 0
# HELP prometheus_tsdb_compaction_chunk_samples Final number of samples on their first compaction
# TYPE prometheus_tsdb_compaction_chunk_samples histogram
prometheus_tsdb_compaction_chunk_samples_bucket{le="4"} 0
prometheus_tsdb_compaction_chunk_samples_bucket{le="6"} 0
prometheus_tsdb_compaction_chunk_samples_bucket{le="9"} 0
prometheus_tsdb_compaction_chunk_samples_bucket{le="13.5"} 0
prometheus_tsdb_compaction_chunk_samples_bucket{le="20.25"} 0
prometheus_tsdb_compaction_chunk_samples_bucket{le="30.375"} 0
prometheus_tsdb_compaction_chunk_samples_bucket{le="45.5625"} 0
prometheus_tsdb_compaction_chunk_samples_bucket{le="68.34375"} 0
prometheus_tsdb_compaction_chunk_samples_bucket{le="102.515625"} 0
prometheus_tsdb_compaction_chunk_samples_bucket{le="153.7734375"} 0
prometheus_tsdb_compaction_chunk_samples_bucket{le="230.66015625"} 0
prometheus_tsdb_compaction_chunk_samples_bucket{le="345.990234375"} 0
prometheus_tsdb_compaction_chunk_samples_bucket{le="+Inf"} 0
prometheus_tsdb_compaction_chunk_samples_sum 0
prometheus_tsdb_compaction_chunk_samples_count 0
# HELP prometheus_tsdb_compaction_chunk_size_bytes Final size of chunks on their first compaction
# TYPE prometheus_tsdb_compaction_chunk_size_bytes histogram
prometheus_tsdb_compaction_chunk_size_bytes_bucket{le="32"} 0
prometheus_tsdb_compaction_chunk_size_bytes_bucket{le="48"} 0
prometheus_tsdb_compaction_chunk_size_bytes_bucket{le="72"} 0
prometheus_tsdb_compaction_chunk_size_bytes_bucket{le="108"} 0
prometheus_tsdb_compaction_chunk_size_bytes_bucket{le="162"} 0
prometheus_tsdb_compaction_chunk_size_bytes_bucket{le="243"} 0
prometheus_tsdb_compaction_chunk_size_bytes_bucket{le="364.5"} 0
prometheus_tsdb_compaction_chunk_size_bytes_bucket{le="546.75"} 0
prometheus_tsdb_compaction_chunk_size_bytes_bucket{le="820.125"}. 0
prometheus_tsdb_compaction_chunk_size_bytes_bucket{le="1230.1875"} 0
prometheus_tsdb_compaction_chunk_size_bytes_bucket{le="1845.28125"} 0
prometheus_tsdb_compaction_chunk_size_bytes_bucket{le="2767.921875"} 0
prometheus_tsdb_compaction_chunk_size_bytes_bucket{le="+Inf"} 0
prometheus_tsdb_compaction_chunk_size_bytes_sum 0
prometheus_tsdb_compaction_chunk_size_bytes_count 0
# HELP prometheus_tsdb_compaction_duration_seconds Duration of compaction runs
# TYPE prometheus_tsdb_compaction_duration_seconds histogram
prometheus_tsdb_compaction_duration_seconds_bucket{le="1"} 0
prometheus_tsdb_compaction_duration_seconds_bucket{le="2"} 0
prometheus_tsdb_compaction_duration_seconds_bucket{le="4"} 0
prometheus_tsdb_compaction_duration_seconds_bucket{le="8"} 0
prometheus_tsdb_compaction_duration_seconds_bucket{le="16"} 0
prometheus_tsdb_compaction_duration_seconds_bucket{le="32"} 0
prometheus_tsdb_compaction_duration_seconds_bucket{le="64"} 0
prometheus_tsdb_compaction_duration_seconds_bucket{le="128"} 0
prometheus_tsdb_compaction_duration_seconds_bucket{le="256"} 0
prometheus_tsdb_compaction_duration_seconds_bucket{le="512"} 0
prometheus_tsdb_compaction_duration_seconds_bucket{le="+Inf"} 0
prometheus_tsdb_compaction_duration_seconds_sum 0
prometheus_tsdb_compaction_duration_seconds_count 0
# HELP prometheus_tsdb_compaction_populating_block Set to 1 when a block is currently being written to the disk.
# TYPE prometheus_tsdb_compaction_populating_block gauge
prometheus_tsdb_compaction_populating_block 0
# HELP prometheus_tsdb_compactions_failed_total total number of compactions that failed for the partition.
# TYPE prometheus_tsdb_compactions_failed_total counter
prometheus_tsdb_compactions_failed_total 0
# HELP prometheus_tsdb_compactions_total Total number of compactions that were executed for the partition.
# TYPE prometheus_tsdb_compactions_total counter
prometheus_tsdb_compactions_total 0
# HELP prometheus_tsdb_compactions_triggered_total total number of triggered compactions for the partition.
# TYPE prometheus_tsdb_compactions_triggered_total counter
prometheus_tsdb_compactions_triggered_total 35
# HELP prometheus_tsdb_head_active_appenders Number of currently active appender transactions
# TYPE prometheus_tsdb_head_active_appenders gauge
prometheus_tsdb_head_active_appenders 0
# HELP prometheus_tsdb_head_chunks Total number of chunks in the head block.
# TYPE prometheus_tsdb_head_chunks gauge
prometheus_tsdb_head_chunks 838
# HELP prometheus_tsdb_head_chunks_created_total total number of chunks created in the head
# TYPE prometheus_tsdb_head_chunks_created_total counter
prometheus_tsdb_head_chunks_created_total 838
# HELP prometheus_tsdb_head_chunks_removed_total Total number of chunks removed in the head
# TYPE prometheus_tsdb_head_chunks_removed_total counter
prometheus_tsdb_head_chunks_removed_total 0
# HELP prometheus_tsdb_head_gc_duration_seconds Runtime of garbage collection in the head block.
# TYPE prometheus_tsdb_head_gc_duration_seconds summary
prometheus_tsdb_head_gc_duration_seconds_sum 0
prometheus_tsdb_head_gc_duration_seconds_count 0
# HELP prometheus_tsdb_head_max_time Maximum timestamp of the head block. The unit is decided by the library consumer.
# TYPE prometheus_tsdb_head_max_time gauge
prometheus_tsdb_head_max_time 1.575797220433e+12
# HELP prometheus_tsdb_head_max_time_seconds Maximum timestamp of the head block.
# TYPE prometheus_tsdb_head_max_time_seconds gauge
prometheus_tsdb_head_max_time_seconds 1.575797220433e+09
# HELP prometheus_tsdb_head_min_time Minimum time bound of the head block. The unit is decided by the library consumer.
# TYPE prometheus_tsdb_head_min_time gauge
prometheus_tsdb_head_min_time 1.575795105433e+12
# HELP prometheus_tsdb_head_min_time_seconds Minimum time bound of the head block.
# TYPE prometheus_tsdb_head_min_time_seconds gauge
prometheus_tsdb_head_min_time_seconds 1.575795105433e+09
# HELP prometheus_tsdb_head_samples_appended_total total number of appended samples.
# TYPE prometheus_tsdb_head_samples_appended_total counter
prometheus_tsdb_head_samples_appended_total 64123
# HELP prometheus_tsdb_head_series Total number of series in the head block.
# TYPE prometheus_tsdb_head_series gauge
prometheus_tsdb_head_series 491
# HELP prometheus_tsdb_head_series_created_total total number of series created in the head
# TYPE prometheus_tsdb_head_series_created_total counter
prometheus_tsdb_head_series_created_total 491
# HELP prometheus_tsdb_head_series_not_found_total total number of requests for series that were not found.
# TYPE prometheus_tsdb_head_series_not_found_total counter
prometheus_tsdb_head_series_not_found_total 0
# HELP prometheus_tsdb_head_series_removed_total total number of series removed in the head
# TYPE prometheus_tsdb_head_series_removed_total counter
prometheus_tsdb_head_series_removed_total 0
# HELP prometheus_tsdb_head_truncations_failed_total total number of head truncations that failed.
# TYPE prometheus_tsdb_head_truncations_failed_total counter
prometheus_tsdb_head_truncations_failed_total 0
# HELP prometheus_tsdb_head_truncations_total total number of head truncations attempted.
# TYPE prometheus_tsdb_head_truncations_total counter
prometheus_tsdb_head_truncations_total 0
# HELP prometheus_tsdb_lowest_timestamp Lowest timestamp value stored in the database. The unit is decided by the library consumer.
# TYPE prometheus_tsdb_lowest_timestamp gauge
prometheus_tsdb_lowest_timestamp 1.575795105433e+12
# HELP prometheus_tsdb_lowest_timestamp_seconds Lowest timestamp value stored in the database.
# TYPE prometheus_tsdb_lowest_timestamp_seconds gauge
prometheus_tsdb_lowest_timestamp_seconds 1.575795105433e+09
# HELP prometheus_tsdb_reloads_failures_total Number of times the database failed to reload block data from disk.
# TYPE prometheus_tsdb_reloads_failures_total counter
prometheus_tsdb_reloads_failures_total 0
# HELP prometheus_tsdb_reloads_total Number of times the database reloaded block data from disk.
# TYPE prometheus_tsdb_reloads_total counter
prometheus_tsdb_reloads_total 1
# HELP prometheus_tsdb_retention_limit_bytes Max number bytes to be retained in the tsdb blocks, configured 0 means disabled
# TYPE prometheus_tsdb_retention_limit_bytes gauge
prometheus_tsdb_retention_limit_bytes 0
# HELP prometheus_tsdb_size_retentions_total The number of times that blocks were deleted because the maximum number of bytes was exceeded.
# TYPE prometheus_tsdb_size_retentions_total counter
prometheus_tsdb_size_retentions_total 0
# HELP prometheus_tsdb_storage_blocks_bytes The number of bytes that are currently used for local storage by all blocks.
# TYPE prometheus_tsdb_storage_blocks_bytes gauge
prometheus_tsdb_storage_blocks_bytes 0
# HELP prometheus_tsdb_symbol_table_size_bytes Size of symbol table on disk (in bytes)
# TYPE prometheus_tsdb_symbol_table_size_bytes gauge
prometheus_tsdb_symbol_table_size_bytes 0
# HELP prometheus_tsdb_time_retentions_total The number of times that blocks were deleted because the maximum time limit was exceeded.
# TYPE prometheus_tsdb_time_retentions_total counter
prometheus_tsdb_time_retentions_total 0
# HELP prometheus_tsdb_tombstone_cleanup_seconds The time taken to recompact blocks to remove tombstones.
# TYPE prometheus_tsdb_tombstone_cleanup_seconds histogram
prometheus_tsdb_tombstone_cleanup_seconds_bucket{le="0.005"} 0
prometheus_tsdb_tombstone_cleanup_seconds_bucket{le="0.01"} 0
prometheus_tsdb_tombstone_cleanup_seconds_bucket{le="0.025"} 0
prometheus_tsdb_tombstone_cleanup_seconds_bucket{le="0.05"} 0
prometheus_tsdb_tombstone_cleanup_seconds_bucket{le="0.1"} 0
prometheus_tsdb_tombstone_cleanup_seconds_bucket{le="0.25"} 0
prometheus_tsdb_tombstone_cleanup_seconds_bucket{le="0.5"} 0
prometheus_tsdb_tombstone_cleanup_seconds_bucket{le="1"} 0
prometheus_tsdb_tombstone_cleanup_seconds_bucket{le="2.5"} 0
prometheus_tsdb_tombstone_cleanup_seconds_bucket{le="5"} 0
prometheus_tsdb_tombstone_cleanup_seconds_bucket{le="10"} 0
prometheus_tsdb_tombstone_cleanup_seconds_bucket{le="+Inf"} 0
prometheus_tsdb_tombstone_cleanup_seconds_sum 0
prometheus_tsdb_tombstone_cleanup_seconds_count 0
# HELP prometheus_tsdb_vertical_compactions_total Total number of compactions done on overlapping blocks.
# TYPE prometheus_tsdb_vertical_compactions_total counter
prometheus_tsdb_vertical_compactions_total 0
# HELP prometheus_tsdb_wal_completed_pages_total total number of completed pages.
# TYPE prometheus_tsdb_wal_completed_pages_total counter
prometheus_tsdb_wal_completed_pages_total 23
# HELP prometheus_tsdb_wal_corruptions_total Total number of WAL corruptions.
# TYPE prometheus_tsdb_wal_corruptions_total counter
prometheus_tsdb_wal_corruptions_total 0
# HELP prometheus_tsdb_wal_fsync_duration_seconds Duration of WAL fsync.
# TYPE prometheus_tsdb_wal_fsync_duration_seconds summary
prometheus_tsdb_wal_fsync_duration_seconds{quantile="0.5"} NaN
prometheus_tsdb_wal_fsync_duration_seconds{quantile="0.9"} NaN
prometheus_tsdb_wal_fsync_duration_seconds{quantile="0.99"} NaN
prometheus_tsdb_wal_fsync_duration_seconds_sum 0
prometheus_tsdb_wal_fsync_duration_seconds_count 0
# HELP prometheus_tsdb_wal_page_flushes_total total number of page flushes.
# TYPE prometheus_tsdb_wal_page_flushes_total counter
prometheus_tsdb_wal_page_flushes_total 312
# HELP prometheus_tsdb_wal_segment_current WAL segment index that TSDB is currently writing to.
# TYPE prometheus_tsdb_wal_segment_current gauge
prometheus_tsdb_wal_segment_current 0
# HELP prometheus_tsdb_wal_truncate_duration_seconds Duration of WAL truncation.
# TYPE prometheus_tsdb_wal_truncate_duration_seconds summary
prometheus_tsdb_wal_truncate_duration_seconds_sum 0
prometheus_tsdb_wal_truncate_duration_seconds_count 0
# HELP prometheus_tsdb_wal_truncations_failed_total total number of WAL truncations that failed.
# TYPE prometheus_tsdb_wal_truncations_failed_total counter
prometheus_tsdb_wal_truncations_failed_total 0
# HELP prometheus_tsdb_wal_truncations_total Total number of WAL truncations attempted.
# TYPE prometheus_tsdb_wal_truncations_total counter
prometheus_tsdb_wal_truncations_total 0
# HELP promhttp_metric_handler_requests_in_flight Current number of scrapes being served.
# TYPE promhttp_metric_handler_requests_in_flight gauge
promhttp_metric_handler_requests_in_flight 1
# HELP promhttp_metric_handler_requests_total Total number of scrapes by HTTP status code.
# TYPE promhttp_metric_handler_requests_total counter
promhttp_metric_handler_requests_total{code="200"} 142
promhttp_metric_handler_requests_total{code="500"} 0
promhttp_metric_handler_requests_total{code="503"} 0
```

</p>
</details>

Let's stop the container.
``shell
docker stop prometheus
```

### Monitoring of microservices condition

#### Let's reorder the directory structure

Before proceeding to the next step, let's make the directory structure clearer/friendly:

1. Let's create a directory [docker](docker) in the root of the repository and move the directory `docker-monolith` and the files `docker-compose.*` to it, and all `.env` (`.env` should be in [.gitgnore](.gitgnore), to the repository and create `.env.example](.env.example).
2. Let's create the [monitoring](monitoring) directory in the root of the repository. This directory will store everything related to monitoring.
3. Do not forget about [.gitgnore](.gitgnore) and update records if necessary (added record `.env`).

**P.S.** From now on, the assembly of services is separated from `docker-compose`, so the instructions `build` ** deleted** from [src/docker-compose.yml](src/docker-compose.yml).

#### creating a Docker image

After getting acquainted with the Prometheus web interface and its standard configuration, let's build our DockerHub image with the configuration for monitoring our microservices.

Create [monitoring/prometheus] directory. Then create a simple [Dockerfile](monitoring/prometheus/Dockerfile) in this directory which will copy the configuration file from our machine into the container:
``shell
mkdir -p monitoring/prometheus && touch Dockerfile
```
``dockerfile
FROM prom/prometheus:v2.1.0
ADD prometheus.yml /etc/prometheus/
```

#### Configuration

The entire Prometheus configuration, unlike many other monitoring systems, takes place through configuration files and command line options.

We will define a simple configuration file to collect metrics from our microservices. In the [monitoring/prometheus](monitoring/prometheus) directory we've created the file [prometheus.yml](monitoring/prometheus/prometheus.yml) with the following content:
```yaml
---
global:
  scrape_interval: '5s'

scrape_configs:
  - job_name: 'prometheus'
    static_configs:
      - targets:
        - 'localhost:9090'.

  - job_name: 'ui'
    static_configs:
      - targets:
        - 'ui:9292'.

  - job_name: 'comment'
    static_configs:
      - targets:
        - 'comment:9292'
```

- The file [monitoring/prometheus/Dockerfile] has been fixed according to the instructions of the printer (replace `ADD` with `COPY`).

#### Create an image

In the prometheus directory we build a Docker image:
``shell
export USER_NAME=dockerhub_login
cd monitoring/prometheus
docker build -t $USER_NAME/prometheus .
```

At the end of the lesson you will need to run the images you collected in this lesson on the DockerHub.

#### Images of microservices

The microservices code has a healthcheck to check if the application is working properly.

Now you need to build images using the scripts `docker_build.sh`, which are in the directory of each service. With this script, we will add information from Git to our healthcheck.

An example script
``shell
#!/bin/bash

echo `git show --format="%h" HEAD | head -1` > build_info.txt
echo `git rev-parse --abbrev-ref HEAD` >> build_info.txt.

docker build -t $USER_NAME/ui .
```

#### Collect images

Build images using scripts `docker_build.sh` in the directory of each service.
``shell
cd src/comment && bash ./docker_build.sh && cd -
cd src/post-py && bash ./docker_build.sh && cd -
cd src/ui && bash ./docker_build.sh && cd -
```

Or all at once from the root of the repository.
``shell
for i in ui post-py comment; do cd src/$i; bash docker_build.sh cd -; done
```

In the [Makefile](Makefile) added targets for building all images individually and together.

The images are collected by `make build`.


### docker-compose.yml

All `docker-compose.*` files have been moved from [src/](src/) to [docker/](docker/).

We'll raise our Prometheus together with microservices. Define the new service in your [docker/docker-compose.yml](docker/docker-compose.yml) file.
```yaml
Services:
...
  prometheus:
    image: ${USERNAME}/prometheus
    ports:
      - '9090:9090'
    Oh..:
      - prometheus_data:/prometheus
    command: # additional command line parameters
      - '--config.file=/etc/prometheus/prometheus.yml' # path to configuration file inside the container
      - '-storage.tsdb.path=/prometheus' # path to the directory with data inside the container
      - '-storage.tsdb.retention=1d' # store data for the last 24 hours

Oh..:
  prometheus_data:
```

We will use Prometheus to monitor all our microservices, so we need the container to be able to communicate over the network with all other services defined in the compositional file.

```yaml
    Networks:
      - reddit_front
      - reddit_back
```

Also check if the service versions are up to date
in `.env` and `.env.example`.

Files `.env*` have been moved from [src/](src/) to [docker/](docker/)

#### Starting microservices

Raise the services defined in docker/dockercompose.yml

``shell
cd docker & docker-compose up -d
```

Error
``log
Pulling ui (vscoder/ui:1.0)...
ERROR: manifest for vscoder/ui:1.0 not found: manifest unknown: manifest unknown
```
The reason is that there are no images of the right version?

Versions of services in [docker/.env] (docker/.env) are replaced by `latest`.

Launch
``shell
docker-compose up -d
```
Success!
``log
Creating docker_post_db_1 ... done
Creating docker_post_1 ... done
Creating docker_ui_1 ... done
Creating docker_prometheus_1 ... done
Creating docker_comment_1 ... done
```

** Error! ** The application has not started

Diagnosis:

List of running services
``shell
docker-compose ps
```
``log
       Name Command State Ports         
--------------------------------------------------------------------------------------
docker_comment_1 puma Exit 1                         
docker_post_1 python3 post_app.py Exit 2                         
docker_post_db_1 docker-entrypoint.sh mongod Up 27017/tcp             
docker_prometheus_1 /bin/prometheus --config.f ...   Up 0.0.0.0:9090->909090/tcp
docker_ui_1 puma --debug -w 2 Exit 1
```

Container logs:

comment
``shell
docker logs docker_comment_1 
```
``log
/usr/local/lib/ruby/site_ruby/2.2.0/bundler/definition.rb:33:in `build': /app/Gemfile not found (Bundler::GemfileNotFound)
        from /usr/local/lib/ruby/site_ruby/2.2.0/bundler.rb:135:in `definition'.
        from /usr/local/lib/ruby/site_ruby/2.2.0/bundler.rb:101:in `setup'.
        from /usr/local/lib/ruby/site_ruby/2.2.0/bundler/setup.rb:20:in `<top (required)>'.
        from /usr/local/lib/ruby/site_ruby/2.2.0/rubygems/core_ext/kernel_require.rb:59:in `require'.
        from /usr/local/lib/ruby/site_ruby/2.2.0/rubygems/core_ext/kernel_require.rb:59:in `require'.
        from /usr/local/bundle/bin/puma:27:in `<main>'.
```

ui
``shell
docker logs docker_ui_1  
```
``log
/usr/local/lib/ruby/site_ruby/2.2.0/bundler/definition.rb:33:in `build': /app/Gemfile not found (Bundler::GemfileNotFound)
        from /usr/local/lib/ruby/site_ruby/2.2.0/bundler.rb:135:in `definition'.
        from /usr/local/lib/ruby/site_ruby/2.2.0/bundler.rb:101:in `setup'.
        from /usr/local/lib/ruby/site_ruby/2.2.0/bundler/setup.rb:20:in `<top (required)>'.
        from /usr/local/lib/ruby/site_ruby/2.2.0/rubygems/core_ext/kernel_require.rb:59:in `require'.
        from /usr/local/lib/ruby/site_ruby/2.2.0/rubygems/core_ext/kernel_require.rb:59:in `require'.
        from /usr/local/bundle/bin/puma:27:in `<main>'.
```

post
``shell
docker logs docker_post_1
```
``log
python3: can't open file 'post_app.py': [Errno 2] No such file or directory
```

Reason [docker/docker-compose.override.yml](docker/docker-compose.override.yml), which specifies mounting directories with code from the local host.

`docker/docker-compose.override.yml' renamed to [docker/docker-compose.override.yml.example](docker/docker-compose.override.yml.example).

Restart everything.
Launch
``shell
docker-compose down; docker-compose up -d
```
Success!
``log
Stopping docker_prometheus_1 ... done
Stopping docker_post_db_1 ... done
Removing docker_ui_1 ... done
Removing docker_comment_1 ... done
Removing docker_prometheus_1 ... done
Removing docker_post_1 ... done
Removing docker_post_db_1 ... done
Removing network docker_reddit_back
Removing network docker_reddit_front
Creating network "docker_reddit_back" with the default driver
Creating network "docker_reddit_front" with the default driver
Creating docker_post_1 ... done
Creating docker_prometheus_1 ... done
Creating docker_post_db_1 ... done
Creating docker_ui_1 ... done
Creating docker_comment_1 ... done
```

Check out .
``shell
docker ps
```
``log
CONTAINER ID IMAGE COMMAND CREATED STATUS PORTS NAMES
1571f4db0a45 vscoder/comment:latest "puma" 31 seconds ago Up 27 seconds docker_comment_1
acdd2f17984a vscoder/prometheus "/bin/prometheus --c..."   31 seconds ago Up 28 seconds 0.0.0.0:9090->9090/tcp docker_prometheus_1
eb95127cf57e vscoder/ui:latest "puma" 31 seconds ago Up 26 seconds 0.0.0.0:9292->9292/tcp docker_ui_1
2071c6919eb5 mongo:3.2 "docker-entrypoint.s..."   31 seconds ago Up 27 seconds 27017/tcp docker_post_db_1
65ad65dd8276 vscoder/post:latest "python3 post_app.py" 31 seconds ago Up 28 seconds docker_post_1
```

The application is open at http://34.76.241.120:9292/.
Prometheus is available at http://34.76.241.120:9090.
The prometheus has active endpoint-y `comment` and `ui` http://34.76.241.120:9090/targets.


#### Healthchecks

Healthcheck-and are checks that our service is healthy and running as expected. In our case, healthcheck is executed inside the microservice code and checks that all services on which its work depends are available to it.

If the services required for its operation are healthy, healthcheck returns status = 1, which corresponds to the fact that the service itself is healthy.

If one of the services it needs is not healthy or available, then the check will return status = 0.

#### Status of the UI service

In the Prometheus web interface search the metric name `ui_health`.

Indeed, there is such a metric.
``log
ui_health{branch="monitoring-1",commit_hash="2dec0f4",instance="ui:9292",job="ui",version="0.0.1" }	
```

Let's plot how the value of the ui_health metric changed over time: _Graph_ tab.

**Bear in mind** that in addition to the name of the metric and its value, we also see information in labels about the version of the application, the committee and the code branch in Git.

We can see that the UI service status was stable at 1 (but it wasn't!), which means that the service was working. Leave this graph open.

**P.S.** If your status is not equal to 1, check which service was running.
is not available (slide 32), and that you have all aliases set for DB.

#### Fix docker-machine from another host

Since the work continued from another host, there were problems connecting to docker-machine. The `docker-machine ls` team did not see the instances created. To see the previously created instance of `docker-host`, the directory `~/.docker` was copied from the first host containing the docker-machine parameters and the current state.

Since the instance had previously been stopped by `docker-machine stop docker-host`, it had to be started by `docker-machine start docker-host`.

An error occurred when running `docker-machine env docker-host`.
``log
Error checking TLS connection: Error checking and/or regenerating the certs: There was an error validating certificates for host "35.241.249.240:2376": x509: certificate is valid for 34.76.241.120, not 35.241.249.240.
You can attempt to regenerate them using 'docker-machine regenerate-certs [name]'.
Be advised that this will trigger a Docker daemon restart which might stop running containers.
```

Cause: external ip has changed.

Solution: we will re-generate certificates `docker-machine regenerate-certs docker-host `. After that we managed to successfully activate `docker-machine env docker-host` environment.

But when you go to `docker-host` by ssh `docker-machine ssh docker-host`, there was no running containers.
``shell ``
sudo docker ps -a
```
``log
CONTAINER ID IMAGE COMMAND CREATED STATUS PORTS NAMES
1571f4db0a45 vscoder/comment:latest "puma" 24 hours ago Exited (1) 20 hours ago docker_comment_1
acdd2f17984a vscoder/prometheus "/bin/prometheus --c..."   24 hours ago Exited (0) 20 hours ago docker_prometheus_1
eb95127cf57e vscoder/ui:latest "puma" 24 hours ago Exited (1) 20 hours ago docker_ui_1
2071c6919eb5 mongo:3.2 "docker-entrypoint.s..."   24 hours ago Exited (0) 20 hours ago docker_post_db_1
65ad65dd8276 vscoder/post:latest "python3 post_app.py" 24 hours ago Exited (0) 20 hours ago docker_post_1
```

Possible solution: to revive all services according to the previously described instruction in README.md.
``shell
export GOOGLE_PROJECT=<project_id_here>
docker run --rm -p 9090:9090 -d --name prometheus prom/prometheus:v2.14.0
docker-machine ip docker-host
http://35.241.249.240:9090/graph
docker stop prometheus
# And why did I do all this? # =)

source ./.venv/bin/sctivate
cd docker
docker-compose up -d
```

Error
``log
WARNING: The MONGO_VERSION variable is not set. Defaulting to a blank string.
WARNING: The UI_APP_HOME variable is not set. Defaulting to a blank string.
WARNING: The USERNAME variable is not set. Defaulting to a blank string.
WARNING: The UI_VERSION variable is not set. Defaulting to a blank string.
WARNING: The UI_PORT variable is not set. Defaulting to a blank string.
WARNING: The POST_APP_HOME variable is not set. Defaulting to a blank string.
WARNING: The POST_VERSION variable is not set. Defaulting to a blank string.
WARNING: The COMMENT_APP_HOME variable is not set. Defaulting to a blank string.
WARNING: The COMMENT_VERSION variable is not set. Defaulting to a blank string.
ERROR: The Compose file './docker-compose.yml' is invalid because:
services.ui.ports contains an invalid type, it should be a number, or an object
```
Cause: there's no env file on the new host.

Solution: copy from the first host
``shell
scp ...
docker-compose up -d
```
Everything's up. The application is available at http://35.241.249.240:9292/.

Spent: ~25 min.

#### Status of UI service. Continued

So, `ui_health` is 0.

Cause: the comment service is looking for a database on the host `comment_db` that does not exist.

It was decided in HomeWork 15 by raising a separate instance from the database with the correct name.

This time let's try to use [network alias] (https://docs.docker.com/compose/networking/#links). In [docker/docker-compose.yml](docker/docker-compose.yml) service post_db added `links:`.
```yaml
Services:
  comment:
    ...
    links:
      - "post_db:comment_db"
```

Testing:
``shell
docker-compose up -d
```
``log
docker_ui_1 is up-to-date
docker_prometheus_1 is up-to-date
docker_post_1 is up-to-date
docker_post_db_1 is up-to-date
Recreating docker_comment_1 ... done
```
The service `docker_comment` has been re-created. Check: http://35.241.249.240:9090/graph?g0.range_input=1h&g0.expr=ui_health&g0.tab=0.

The value of `ui_health` is now 1.


##### Checking metrics

Stop post service

We said that we agreed to consider the service healthy, if all the services on which it depends are also healthy.

Let's try to stop the post service for a while and check how the status of the ui service, which depends on post, will change. 

``shell
docker-compose stop post
```
``log
Stopping docker_post_1 ... done
```

After updating the chart, the `ui_health` metric has changed its value to `0` again.


##### Finding the problem

In addition to the service status, we also collect the statuses of the services on which it depends. The names of the metrics whose values correspond to these statuses are in the format `ui_health_<service-name>`.

Let's see if something bad has happened to the services, on which the UI service depends.

Let's type ui_health_ in the expression string and Prometheus will offer us to add metrics names.

Let's check the comment service. We see that the service did not change its status at this time: `ui_health_comment_availability`.

And the post service is bad: `ui_health_post_availability`.

Fix it. We found the problem and know how to fix it (we created it :)). We'll raise the post service.
``shell
docker-compose start post
```
``log
Starting post... done
```
Post service got better: `ui_health_post_availability`.
UI service too: `ui_health.


#### Individually

If you want, you can try to stop the comment service or database for some of the services and perform similar operations to monitor the situation.

I tried to put out the database.

##### Re-creation of docker-machine

The `docker-host` machine was removed after the current task was completed.

On the new host, docker-host and the entire application have been re-installed.
``shell
make docker_machine_create
eval $(docker-machine env docker-host)
docker-machine ip docker-host
```

We collect application images
``shell
export USER_NAME=vscoder
make build
```


### Collecting host metrics using an exporter

The exporter looks like an auxiliary agent for collecting metrics.

In situations when we can't implement the output of Prometheus metrics in the application code, we can use an exporter that will broadcast the metrics of the application or system in the format available for reading by Prometheus.

The exporter is:
- A program that makes metrics available for collection by Prometheus.
- Gives an opportunity to convert metrics to the format required for Prometheus
- Used when you cannot change the application code
- Examples: PostgreSQL, RabbitMQ, Nginx, Node exporter, cAdvisor

#### Node exporter

Let's use [Node Exporter] (https://github.com/prometheus/node_exporter) to collect information about the Docker host (the virtual desktops where we have the containers running) and submit this information to Prometheus.

### docker-compose.yml

Node exporter will run also in the container. Define another service in [docker/docker-compose.yml](docker/docker-compose.yml) file.

Remember also to add the network definition for the node-exporter service to provide Prometheus access to the exporter.

```yaml
Services:
  ...
  node-exporter:
    image: prom/node-exporter:v0.18.1
    user: root
    Oh..:
      - /proc:/host/proc:ro
      - /sys:/host/sys:ro
      - /:/rootfs:ro
    networks:
      - reddit_front
      - reddit_back
    command:
      - '--path.procfs=/host/proc'.
      - '--path.sysfs=/host/sys'.
      - '--collector.filesystem.ignored-mount-points='^/(sys|proc|dev|host|etc)($$|/)'.
```

#### Additional information: let's parameterize the versions of images

Versions of `prometheus` and `node_exporter` are parameterized.
[docker/docker-compose.yml](docker/docker-compose.yml)
``Yaml
Services:
  ...
  prometheus:
    image: ${USERNAME}/prometheus:${PROMETHEUS_VERSION}
    ...
  node-exporter:
    image: prom/node-exporter:${NODE_EXPORTER_VERSION}
    ...
```

In [docker/.env.example](docker/.env.example) added the following variables
``shell
PROMETHEUS_VERSION=latest
NODE_EXPORTER_VERSION=v0.18.1
```

#### Additional information: Makefile target build_prometheus

The script for building prometheus [monitoring/prometheus/docker_build.sh](monitoring/prometheus/docker_build.sh) was created.
``shell
#!/bin/bash
set -eu

docker build -t $USER_NAME/prometheus .
```

A new target `build_prometheus` has been added to [Makefile] to build prometheus with its own config.

Pick up the application
``shell
cd ./docker && docker-compose up -d
```

#### prometheus.yml

To tell Prometheus to keep track of another service, we need to add information about it to the config.

We'll add one more job:
```Yaml
scrape_configs:
  ...
  - job_name: 'node'
    static_configs:
      - targets:
      - 'node-exporter:9100'.
```

Don't forget to put together a new Docker for Prometheus:
``shell
make build_prometheus
```

#### Re-create our services

``shell
source ./.venv/bin/activate
cd ./docker
docker-compose down
docker-compose up -d
```
``log
Creating network "docker_reddit_back" with the default driver
Creating network "docker_reddit_front" with the default driver
Pulling node-exporter (prom/node-exporter:v0.18.1)...
v0.18.1: Pulling from prom/node-exporter
49a2d53aa1af: Pull complete
3589a6efd9ce: Pull complete
190160031744: Pull complete
Digest: sha256:a2f29256e53cc3e0b64d7a472512600b2e9410347d53cdc85b49f659c17e02ee
Status: Downloaded newer image for prom/node-exporter:v0.18.1
Creating docker_post_1 ... done
Creating docker_prometheus_1 ... done
Creating docker_node-exporter_1 ... done .
Creating docker_ui_1 ... done
Creating docker_post_db_1 ... done
Creating docker_comment_1 ... done
```

prometheus web interface http://35.195.16.90:9090/ has not opened. The connection has been reset.

Diagnostics:
``shell
docker-compose ps
```
``log
         Name Command State Ports         
-----------------------------------------------------------------------------------------
docker_comment_1 puma Up                             
docker_node-exporter_1 /bin/node_exporter --path. ...   Up 9100/tcp              
docker_post_1 python3 post_app.py Up                             
docker_post_db_1 docker-entrypoint.sh mongod Up 27017/tcp             
docker_prometheus_1 /bin/prometheus --config.f ...   Exit 1                         
docker_ui_1 puma Up 0.0.0.0:9292->9292/tcp
```
The prometheus service has completed its work. Watch the logs.
``shell
docker-compose logs prometheus
```
``log
...
prometheus_1 | level=error ts=2019-12-10T06:20:50.235Z caller=main.go:736 err="error loading config from \"/etc/prometheus/prometheus.yml\": couldn't load configuration (--config.file=\"/etc/prometheus/prometheus. yml\"): parsing YAML file /etc/prometheus/prometheus.yml: yaml: unmarshal:\n line 24: cannot unmarshal ! str `node-ex...` into struct { Targets []string \"yaml:\\\\"targets\\\"\"; Labels model.LabelSet \"yaml:\\\"labels\\\"\" }".
```
Cause: curve [monitoring/prometheus/prometheus.yml](monitoring/prometheus/prometheus.yml)

Fixed:
``Yaml
...
  - job_name: "node"
    static_configs:
      - targets:
          - "node-exporter:9100."
```

Collect an image, run applications.
``shell
cd ... && make build_prometheus && cd -
docker-compose up -d
```
``log
docker_post_1 is up-to-date
docker_ui_1 is up-to-date
Recreating docker_prometheus_1 ... 
docker_node-exporter_1 is up-to-date
docker_post_db_1 is up-to-date
Recreating docker_prometheus_1 ... done
```
Check out .
``shell
docker-compose ps
```
``log
         Name Command State Ports         
----------------------------------------------------------------------------------------
docker_comment_1 puma Up                            
docker_node-exporter_1 /bin/node_exporter --path. ...   Up 9100/tcp              
docker_post_1 python3 post_app.py Up                            
docker_post_db_1 docker-entrypoint.sh mongod Up 27017/tcp             
docker_prometheus_1 /bin/prometheus --config.f ...   Up 0.0.0.0:9090->909090/tcp
docker_ui_1 puma Up 0.0.0.0:9292->9292/tcp
```

It seems to be all right. Checking web-interface http://35.195.16.90:9090/graph opened ** successfully**.

Let's see, Prometheus endpoint list http://35.195.16.90:9090/targets - another endpoint should appear.

#### Getting information

Get information about CPU usage: `node_load1`.
``log
node_load1{instance="node-exporter:9100",job="node"} 0
```

Let's go to the host `docker-machine ssh docker-host`.

Let's add loads: `yes > /dev/null'.

The graph at http://35.195.16.90:9090/graph?g0.range_input=1h&g0.expr=node_load1&g0.tab=0 shows that the load has increased.

### completion of work

### Makefile

Targets have been added:
- push_comment
- push_post
- push_ui
- push_prometheus
- push

#### Let the images go

Run the images you collected on DockerHub (from the root of the project):
``shell
docker login
make push
```

Link to docker-hub https://hub.docker.com/u/vscoder.

### Tasks from \ ##

#### MongoDB exporter

Add MongoDB monitoring to Prometheus using the required exporter.

The exporter was chosen [percona/mongodb_exporter] (https://github.com/percona/mongodb_exporter) from percona, as it is presented by a well-known developer, and also as the only one presented on prometheus wiki [Default port allocations] (https://github.com/prometheus/prometheus/wiki/Default-port-allocations).

The exporter [dcu/mongodb_exporter] (https://github.com/dcu/mongodb_exporter), presented at https://prometheus.io/docs/instrumenting/exporters/, was not selected based on recommendations from ERS.

##### Installation

Added Makefile target `mongodb_exporter_clone`, which clones the repository with github.
``makefile
mongodb_exporter_clone:
	cd ./monitoring && git clone https://github.com/percona/mongodb_exporter.git
```
Cloned repository
``shell
make mongodb_exporter_clone
```
``log
cd ./monitoring && git clone https://github.com/percona/mongodb_exporter.git
Cloning in "mongodb_exporter"...
Enumerating objects: 39, done.
remote: Counting objects: 100% (39/39), done.
remote: Compressing objects: 100% (34/34), done.
remote: Total 5517 (delta 7), reused 14 (delta 3), pack-reused 5478.
Receiving objects: 100% (5517/5517), 6.16 MiB | 267.00 KiB/s, ready.
Definition of changes: 100% (2731/2731), ready.
```

Added Makefile target `mongodb_exporter_docker_build`, which collects the docker container.
``makefile
# mongodb_exporter
MONGODB_EXPORTER_DOCKER_IMAGE_NAME?=${USER_NAME}/mongodb-exporter
MONGODB_EXPORTER_VERSION?=v0.10.0
mongodb_exporter_docker_build:
	cd ./monitoring/mongodb_exporter && make docker DOCKER_IMAGE_NAME=${MONGODB_EXPORTER_DOCKER_IMAGE_NAME} DOCKER_IMAGE_TAG=${MONGODB_EXPORTER_VERSION}
```
Built docker-image `vscoder/mongodb-mongodb_exporter:v0.10.0`.
``shell
make mongodb_exporter_docker_build
```
``log
...
Successfully built 8da76a8e3cbb
Successfully tagged vscoder/mongodb-exporter:v0.10.0
```

In [docker/.env](docker/.env) added variable `MONGODB_EXPORTER_VERSION=v0.10.0`.

In [docker/docker-compose.yml](docker/docker-compose.yml) added `postdb-exporter` service.
``Yaml
postdb-exporter:
  image: ${USERNAME}/mongodb-exporter:${MONGODB_EXPORTER_VERSION}
  Networks:
    #- reddit_front
    - reddit_back
  Environment:
    MONGODB_URI: "mongodb://post_db:27017".
```

In [monitoring/prometheus/prometheus.yml] added job
``Yaml
scrape_config:
  ...
  - job_name: "post_db"
    static_configs:
      - targets:
        - "postdb-exporter:9216"
```

In [.gitignore](.gitignore) added line
```
monitoring/mongodb_exporter
```

In Makefile target `build` added build `mongodb_exporter_docker_build`.

In Makefile target `push` added upload `mongodb_exporter_push`.

Assembly of everything
``shell
make build
```
successfully

A target `run` has been added to the Makefile. The application has been launched.
``shell
make run
```

Check http://35.195.16.90:9090.
``log
mongodb_exporter_build_info{goversion="go1.11.13",instance="postdb-exporter:9216",job="post_db"}.	
```


### Cloudprober

It was decided to use cloudprober due to its greater functionality compared to blackbox_exporter. In particular, it is possible to use "external" checks by the script, which may be useful later.

The official site https://cloudprober.org/.

Link to github https://github.com/google/cloudprober.

Docker-image https://hub.docker.com/r/cloudprober/cloudprober

Documentation https://cloudprober.org/getting-started/.

##### Implementation

A [monitoring/cloudprober/Dockerfile] file has been created adding a confick to the cloudprober image.
``dockerfile
FROM cloudprober/cloudprober:v0.10.5
COPY cloudprober.cfg /etc/cloudprober.cfg
```

The file [monitoring/cloudprober/cloudprober.cfg](monitoring/cloudprober/cloudprober.cfg) containing cloudprober configuration was created.
``conf
probe {
  name: "ui"
  type: HTTP
  targets {
    host_names: "ui:9292"
  }
  interval_msec: 5000 # 5s
  timeout_msec: 1000 # 1s
}
probe {
  name: "comment"
  type: HTTP
  targets {
    host_names: "comment:9292"
  }
  interval_msec: 5000 # 5s
  timeout_msec: 1000 # 1s
}
probe {
  name: "post"
  type: HTTP
  targets {
    host_names: "post:5000"
  }
  interval_msec: 5000 # 5s
  timeout_msec: 1000 # 1s
}
```

Created file [monitoring/cloudprober/docker_build.sh](monitoring/cloudprober/docker_build.sh) that collects image `$USER_NAME/cloudprober`.
``shell
#!/bin/bash
set -eu

docker build -t $USER_NAME/cloudprober .
```

In the [Makefile](Makefile) added targets 
- `cloudprober_build` to build the image
``makefile
cloudprober_build:
	cd ./monitoring/cloudprober & bash docker_build.sh
```
- `cloudprober_push` to upload an anker-hub image
``makefile
cloudprober_push:
	docker push ${USER_NAME}/cloudprober
```

The created goals are added to `build` and `push` goals respectively.
``makefile
build: build_post build_comment build_ui build_prometheus mongodb_exporter_docker_build cloudprober_build

push: push_comment push_post push_ui push_prometheus mongodb_exporter_push cloudprober_push
```

To [monitoring/prometheus/prometheus.yml] added job
``Yaml
  - job_name: "cloudprober"
    scrape_interval: 10s
    static_configs:
      - targets:
          - "cloudprober:9313"
```

In [docker/.env.example] (docker/.env.example) added variable `CLOUDPROBER_VERSION=latest`.

In [docker/docker-compose.yml](docker/docker-compose.yml) added service
``Yaml
  cloudprober:
    image: ${USERNAME}/cloudprober:${CLOUDPROBER_VERSION}
    Networks:
      - reddit_back
```

Fixed Makefile target `mongodb_exporter_clone`. Now the repository c `mongodb_exporter` is cloned only if the directory `monitoring/mongodb_exporter` does not exist.

Everything is assembled.
``shell
make build
```

Launching the application:
``shell
make run
```

Checked:

total http://104.155.62.111:9090/graph?g0.range_input=1h&g0.expr=total&g0.tab=1
``log
total{dst="comment:9292",instance="cloudprober:9313",job="cloudprober",probe="comment",ptype="http" } 114
total{dst="post:5000",instance="cloudprober:9313",job="cloudprober",probe="post",ptype="http" } 116
total{dst="ui:9292",instance="cloudprober:9313",job="cloudprober",probe="ui",ptype="http" } 116
```

success http://104.155.62.111:9090/graph?g0.range_input=1h&g0.expr=success&g0.tab=1
``log
success{dst="comment:9292",instance="cloudprober:9313",job="cloudprober",probe="comment",ptype="http" } 124
success{dst="post:5000",instance="cloudprober:9313",job="cloudprober",probe="post",ptype="http" } 126
success{dst="ui:9292",instance="cloudprober:9313",job="cloudprober",probe="ui",ptype="http"} 0
```

latency http://104.155.62.111:9090/graph?g0.range_input=1h&g0.expr=latency&g0.tab=1
``log
latency{dst="comment:9292",instance="cloudprober:9313",job="cloudprober",probe="comment",ptype="http" } 323976.069
latency{dst="post:5000",instance="cloudprober:9313",job="cloudprober",probe="post",ptype="http" } 436631.507
latency{dst="ui:9292",instance="cloudprober:9313",job="cloudprober",probe="ui",ptype="http"} 0
```

Problem: ui service is unavailable

Cause: `reddit_front` network was not added to [docker/docker-compose.yml](docker/docker-compose.yml) service `cloudprober`. Fixed .
``Yaml
  cloudprober:
    image: ${USERNAME}/cloudprober:${CLOUDPROBER_VERSION}
    Networks:
      - reddit_back
      - reddit_front
```

Restart .
``shell
make run
```

success http://104.155.62.111:9090/graph?g0.range_input=1h&g0.expr=success&g0.tab=1
``log
success{dst="comment:9292",instance="cloudprober:9313",job="cloudprober",probe="comment",ptype="http" } 6
success{dst="post:5000",instance="cloudprober:9313",job="cloudprober",probe="post",ptype="http" } 8
success{dst="ui:9292",instance="cloudprober:9313",job="cloudprober",probe="ui",ptype="http" } 8
```

total http://104.155.62.111:9090/graph?g0.range_input=1h&g0.expr=total&g0.tab=1
``log
total{dst="comment:9292",instance="cloudprober:9313",job="cloudprober",probe="comment",ptype="http" } 16
total{dst="post:5000",instance="cloudprober:9313",job="cloudprober",probe="post",ptype="http" } 18
total{dst="ui:9292",instance="cloudprober:9313",job="cloudprober",probe="ui",ptype="http" } 18
```

latency http://104.155.62.111:9090/graph?g0.range_input=1h&g0.expr=latency&g0.tab=1
``log
latency{dst="comment:9292",instance="cloudprober:9313",job="cloudprober",probe="comment",ptype="http" } 63902.087
latency{dst="post:5000",instance="cloudprober:9313",job="cloudprober",probe="post",ptype="http" } 91329.549
latency{dst="ui:9292",instance="cloudprober:9313",job="cloudprober",probe="ui",ptype="http"} 845258.711
```

failure_ratio `(rate(total[1m]) - rate(success[1m])) / rate(total[1m])` and avg_latency `rate(latency[1m]) / rate(success[1m]) / 1000` http://104.155.62.111:9090/graph?g0.range_input=1h&g0. expr=(rate(total%5B1m%5D)%20-%20rate(success%5B1m%5D))%20%2F%20rate(total%5B1m%5D)&g0.tab=0&g1.range_input=1h&g1.expr=rate(latency%5B1m%5D)%20%2F%20rate(success%5B1m%5D)%20%2F%201000&g1.tab=0.


#### Makefile

In the [Makefile](Makefile) added targets

| Purpose | Description |
| ----------------------------- | ------------------------------------------------------------------------------------------------ |
| build_comment | Collect image comment |
| build_post | Collect image post |
| build_ui | Collect image ui |
| build_prometheus | Collect prometheus with our config |.
| build | Collect all images |
| push_comment | Push to the image docker hub `${USER_NAME}/comment` |.
| push_post | Push to image docker hub `${USER_NAME}/post` |.
| push_ui | Push to the image docker hub `${USER_NAME}/ui` |.
| push_prometheus | Push to the image docker hub `${USER_NAME}/prometheus` |.
| push | Push to the docker hub of all images |
| mongodb_exporter_clone | Repository cloning https://github.com/percona/mongodb_exporter.git |
| mongodb_exporter_docker_build | Assemble docker-image with mongodb-exporter |.
| mongodb_exporter_push | Push into the image docker hub `${MONGODB_EXPORTER_DOCKER_IMAGE_NAME}:${MONGODB_EXPORTER_VERSION}` |.
| cloudprober_build | build docker-image cloudprober |
| cloudprober_push | Push to image docker hub `${USER_NAME}/cloudprober` |.
| variables | Create variables `docker/.env` from `docker/.env.example`, if `docker/.env` does not exist yet |.

TODO: implement push-like images with the correct version

### project launch

#### Preparations

It is necessary to fill in `env` for example `env.example` beforehand, and also will execute authorization in `gcloud`.

``shell
# Installing docker-machine
install_docker_machine

# Creating docker-machine
docker_machine_create

# The use of docker-machine
eval $(docker-machine env docker-host)

# Find out about docker-machine ip
make docker_machine_ip
```

#### project launch

``shell
# Collecting images
source ./env
make build

# Application launcher
make run
```

Annex: http://<IP_OF_DOCKER_MACHINE_INSTANCE_OR_LOCALHOST>:9292.

Monitoring: http://<IP_OF_DOCKER_MACHINE_INSTANCE_OR_LOCALHOST>:9090/graph?g0.range_input=1h&g0. expr=(rate(total%5B1m%5D)%20-%20rate(success%5B1m%5D))%20%2F%20rate(total%5B1m%5D)&g0.tab=0&g1.range_input=1h&g1.expr=rate(latency%5B1m%5D)%20%2F%20rate(success%5B1m%5D)%20%2F%201000&g1.tab=0.



## HomeWork 17: Monitoring applications and infrastructure


### Plan

1. Container Docker Monitoring
2. Metrics visualization
3. Collecting application and business metrics
4. Setting up and checking your allergies
5. Many tasks from ⭐ (optional).


### Container Docker Monitoring


#### Preparations for the environment

You need to open ports in the firewall for new services
on their own as they're added.

Let's create a Docker host in GCE and configure the local environment to
handling it

An example from remote control:
``shell
$ export GOOGLE_PROJECT=_your project_

# Create a dock host
docker-machine create --driver google \.
    --google-machine-image https://www.googleapis.com/compute/v1/projects/ubuntu-os-cloud/global/images/family/ubuntu-1604-lts \.
    --google-machine-type n1-standard-1 \.
    --google-zone europe-west1-b \
    docker-host

# Set up a docker client on a remote docker demon
eval $(docker-machine env docker-host)

# Switching to a local docker
eval $(docker-machine env --unset)

$ docker-machine ip docker-host

$ docker-machine rm docker-host
```

But we'll go the other way:
" hell
make docker_machine_create DOCKER_MACHINE_TYPE=n1-standard-1
eval $(docker-machine env docker-host)
make docker_machine_ip
```


#### Container Docker Monitoring

Let's split the Docker Compose files:

At the moment both monitoring and applications are described in one big [docker-compose.yml](docker/docker-compose.yml). On the one hand, it is simple, but on the other hand, we mix different entities and the file itself grows rapidly.

Let's leave the description of the applications in [docker-compose.yml](docker/docker-compose.yml), and the monitoring will be separated into a separate file [docker-compose-monitoring.yml](docker/docker-compose-monitoring.yml).

To start the applications, we will use `docker-compose up -d` as before, and for monitoring - `docker-compose -f docker-compose-monitoring.yml up -d`.


#### cAdvisor

We will use [cAdvisor] (https://github.com/google/cadvisor) to monitor the status of our Docker containers.

cAdvisor collects information about the resources consumed by our containers and the characteristics of their operation.

Examples of metrics are:
- The percentage of CPU and memory used by the container that is allocated to run it,
- network traffic volume
- etc.

#### File docker-compose-monitoring.yml

cAdvisor will also run in the container. To do this, add a new service to our compositional monitoring file [docker/docker-compose-monitoring.yml](docker/docker-compose-monitoring.yml).

Place this service in one network with Prometheus so that it could collect metrics from it.

```Yaml.
cadvisor:
  image: google/cadvisor:v0.33.0
  Cadvisor:
    - '/:/rootfs:ro'
    - '/var/run:/var/run:rw'.
    - "/sys:/sys:ro
    - '/var/lib/docker/:/var/lib/docker:ro'.
  ports:
    - '8080:8080'
```

#### File prometheus.yml

Let's add information about the new service to [Prometheus configuration] (monitoring/prometheus/prometheus.yml) so that it starts collecting metrics:
```yaml
scrape_configs:
  ...
  - job_name: 'cadvisor'.
    static_configs:
      - targets:
        - 'cadvisor:8080'.
```

Let's rebuild the Prometheus image with the updated configuration.

An example from the lecture:
``shell
export USER_NAME=username # where username is your Docker Hub login.
docker build -t $USER_NAME/prometheus .
```

But we're good at feng shui (almost):

Added it to [env.example](env.example)
``shell
export USER_NAME=${USERNAME}
```

In the Makefile, we will add the `**_build` and `**_push` targets.
``shell
. ./env && \
...
```

And the assembly:
``shell
make build_prometheus
```

#### cAdvisor UI

Let's launch services (not our method as usual)):
``shell
docker-compose up -d
docker-compose -f docker-compose-monitoring.yml up -d
```

The Makefile target `run` is given in the following form:
``makefile
run:
	cd docker \
	&& ../.venv/bin/docker-compose up -d \.
	&& ../.venv/bin/docker-compose -f docker-compose-monitoring.yml up -d
```

Launch
``shell
make run
```

Images have been successfully downloaded from docker hub. The project has been launched.
``log
...
Creating docker_ui_1 ... done
Creating docker_post_db_1 ... done
Creating docker_post_1 ... done
Creating docker_comment_1 ... done
...
WARNING: Found orphan containers (docker_comment_1, docker_post_1, docker_post_db_1, docker_ui_1) for this project. If you removed or renamed this service in your compose file, you can run this command with the --remove-orphans flag to clean it up.

Creating docker_prometheus_1 ... done .
Creating docker_cadvisor_1 ... done .
Creating docker_node-exporter_1 ... done .
Creating docker_cloudprober_1 ... done
Creating docker_postdb-exporter_1 ... done
```

cAdvisor has a UI that displays the information collected about containers.

Let's open port 8080 in gcloud.
``shell
gcloud compute firewall-rules create cadvisor \
  --allow tcp:8080 \
  --target-tags=docker-machine \.
  -description="Allow cAdvisor UI connections" \
  --direction=INGRESS
```
We wait a few minutes... To no avail.

We can see in the prometheus that he doesn't see cAdvisor.

I forgot to add networks to the `cadvisor` service [docker/docker-compose-monitoring.yml](docker/docker-compose-monitoring.yml)
``Yaml
Services:
  cadvisor:
    image: google/cadvisor:v0.33.0
    Cadvisor:
      - "/:/rootfs:ro"
      - "/var/run:/var/run:rw."
      - "/sys:/sys:ro"
      - "/var/lib/docker/:/var/lib/docker:ro."
    ports:
      - "8080:8080"
    Networks:
      - reddit_back
      - reddit_front
```
``shell
make run
```
we created a firewall rule in the wrong project, as you can see from the logs.

By some reason, the rule was created all the time in the project... Set the project with the command `gcloud config set project <project_id>> ` after which the rule was created where it is needed.

``shell
gcloud compute firewall-rules delete cadvisor

gcloud config set project <project_id>

gcloud compute firewall-rules create cadvisor \
  --allow tcp:8080 \
  --target-tags=docker-machine \.
  -description="Allow cAdvisor UI connections" \
  --direction=INGRESS
```

Open the Web UI page at http://<docker-machinehost-ip>:8080.

Nothing like that, netdata is prettier)) Although cAdvisor is more obvious as the number of metrics visible without scrolling. Actually, it's fat:
``log
root 14 262 14 236 18:52 6.30 2.80 105.67 MiB 786.48 MiB Ssl 00:01:18 cadvisor
```

Click the Docker Containers link (bottom left) to view container information.

In the UI we can see:
- a list of containers running on the host
- host information (Driver Status section)
- container image information (Images section)

Click on the name of one of the containers to see information about its operation:

It shows information about the processes, CPU usage, memory, network and file system:

On the /metrics path all collected metrics are published for collection by Prometheus: http://34.77.224.184:8080/metrics.

We see that the names of container metrics begin with the word `container`.

Let's make sure the container metrics are collected. Let's enter the word `container` and see what he proposes to add: yes, it does...


### Visualization of metrics: Grafana.

We use the Grafana tool to visualize data from Prometheus.

Add new service to [docker-compose-monitoring.yml](docker/docker-compose-monitoring.yml). Also add grafana into the network `reddit_front`.
``Yaml
Services:

  grafana:
    image: grafana/grafana:${GRAFANA_VERSION}
    Oh..:
      - grafana_data:/var/lib/grafana
    Environment:
      - GF_SECURITY_ADMIN_USER=admin
      - GF_SECURITY_ADMIN_PASSWORD=secret
    Depend_on:
      - prometheus
    ports:
      - 3000:3000
    Networks:
      - reddit_front

Oh..:
  grafana_data:
```
In the DS it is specified to use `grafana:5.0.0`, it is specified to install `grafana:6.5.2` - this is more interesting))).

For `cadvisor` the version of the image has been parameterized.

The service `cadvisor` is also left only on the network `reddit_front` because it does not need to interact with anything except prometheus.

Let's pick up the docker-machine again (as the work continues from another place, the machine was killed earlier).

``shell
make docker_machine_create
eval $(docker-machine env docker-host)
make docker_machine_ip
```

#### Grafana: Web UI

Let's launch a new service:
``Yaml
docker-compose -f docker-compose-monitoring.yml up -d grafana
```
... they wrote, but we're not running anything!!! So we're gonna start everything:
``hell...
make run
```

Let's add a firewall rule.
``shell
gcloud compute firewall-rules create grafana \
  --allow tcp:3000 \
  --target-tags=docker-machine \.
  -description="Allow grafana UI connections" \
  --direction=INGRESS
```

Let's open the Web UI Grafana page at http:// <dockermachine-host-ip>:3000 and use the administrator login and password that we passed through the environment variables:


#### Grafana: Adding a data source

Click Add data source:

Select the desired type and set the connection parameters:

- Type: Prometheus
- Name: Prometheus Server
- URL: http://prometheus:9090

**Save & Test**


#### Dashboards

Let's go to [grafana site] (https://grafana.com/grafana/dashboards), where you can find and download a large number of already created official and community dashboards to visualize different types of metrics for different monitoring systems and databases.

Let's choose our monitoring system (Prometheus) as the data source and search by Docker category. Then we will choose the popular dashboard: **Docker + System dashboard**.

Press _Download JSON_. In the directory `monitoring` create
directories `grafana/dashboards` where you can put your downloaded
dashboard. Change the dashboard file name to
[DockerMonitoring.json] (monitoring/grafana/dashboards/DockerMonitoring.json).


#### Import of dashboards.

Open the Grafana web interface again and choose to import the template (Dashboards -> Manage -> Import).

Download the downloaded dashboard. When downloading, specify the source
data for visualization (Prometheus Server):

A set of charts with status information should appear.
of the host system and container operation: appeared, but no data. 

**Problem:** not all view in prometheus. **Cause:** outdated configuration [monitoring/prometheus/prometheus.yml](monitoring/prometheus/prometheus.yml). After yesterday's work the updated prometheus image was not uploaded to docker-hub.

We'll fix it:
``shell 
export USER_NAME=dockerhub_username
make build_prometheus push_prometheus
```

Let's go:
``shell
make run
```

**Trouble:** no metrics `node_exporter` are displayed. **Cause:** incorrect metrics names. For example:

| grafana | node_exporter |.
| -------------------- | -------------------------- |
| node_filesystem_size | node_filesystem_size_bytes |
| node_filesystem_free | node_filesystem_free_bytes |.

Previously selected dashboard `Last updated: 2 years ago `

Picked a dashboard https://grafana.com/grafana/dashboards/9633.

Part of the metrics wasn't displayed because of a hardcore job name `node-exporter`. Added a variable `node_job_name` with `query` `label_values(node_boot_time_seconds, job)` that returns the job name.

In the json-representation dashboard fixed `node-exporter` to `$node_job_name`. Now all the charts are displayed.

Saved actual json in [monitoring/grafana/dashboards/DockerMonitoring.json].


### Collecting application metrics

As an example of application metrics in the UI service [we added] (https://github.com/express42/reddit/commit/e443f6ab4dcf25f343f2a50c01916d750fc2d096):

- counter `ui_request_count`, which counts every incoming HTTP request (adding information such as HTTP method, path, return code through labels, we specify this metric).
- Histogram `ui_request_latency_seconds`, which allows you to track information about the processing time of each request

As an example of application metrics in the Post service [we added] (https://github.com/express42/reddit/commit/d8a0316c36723abcfde367527bad182a8e5d9cf2):

- Histogram `post_read_db_seconds', which allows you to track information about the time it takes to find a post in the database.

#### Why?

The created metrics will give visibility of our application and an understanding of its current state.

For example, the HTTP request processing time should not be long, as it means that the user has to wait a long time between requests, and this impairs the overall impression of the application. Therefore, a long processing time will signal a problem for us.

By tracking incoming HTTP requests, we can see for example how many responses are returned with an error code. A large number of such responses will also signal to us a problem with the application.


#### prometheus.yml

Let's add information about the post-service to the Prometheus configuration so that it starts collecting metrics from it as well:

``Yaml
scrape_configs:
  ...
  - job_name: "post"
    static_configs:
      - targets:
          - "post:5000"
```

Reassemble (and upload to docker-hub) Prometheus image with updated configuration:

Remote Sensing variant:
``shell
export USER_NAME=username # where, usename is your login from DockerHub
docker build -t $USER_NAME/prometheus .
```

Our method
``shell
export USER_NAME=username # where, usename is your login from DockerHub
make build_prometheus push_prometheus
```

Let's re-create our Docker monitoring infrastructure (I wonder why exactly re-create everything?):

The remote control variant:
``Yaml
docker-compose -f docker-compose-monitoring.yml down
docker-compose -f docker-compose-monitoring.yml up -d
```

Let's just try to apply
``shell
make run
```
``log
Recreating docker_prometheus_1 ... done
```

And let's add some posts in the application and some comments to collect the values of the application metrics: done.


#### creating a dashboard in Grafana

Let's build charts of application metrics to be collected. Let's choose to create a new dashboard: Open the Grafana web interface again and choose to create a template (Dashboard).

1. Choose "Build chart" (New Panel ➡ Graph).
2. Click once on the name of the chart (Panel Title), then select Edit:

Let's start with a simple graph of how to change the HTTP request counter by time. Let's select the data source and enter the name of the metric in the request field:

Then just click on any place in the UI to remove the cursor from the request field and Grafana will execute the request and plot the graph.

In the upper right corner, we can reduce the time interval on which we are plotting the chart and set up automatic data updating.

We now have a graph of the various HTTP requests coming to the UI service.

We will change the chart header and description.

We will save the created dashboard.

Let's build a graph of requests that return the error code on the same dashboard. Let's add another chart on our dashboard.

Switch to the chart editing mode.

In the query field, write an expression to search for all http queries where the return code starts with either 4 or 5 (use a regular expression to search the label). Let's use the rate() function to see not only the counter value for the whole period of observation, but also the rate of increase of this value for the time interval (take, for example, a 1-minute interval, so that the chart is clearly visible).

The chart will not show anything, if there were no requests with an incorrect return code. To verify that our request is correct, let's use a non-existent HTTP path, for example http://104.199.106.171:9292/nonexistent, to get the error code 404 in response to our request.

Let's check the chart (the time interval can be reduced for better visibility of the chart).

Add a header and a description of the chart and click save the changes to the dashboard.

Grafana supports dashboard versioning, so when saving, we were asked to enter a message explaining the dashboard changes. You can see the history of changes to your own.


#### By yourself

As you can see, the first chart that we have made simply by `ui_request_count` does not display any useful information, because the type of metric `count`, and it just grows. Task: Use the rate function for the first chart (UI http requests) similar to the second chart (Rate of UI HTTP Requests with Error).

https://prometheus.io/docs/prometheus/latest/querying/functions/#rate.

Request:
``promql
rate(ui_request_count{job="ui"}[1m]).
```


#### histogram

A histogram is a graphical way of representing the distribution of probabilities of a certain random value on a given interval of values. To build a histogram, the interval of values is taken, which can take the measured value and is divided into intervals (usually the same value), these intervals are marked on the horizontal X axis. A rectangle is then drawn above each interval, the height of which corresponds to the number of measurements of the value falling into the interval.

A simple example of a histogram is the distribution of grades for a control in a class with 21 students. We take the interval of possible values (from 1 to 5) and divide it into equal intervals. Then on each interval we draw a column, the height of which corresponds to the frequency with which this grade appears.


#### Histogram metric

Prometheus has a type of histogram metrics. This type of metrics gives the value of the distribution range of the measured value in the given value range as its value. We use this type of metrics to measure the processing time of an HTTP request by our application.

Let's consider a histogram example in Prometheus. Let's see the information about the processing time of a request coming to the main application page.

``promql
ui_request_latency_seconds_bucket{path="/"}
```
but there's no such metric... On the advice of colleagues in the slag, a metric will be used...
``promql
ui_request_response_time_bucket{path="/"}
```

These values mean that there were 3 queries with the processing time `<= 0.025s', and queries `0.01 <= 0.01s' had 7 queries (this column includes 3 queries from the previous column and 4 queries from the interval `[0.025s; 0.01s]`, this histogram is also called cumulative). There are no requests that would take `> 0.01s` for processing, so the value of all subsequent columns is equal to 7.


#### Procentyl

- Numerical value in a set of values
- All numbers in the set are less than a percentage, fall within the specified percentage of values from the total number of values in the set.

##### Example percentile

There are 20 students in the class. Vanya is the fourth largest in the class. Then Vanya's height (180 cm) is 80th percentile. This means that 80% of the students are less than 180 cm tall.

##### 95th percentile

Often values of 90, 95 or 99 percent are used to analyse the monitoring data.

We will calculate the 95th percentile for the query processing time sample to see which value is the maximum limit for most (95%) queries. To do this, we will use the built-in `histogram_quantile()` function.

Add the third chart to your dashboard. In the request field, enter the following expression to calculate the 95 percent response time (gist)
``promql
histogram_quantile(0.95, sum(rate(ui_request_response_time_bucket[5m])) by (le))
```

Save the dashboard changes and export it to JSON file, which we upload to our local machine.

Put the uploaded file into the directory `monitoring/grafana/dashboards` created earlier under the name [UI_Service_Monitoring.json](monitoring/grafana/dashboards/UI_Service_Monitoring.json).


### Collecting business logic metrics

As an example of business logic metrics, we have added **post counters** and **comments** to our application.
- `post_count`.
- `comment_count`

We will plot the growth rate of the counter value for the last hour using the `rate()` function. This will allow us to get information about the activity of the application users.

Create a new dashboard, call it `Business_Logic_Monitoring` and build the chart of the function `rate(post_count[1h])`.

Draw another chart for the comment counter, export the dashboard and save it in the directory `monitoring/grafana/dashboards` named [Business_Logic_Monitoring.json](monitoring/grafana/dashboards/Business_Logic_Monitoring.json).


### Setting up and checking for allergies


##### Allerty rules

We will define several rules where we will set conditions for the states of the monitored systems under which we should receive alerts, as these conditions may lead to the unavailability or malfunction of our application.

P.S. It should be noted that Grafana itself also has alerting. But in terms of functionality it is inferior to Alertmanager in Prometheus.

#### Alertmanager

Alertmanager - an additional component for the Prometheus monitoring system, which is responsible for primary processing of alerts and further sending alerts to the specified destination.

Create a new directory `monitoring/alertmanager`. In this directory create [Dockerfile] (monitoring/alertmanager/Dockerfile) with the following content:
```dockerfile
FROM prom/alertmanager:v0.14.0
COPY config.yml /etc/alertmanager/
```

The Alertmanager settings, as well as Prometheus settings, are set via YAML file or options by string command. In the directory `monitoring/alertmanager` create a file [config.yml](monitoring/alertmanager/config.yml), where you can determine the sending of notifications to YOUR test slag channel.

To send notifications to the slag, create YOUR [Incoming Webhook](https://api.slack.com/messaging/webhooks) [monitoring/alertmanager/config.yml](monitoring/alertmanager/config.yml). A slack application `vscoders alertmanager` was created.
```yaml
---
global:
  slack_api_url: "https://hooks.slack.com/services/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"

The route:
  receiver: "slack-notifications"

receivers:
  - name: "slack-notifications"
    slack_configs:
      - channel: "#aleksey_koloskov"
```

Let's collect the alertmanager: image for this.

The file [monitoring/alertmanager/docker_build.sh](monitoring/alertmanager/docker_build.sh) was created.

Added Makefiel:
``makefile
###
# alertmanager
###
alertmanager_build:
	./env && \
	cd ./monitoring/alertmanager & bash docker_build.sh

alertmanager_push:
	. ./env && \
	docker push $${USER_NAME}/alertmanager
```

**IMPORTANT** for the `docker push` command to insert the value from the file `./env` into the variable `USER_NAME`, it is necessary to insert exactly **double dollar sign**, because one dollar sign has special purpose in Makefile. Fixed all `*_push` in [Makefile](Makefile). Link to https://community.hpe.com/t5/Languages-and-Scripting/Setting-Environment-variable-in-Makefile/td-p/4127916#.XfVLwHoufRY.

Collecting the alertmanager image

ERS track
``shell
cd monitoring/alertmanager && docker build -t $USER_NAME/alertmanager .
```

The way to make
``shell
make alertmanager_build alertmanager_push
```
Everything's down and running.

Let's add a new service to [docker/docker-compose-monitoring.yml]. Do not forget to add it to the same network as the Prometheus service:
```yaml
Services:
  ...
  alertmanager:
    image: ${USERNAME}/alertmanager
    command:
      - "--config.file=/etc/alertmanager/config.yml".
    ports:
      - 9093:9093
    Networks:
      - reddit_back
```


#### Alert rules

Let's create a file [alerts.yml] (monitoring/prometheus/alerts.yml) in the directory `prometheus`, in which we define conditions at which an alert should trigger and send Alertmanager. We will create a simple alert that will trigger in a situation where one of the monitored systems (endpoint) is not available to collect metrics (in this case, the metric `up` with the label `instance` equal to the name of the endpoint will be zero). Perform a query by `up` metric name in Prometheus web interface to make sure that all endpoints are now available for metrics collection:
``promql
up
```
``log
up{instance="cadvisor:8080",job="cadvisor"} 1.
up{instance="cloudprober:9313",job="cloudprober"} 1
up{instance="comment:9292",job="comment"} 1.
up{instance="localhost:9090",job="prometheus"} 1.
up{instance="node-exporter:9100",job="node"} 1
up{instance="post:5000",job="post"} 1
up{instance="postdb-exporter:9216",job="post_db"} 1
up{instance="ui:9292",job="ui"} 1.
```

[alerts.yml](monitoring/prometheus/alerts.yml)
``Yaml
---
I'm sorry:
  - name: alert.rules
    Rules:
      - alert: InstanceDown
        expr: up == 0
        for: 1m
        The labels:
          severity: page
        annotations:
          description: "{{{$labels.instance }} of job {{{$labels.job}} has been down for more than 1 minute."
          "Instance {{{{$labels.instance}} down."
```

Add the operation of copying this file to Dockerfile: [monitoring/prometheus/Dockerfile](monitoring/prometheus/Dockerfile).
``dockerfile
FROM prom/prometheus:v2.14.0
COPY prometheus.yml /etc/prometheus/
# added
COPY alerts.yml /etc/prometheus/
```


#### prometheus.yml

Add rule information to [prometheus config] (monitoring/prometheus/prometheus.yml)
``Yaml
global:
  scrape_interval: '5s'
...
rule_files:
  - "alerts.yml"

Alerting:
  alertmanagers:
    - scheme: http
      static_configs:
        - targets:
            - "alertmanager:9093"
```

Reassemble the Prometheus image:

Remote Sensing method
``shell
docker build -t $USER_NAME/prometheus .
```

Make method
``shell
make build_prometheus push_prometheus
```


#### Push slack api url to github ERROR

After the Githab, there was a letter from the slag...

> Hi there,
> 
> 
> We recently discovered one or more publicly accessible incoming webhooks associated with the vscoders alertmanager app on Slack, for which you > are listed as a collaborator. This type of public webhook exposure can happen when someone who created or has access to a webhook URL posted it on a public site, such as GitHub or other code-sharing forums.
> 
> Although none of the teams using your app are at risk of data exposure through a webhook, we've invalidated the publicly exposed webhook URLs to prevent unauthorized parties from posting messages into their Slack workspaces. This means that vscoders alertmanager can no longer use these webhooks to post its own messages into their Slack workspaces. We've already reached out to the Slack customers who are using your app to advise them that your app may not work any longer, and that they'll need to reinstall the app on their workspace to continue using it.
> 
> If you have additional questions, you can reply directly to this - our support team is standing by and ready to help.
> 
> 
> -The team at Slack

There's no need to get webhook into Githab! But we'll deal with that later.



#### Alert check

Recreate our Docker monitoring infrastructure (again, why?):

Remote sensing method
``shell
docker-compose -f docker-compose-monitoring.yml down
docker-compose -f docker-compose-monitoring.yml up -d
```

The method of making
``shell
make run
```

You can see the alerts in the Prometheus web interface: 

**Trouble** No alerting rules defined. 

Let's try to recreate the monitoring infrastructure after all... To no avail.

Fixed assembly of mongodb_exporter in Makefile.
``makefile
...
MONGODB_EXPORTER_DOCKER_IMAGE_NAME?=$${USER_NAME}/mongodb-exporter
...
mongodb_exporter_docker_build: mongodb_exporter_clone
	. ./env && \
	...

mongodb_exporter_push:
	. ./env && \
	...
```

Fixing the alerts:

For starters, let's lower the perpeteus to the version from RS `v2.1.0`... Didn't give any results.

I was working in the local docker instead of the dokcer-machine instance in gcp... Something like that.

I returned the version of prometheus `v2.14.0`...

I re-created the monitoring:
``shell
docker-compose -f docker-compose-monitoring.yml down
docker-compose -f docker-compose-monitoring.yml up -d
```

**URA!!** Everything works, alert rules are displayed)).


#### Fix the slack

First we'll fix the notifications in slack. To avoid blocking, you will have to pass webhook url through the environment variable. 

Searches over the Internet have not resulted in a suitable solution for this task. In Prode, you can use Hashicorp Vault to store secrets.

We will pass the secret in the environment variable when building the image.

#### implementation

A file [monitoring/alertmanager/env] containing slack api url has been created.
``shell
export SLACK_API_URL="https://hooks.slack.com/services/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" # here is fake slack_api_url. DO NOT FORGET to set correct url!
export SLACK_CHANNEL="#channel_here"
```

The file [monitoring/cloudprober/docker_build.sh](monitoring/cloudprober/docker_build.sh) is as follows
``shell
#!/bin/bash
set -eu

# We get the variables from the ./env file
. ./env
# Frame the values of the environment variables in the config template and write the result to a file
cat config.yml.template | envsubst > config.yml
# Collecting the image
docker build -t $USER_NAME/alertmanager .
# For security reasons, we delete the resulting config file
rm config.yml
```

The file `monitoring/alertmanager/config.yml` has been renamed to [monitoring/alertmanager/config.yml.template] and is listed as follows
``Yaml
---
global:
  slack_api_url: "${SLACK_API_URL}".

The route:
  receiver: "slack-notifications"

receivers:
  - name: "slack-notifications"
    slack_configs:
      - channel: "${SLACK_CHANNEL}"
```

Generating a new slack webhook. We prescribe it in `monitoring/alertmanager/env`.

Collecting alertmanager
``shell
make alertmanager_build
```

We apply .
``shell
make run
```


#### Alert check

We'll stop one of the services and wait a minute.

**Notification came in the slag!!!** =)))))))))))

The Alertmanager also has its own web interface available on port 9093, which we have written into the compose file.

P.S. You can check the operation of web hook slags with the usual curl.


### completion of work

Push
``shell
make push
```

Docker hub link https://hub.docker.com/u/vscoder.

### project launch

#### Preparations

It is preliminary necessary to fill in the files `./env` and `./monitoring/alertmanager/env` for example `env.example` in corresponding directories, and also to execute authorization in `gcloud`.

``shell
# Installing docker-machine
install_docker_machine

# Creating docker-machine
docker_machine_create

# The use of docker-machine
eval $(docker-machine env docker-host)

# Find out about docker-machine ip
make docker_machine_ip
```

#### project launch

``shell
# Assembling images (it's not necessary, must come from docker-hub)
make build

# Application launcher
make run
```

Annex: http://<IP_OF_DOCKER_MACHINE_INSTANCE_OR_LOCALHOST>:9292.

Prometheus: http://<IP_OF_DOCKER_MACHINE_INSTANCE_OR_LOCALHOST>:9090/graph?g0.range_input=1h&g0.expr=(rate(total%5B1m%5D)%20-%20rate(success%5B1m%5D))%20%2F%20rate(total%5B1m%5D)&g0. tab=0&g1.range_input=1h&g1.expr=rate(latency%5B1m%5D)%20%2F%20rate(success%5B1m%5D)%20%2F%201000&g1.tab=0

Grafana: http://<IP_OF_DOCKER_MACHINE_INSTANCE_OR_LOCALHOST>:3000


### Fix travis-ci test

To pass tests, added file [monitoring/alertmanager/config.yml] (monitoring/alertmanager/config.yml). The content of the file is replaced during the build.


### Tasks from \*.


#### Makefile

If you have implemented Makefile in the past, add the build and publication of services added to it;

It's made in the process


#### Collecting metrics from docker

In Docker in experimental mode, metrics recoil in Prometheus format is implemented. Add the collection of these metrics in Prometheus. Compare the number of metrics with Cadvisor. Select a ready-made dashboard or create your own data source for it. Download it to the monitoring/grafana/dashboards;

https://docs.docker.com/config/thirdparty/prometheus/.

TODO: do


#### Telegraf

You can also use Telegraf from InfluxDB to collect metrics from the Docker demon. Add these metrics collection to Prometheus. Compare the number of metrics with Cadvisor. Select a ready-made dashboard or create your own data source for it. Download it to the monitoring/grafana/dashboards;

TODO: do


#### Alertmanager email

Think of and implement other alerts, for example 95 percent of the UI response time discussed above; Configure the integration of Alertmanager with e-mail besides the slack;

TODO: do


### Tasks from \*\*

#### Automatic Grafana Deployment

In Grafana 5.0, the ability to describe data sources and dashboards in configuration files was added. Implement automatic addition of data source and dashboards created in this RS to the graph;

TODO: do


#### Stackdriver

Implement the collection of metrics with Stackdriver, in PR describe what metrics were collected;

TODO: do


#### Their metrics

Think up your application/business metrics and implement them in the application code. Describe in PR what was added;

TODO: do


### Tasks from \*\*\*

#### Tickster

Implement a scheme with proxying requests from Grafana to Prometheus via Trickster, caching proxies from Comcast;

TODO: do


#### Automatic problem fixing

Using the Autoheal + AWX bundle, implement automatic problem correction (e.g. restart of one of the microservices in a fall);

> - Autoheal - project of the OpenShift team for automatic fixing of problems based on alerts results;
> - AWX - open source version of Ansible Tower, you can install it either manually or using one of the ready-made roles, [for example] (https://github.com/geerlingguy/ansible-role-awx);

Create additional folders in the monitoring directory.

TODO: do



## HomeWork 18: Logging and distributed tracing

### Plan

- Collection of unstructured logs
- Log Visualization
- Collecting structured logs
- Distributed tracing


### Preparations

The microservices code has been updated to add logging functionality. New version of access code by [link] (https://github.com/express42/reddit/tree/logging).

- Update the code in the **/src** directory of your repository from the code above. (old `./src' renamed to `./src.microservices').
  ``shell
  # Rename old ./src
  mv ./src ./src.microservices
  # Copy Dockerfile and Makefile
  cp ./src.microservices/comment/Dockerfile ./src/comment/
  cp ./src.microservices/post-py/Dockerfile ./src/post-py/
  cp ./src.microservices/ui/Dockerfile ./src/ui/
  cp ./src.microservices/Makefile ./src/
  # Move old ./src outside the project
  mv ./src.microservices ../
  ```
- If you are using python-alpine, add `gcc` and `musl-dev` packages to **/src/post-py/Dockerfile** (replace `build-base` with `gcc` and `musl-dev`).
  ``dockerfile
  ...
  RUN apk add --no-cache --virtual .build-deps gcc musl-dev \ .
    && pip install --no-cache-dir -r $APP_HOME/requirements.txt \.
    && apk del .build-deps
  ...
  ```
- Build images using the scripts docker_build.sh in the directory of each service
  Remote Sensing method
  ``shell
  for i in ui post-py comment; do cd src/$i; bash docker_build.sh; cd -; done
  ```
  The method of making
  ```
  make build_ui build_post build_comment
  ```

Warning! In this RS we use separate tags for application containers :logging


#### Preparations for the environment

Remote Sensing method
``shell
export GOOGLE_PROJECT=_your project_

docker-machine create --driver google \.
    --google-machine-image https://www.googleapis.com/compute/v1/projects/ubuntu-os-cloud/global/images/family/ubuntu-1604-lts \.
    --google-machine-type n1-standard-1 \.
    --google-open-port 5601/tcp \
    --google-open-port 9292/tcp \
    --google-open-port 9411/tcp \
    logging

# configure local env
eval $(docker-machine env logging)

# find out the IP address
docker-machine ip logging
```

The Make method is not very suitable in this case as it requires manual opening of firewall ports. So let's add a Makefile.
``makefile
###
# docker-machine logging
###
docker_machine_create_logging:
	${DOCKER_MACHINE} create --driver google \.
		--google-machine-image https://www.googleapis.com/compute/v1/projects/ubuntu-os-cloud/global/images/family/ubuntu-1604-lts \.
		--google-machine-type n1-standard-1 \.
		--google-open-port 5601/tcp \
		--google-open-port 9292/tcp \
		--google-open-port 9411/tcp \
		logging
	${DOCKER_MACHINE} env logging

docker_machine_rm_logging:
	make docker_machine_rm DOCKER_MACHINE_NAME=logging.

docker_machine_ip_logging:
	make docker_machine_ip DOCKER_MACHINE_NAME=logging.
```

So, the Make method
``shell
make docker_machine_create_logging docker_machine_ip_logging
```


### Logging Container Docker

#### Elastic Stack

As mentioned in the lecture, all logs should be stored centrally: on one (several) servers. In this SK we will consider an example of a centralized logging system based on the Elastic Stack (formerly known as ELK): which includes 3 core components:
- ElasticSearch (TSDB and storage search engine).
- Logstash (for data aggregation and transformation)
- Kibana (for visualization)

However, for log aggregation instead of Logstash, we'll use Fluentd, thus obtaining another popular combination of these tools called EFK.

### docker-compose-logging.yml

Let's create a separate compose file for our logging system in `docker/` folder.

[docker/docker-compose-logging.yml](docker/docker-compose-logging.yml)
``Yaml
---
version: "3"
Services:
  fluentd:
    image: ${USERNAME}/fluentd
    ports:
      - "24224:24224"
      - "24224:24224/udp."

  Oh..:
    image: elasticsearch:7.4.0
    expose:
      - 9200
    ports:
      - "9200:9200"

  kibana:
    image: kibana:7.4.0
    ports:
      - "5601:5601"
```

#### Fluentd

Fluentd is a tool that can be used to send, aggregate and convert log messages. We will use Fluentd to aggregate (collect in one place) and parse the logs services of our application.

We will create a Fluentd image with the configuration we need.

Create a directory of `logging/fluentd` in your microservices project.

In the created directories, create a simple `Dockerfile` with the following content:

[logging/fluentd/Dockerfile](logging/fluentd/Dockerfile)
``dockerfile
FROM fluent/fluentd:v0.12
RUN gem install fluent-plugin-elasticsearch --no-rdoc --no-ri --version 1.9.5
RUN gem install fluent-plugin-grok-parser --no-rdoc --no-ri --version 1.0.0
ADD fluent.conf /fluentd/etc
```

In the directory `logging/fluentd` create a configuration file:

[logging/fluentd/fluent.conf](logging/fluentd/fluent.conf)
``xml
<source>
  @type forward
  port 24224
  bind 0.0.0.0
</source>

<match *.**>
  @type copy
  <store>
    @type elasticsearch
    host elasticsearch
    port 9200
    logstash_format true
    logstash_prefix fluentd
    logstash_dateformat %Y%m%d
    include_tag_key true
    type_name access_log
    tag_key @log_name
    flush_interval 1s
  </store>
  <store>
    @type stdout
  </store>
</match>
```

Gather a docker image for `fluentd`.

From the `logging/fluentd` directory.

ERS track
``shell
docker build -t $USER_NAME/fluentd .
```

Well, we'll create [logging/fluentd/docker_build.sh](logging/fluentd/docker_build.sh).
``shell
#!/bin/bash
set -eu

docker build -t $USER_NAME/fluentd .
```
and Makefile targets
``shell
###
# fluentd
###
fluentd_build:
	. ./env && \
	cd ./logging/fluentd & bash docker_build.sh

fluentd_push:
	. ./env && \
	docker push $${USER_NAME}/fluentd
```

And only now will we collect the image
``shell
make fluentd_build fluentd_push
```


### Structured logs

The logs must have a specified (unified) structure and contain information about the service's operation necessary for normal operation.

Log messages must also have a format understandable for the selected logging system in order to avoid unnecessary spending of resources on data conversion to the required form. We will consider structured logs on the example of the post service.

We will correct the [.env](docker/.env) file and change the tags of our application to logging.
``shell
...
UI_VERSION=logging
UI_APP_HOME=/app
UI_PORT=9292
POST_VERSION=logging
POST_APP_HOME=/app
COMMENT_VERSION=logging
COMMENT_APP_HOME=/app
...
```

Run application services
``shell
make build
cd docker/ && docker-compose up -d
```

And run the command to view the logs of the post service:
``shell
docker-compose logs -f post
```
``log
Attaching to docker_post_1
post_1 | {"addr": "172.19.0.2", "event": "request", "level": "info", "method": "GET", "path": "/healthcheck?", "request_id": null, "response_status": 200, "service": "post", "timestamp": "2019-12-17 04:50:50" }
post_1 | {"addr": "172.19.0.2", "event": "request", "level": "info", "method": "GET", "path": "/healthcheck?", "request_id": null, "response_status": 200, "service": "post", "timestamp": "2019-12-17 04:50:55" }
post_1 | {"addr": "172.19.0.2", "event": "request", "level": "info", "method": "GET", "path": "/healthcheck?", "request_id": null, "response_status": 200, "service": "post", "timestamp": "2019-12-17 04:51:00" }
post_1 | {"addr": "172.19.0.2", "event": "request", "level": "info", "method": "GET", "path": "/healthcheck?", "request_id": null, "response_status": 200, "service": "post", "timestamp": "2019-12-17 04:51:05" }
post_1 | {"addr": "172.19.0.2", "event": "request", "level": "info", "method": "GET", "path": "/healthcheck?", "request_id": null, "response_status": 200, "service": "post", "timestamp": "2019-12-17 04:51:10" }
post_1 | {"addr": "172.19.0.2", "event": "request", "level": "info", "method": "GET", "path": "/healthcheck?", "request_id": null, "response_status": 200, "service": "post", "timestamp": "2019-12-17 04:51:15" }
```

Warning! Among the logs you can see problems with the availability of Zipkin, we have not yet installed it. Errors can be ignored. [Github issue](https://github.com/express42/reddit/issues/2)

Open the application in your browser and create several posts, watch how the logs are written in the terminal.
``log
post_1 | {"addr": "172.19.0.2", "event": "request", "level": "info", "method": "GET", "path": "/healthcheck?", "request_id": null, "response_status": 200, "service": "post", "timestamp": "2019-12-17 04:53:20" }
post_1 | {"event"}: "find_all_posts", "level": "info", "message": "Successfully retrieved all posts from the database", "params": {}, "request_id": "0f6cf007-a51a-4d42-b8eb-5c6f51fdc605", "service": "post", "timestamp": "2019-12-17 04:53:22" }.
post_1 | {"addr": "172.19.0.2", "event": "request", "level": "info", "method": "GET", "path": "/posts?", "request_id": "0f6cf007-a51a-4d42-b8eb-5c6f51fdc605", "response_status": 200, "service": "post", "timestamp": "2019-12-17 04:53:22" }
post_1 | {"addr": "172.19.0.2", "event": "request", "level": "info", "method": "GET", "path": "/healthcheck?", "request_id": "0f6cf007-a51a-4d42-b8eb-5c6f51fdc605", "response_status": 200, "service": "post", "timestamp": "2019-12-17 04:53:25" }
post_1 | {"addr": "172.19.0.2", "event": "request", "level": "info", "method": "GET", "path": "/healthcheck?", "request_id": "0f6cf007-a51a-4d42-b8eb-5c6f51fdc605", "response_status": 200, "service": "post", "timestamp": "2019-12-17 04:53:30" }
post_1 | {"event"}: "find_all_posts", "level": "info", "message": "Successfully retrieved all posts from the database", "params": {}, "request_id": "f1d68a4f-c685-4585-abb0-570276e21812", "service": "post", "timestamp": "2019-12-17 04:53:30" }.
post_1 | {"addr": "172.19.0.2", "event": "request", "level": "info", "method": "GET", "path": "/posts?", "request_id": "f1d68a4f-c685-4585-abb0-570276e21812", "response_status": 200, "service": "post", "timestamp": "2019-12-17 04:53:30" }
post_1 | {"event"}: "find_all_posts", "level": "info", "message": "Successfully retrieved all posts from the database", "params": {}, "request_id": "0da9978b-80cb-4b32-b56f-096fb8ed72b8", "service": "post", "timestamp": "2019-12-17 04:53:31" }.
post_1 | {"addr": "172.19.0.2", "event": "request", "level": "info", "method": "GET", "path": "/posts?", "request_id": "0da9978b-80cb-4b32-b56f-096fb8ed72b8", "response_status": 200, "service": "post", "timestamp": "2019-12-17 04:53:31" }
post_1 | {"event"}: "find_all_posts", "level": "info", "message": "Successfully retrieved all posts from the database", "params": {}, "request_id": "a7d06d49-1e67-40e4-b8b2-d83c21930257", "service": "post", "timestamp": "2019-12-17 04:53:32" }.
post_1 | {"addr": "172.19.0.2", "event": "request", "level": "info", "method": "GET", "path": "/posts?", "request_id": "a7d06d49-1e67-40e4-b8b2-d83c21930257", "response_status": 200, "service": "post", "timestamp": "2019-12-17 04:53:32" }
post_1 | {"event"}: "find_all_posts", "level": "info", "message": "Successfully retrieved all posts from the database", "params": {}, "request_id": "bed17527-4202-4054-a124-87e800362971", "service": "post", "timestamp": "2019-12-17 04:53:32" }.
post_1 | {"addr": "172.19.0.2", "event": "request", "level": "info", "method": "GET", "path": "/posts?", "request_id": "bed17527-4202-4054-a124-87e800362971", "response_status": 200, "service": "post", "timestamp": "2019-12-17 04:53:32" }
post_1 | {"addr": "172.19.0.2", "event": "request", "level": "info", "method": "GET", "path": "/healthcheck?", "request_id": "bed17527-4202-4054-a124-87e800362971", "response_status": 200, "service": "post", "timestamp": "2019-12-17 04:53:35" }
```

Each event related to the work of our application is logged in JSON format and has the necessary structure: event type, message, params, service name, etc.


#### Sending logs to Fluentd

As noted in the lecture, by default Docker containers use the json-file driver to log information that is written by the service inside the container to stdout (and stderr). To send logs to Fluentd, use the docker driver [fluentd] (https://docs.docker.com/engine/admin/logging/fluentd/).

Let's define the driver for logging for the post service inside a compose file:

[docker/docker-compose.yml](docker/docker-compose.yml)
``Yaml
version: '3'
Services:
  post:
    image: ${USER_NAME}/post
    Environment:
      - POST_DATABASE_HOST=post_db
      - POST_DATABASE=posts
    Depend_on:
      - post_db
    ports:
      - "5000:5000"
    logging:
      driver: "fluentd"
      Okay:
        fluentd-address: localhost:24224
        tag: service.post
```


#### Loggathering Post service

Let's raise the infrastructure of the centralized logging system and restart the application services. From the docker directory:

Remote Sensing method
``shell
docker-compose -f docker-compose-logging.yml up -d
docker-compose down
docker-compose up -d
```

But we'll create a Makefile...
``makefile
###
# app down
###
down_app:
	cd docker \
	&& ../.venv/bin/docker-compose down

down_monitoring:
	cd docker \
	&& ../.venv/bin/docker-compose -f docker-compose-monitoring.yml down

down_logging:
	cd docker \
	&& ../.venv/bin/docker-compose -f docker-compose-logging.yml down


###
# run
###
run_app variables:
	cd docker \
	&& ../.venv/bin/docker-compose up -d

run_monitoring: variables
	cd docker \
	&& ../.venv/bin/docker-compose -f docker-compose-monitoring.yml up -d

run_logging: variables
	cd docker \
	&& ../.venv/bin/docker-compose -f docker-compose-logging.yml up -d
```

And now the Make method
``shell
make_logging down_app run_app
```

Let's create some posts in the application:


#### Kibana

Kibana is a tool for log visualization and analysis from Elastic.

Let's open the Kibana WEB-interface for viewing the logs collected in ElasticSearch Post service (kibana listens on port 5601).

It's a mistake: 
> Kibana server is not ready yet

See the list of running containers
``shell
cd ./docker && docker-compose -f docker-compose-logging.yml ps
```
``log
         Name Command State Ports                            
--------------------------------------------------------------------------------------------------------------------------------
docker_elasticsearch_1 /usr/local/bin/docker-entr ...   Exit 78                                                               
docker_fluentd_1 tini -- /bin/entrypoint.sh ...   Up 0.0.0.0:24224->24224/tcp, 0.0.0.0:24224->24224/udp, 5140/tcp
docker_kibana_1 /usr/local/bin/dumb-init - ...   Up 0.0.0.0:5601->5601/tcp
```

See the ES logs.
``shell
docker-compose -f docker-compose-logging.yml logs elasticsearch
```
``log
...
elasticsearch_1 | {"type": "server", "timestamp": "2019-12-17T05:10:21,661Z", "level": "INFO", "component": "o.e.n.Node", "cluster.name": "docker-cluster", "node.name": "fd168d3dcd92", "message": "initialized" }
elasticsearch_1 | {"type": "server", "timestamp": "2019-12-17T05:10:21,663Z", "level": "INFO", "component": "o.e.n.Node", "cluster.name": "docker-cluster", "node.name": "fd168d3dcd92", "message": "starting ...". }
elasticsearch_1 | {"type": "server", "timestamp": "2019-12-17T05:10:22,530Z", "level": "INFO", "component": "o.e.t.TransportService", "cluster.name": "docker-cluster", "node.name": "fd168d3dcd92", "message": "publish_address {172.20.0.4:9300}, bound_addresses {0.0.0.0:9300}" }.
elasticsearch_1 | {"type": "server", "timestamp": "2019-12-17T05:10:22,569Z", "level": "INFO", "component": "o.e.b.BootstrapChecks", "cluster.name": "docker-cluster", "node.name": "fd168d3dcd92", "message": "bound or publishing to a non-loopback address, enforcing bootstrap checks" }
elasticsearch_1 | ERROR: [2] bootstrap checks failed
elasticsearch_1 | [1]: max virtual memory areas vm.max_map_count [65530] is too low, increasing to at least [262144].
elasticsearch_1 | [2]: the default discovery settings are unsuitable for production use; at least one of [discovery.seed_hosts, discovery.seed_providers, cluster.initial_master_nodes] must be configured
elasticsearch_1 | {"type": "server", "timestamp": "2019-12-17T05:10:22,632Z", "level": "INFO", "component": "o.e.n.Node", "cluster.name": "docker-cluster", "node.name": "fd168d3dcd92", "message": "stopping ...". }
elasticsearch_1 | {"type": "server", "timestamp": "2019-12-17T05:10:22,677Z", "level": "INFO", "component": "o.e.n.Node", "cluster.name": "docker-cluster", "node.name": "fd168d3dcd92", "message": "stopped" }
elasticsearch_1 | {"type": "server", "timestamp": "2019-12-17T05:10:22,679Z", "level": "INFO", "component": "o.e.n.Node", "cluster.name": "docker-cluster", "node.name": "fd168d3dcd92", "message": "closing ...". }
elasticsearch_1 | {"type": "server", "timestamp": "2019-12-17T05:10:22,752Z", "level": "INFO", "component": "o.e.n.Node", "cluster.name": "docker-cluster", "node.name": "fd168d3dcd92", "message": "closed" }
elasticsearch_1 | {"type": "server", "timestamp": "2019-12-17T05:10:22,756Z", "level": "INFO", "component": "o.e.x.m.p.NativeController", "cluster.name": "docker-cluster", "node.name": "fd168d3dcd92", "message": "Native controller process has stopped - no new native processes can be started". }
```

The search in the slag gave us a solution. Chinim:

We set vm.max_map_count on docker-machine instance.
``shell
docker-machine ssh logging sudo sysctl -w vm.max_map_count=262144
exit
```

Let's update the version and add envionment

[docker-compose-logging.yml] [docker/docker-compose-logging.yml]
``Yaml
Services:
  ...
  elasticsearch:
    image: elasticsearch:7.5.0
    expose:
      - 9200
    ports:
      - "9200:9200"
    Environment:
      - node.name=elasticsearch
      - cluster.name=docker-cluster
      - node.master=true
      - cluster.initial_master_nodes=elasticsearch
      - bootstrap.memory_lock=true
      - "ES_JAVA_OPTS=-Xms1g -Xmx1g".
  ...
```

Restarting logging
``shell
make down_logging run_logging
```

Check out .
``shell
cd ./docker && docker-compose -f docker-compose-logging.yml ps
```
Error
``log
         Name Command State Ports                            
--------------------------------------------------------------------------------------------------------------------------------
docker_elasticsearch_1 /usr/local/bin/docker-entr ...   Exit 78                                                               
docker_fluentd_1 tini -- /bin/entrypoint.sh ...   Up 0.0.0.0:24224->24224/tcp, 0.0.0.0:24224->24224/udp, 5140/tcp
docker_kibana_1 /usr/local/bin/dumb-init - ...   Up 0.0.0.0:5601->5601/tcp
```
``shell
docker-compose -f docker-compose-logging.yml logs elasticsearch
```
``log
elasticsearch_1 | {"type": "server", "timestamp": "2019-12-17T05:31:29,375Z", "level": "WARN", "component": "o.e.b.JNANatives", "cluster.name": "docker-cluster", "node.name": "elasticsearch", "message": "Unable to lock JVM Memory: error=12, reason=Cannot allocate memory" }
elasticsearch_1 | {"type": "server", "timestamp": "2019-12-17T05:31:29,386Z", "level": "WARN", "component": "o.e.b.JNANatives", "cluster.name": "docker-cluster", "node.name": "elasticsearch", "message": "This can result in part of the JVM being swapped out." }
elasticsearch_1 | {"type": "server", "timestamp": "2019-12-17T05:31:29,388Z", "level": "WARN", "component": "o.e.b.JNANatives", "cluster.name": "docker-cluster", "node.name": "elasticsearch", "message": "Increase RLIMIT_MEMLOCK, soft limit: 65536, hard limit: 65536". }
elasticsearch_1 | {"type": "server", "timestamp": "2019-12-17T05:31:29,390Z", "level": "WARN", "component": "o.e.b.JNANatives", "cluster.name": "docker-cluster", "node.name": "elasticsearch", "message": "These can be adjusted by modifying /etc/security/limits.conf, for example: \n\t# allow user 'elasticsearch' mlockall\n\telasticsearch soft memlock unlimited\n\telasticsearch hard memlock unlimited" }
elasticsearch_1 | {"type": "server", "timestamp": "2019-12-17T05:31:29,397Z", "level": "WARN", "component": "o.e.b.JNANatives", "cluster.name": "docker-cluster", "node.name": "elasticsearch", "message": "If you are logged in interactively, you will have to re-login for the new limits to take effect." }
...
elasticsearch_1 | ERROR: [1] bootstrap checks failed
elasticsearch_1 | [1]: memory locking requested for elasticsearch process but memory is not locked
```
Partly helped to find the problem was the discussion on [link] (https://discuss.elastic.co/t/elasticsearch-is-not-starting-when-bootstrap-memory-lock-is-set-to-true/120962/2).


##### memory locking requested for elasticsearch process but memory is not locked

Right `/etc/security/limits.conf` on docker-machine.
``shell
docker-machine ssh logging
echo elasticsearch soft memlock unlimited | sudo tee /etc/security/limits.conf
echo elasticsearch hard memlock unlimited | sudo tee /etc/security/limits.conf
exit
```

Raise the logging.
``shell
make down_logging run_logging
```

The result is the same.

After some wanderings, the solution is found at https://github.com/deviantony/docker-elk/issues/243.

Limits added to service
``Yaml
ulimits:
  memlock:
    soft: -1
    hard: -1
```

The final [docker/docker-compose-logging.yml](docker/docker-compose-logging.yml)
``Yaml
---
version: "3"
Services:
  fluentd:
    image: ${USERNAME}/fluentd
    ports:
      - "24224:24224"
      - "24224:24224/udp."

  Oh..:
    image: elasticsearch:7.5.0
    expose:
      - 9200
    ports:
      - "9200:9200"
    Environment:
      - node.name=elasticsearch
      - cluster.name=docker-cluster
      - node.master=true
      - cluster.initial_master_nodes=elasticsearch
      - bootstrap.memory_lock=true
      - "ES_JAVA_OPTS=-Xms1g -Xmx1g".
    ulimits:
      memlock:
        soft: -1
        hard: -1

  kibana:
    image: kibana:7.5.0
    ports:
      - "5601:5601"
```

##### Kibana sequel

Let's open the Kibana WEB-interface for viewing ElasticSearch collected Post service logs (kibana listens on port 5601) http://34.66.31.172:5601.

1. Discover
2. Configure an index pattern `fluentd-*.
3. Next.
4. Time Filter field name `@timestamp`.
5. Next.
6. Discover .

Then you can play with the interface, see the logs.

We see the log message, which we have recently observed in the terminal. Now these log messages are stored centrally in ElasticSearch. We also see additional information about where this log came from.

Note that the names in the left column are called fields. Fields can be searched to quickly find the information you need.

You can enter an arbitrary expression in the search field to see some examples of the search.

For example, by looking at the list of available fields, we can search for all logs from the `reddit_post_1' container.

Note that the log field contains a JSON object which contains a lot of information interesting to us.
``json
{"addr": "172.22.0.3", "event": "request", "level": "info", "method": "GET", "path": "/healthcheck?", "request_id": "07585bd8-ca1f-473f-ae72-21f3d08f0d5d", "response_status": 200, "service": "post", "timestamp": "2019-12-17 06:24:16" }
```

We would like to highlight this information in the fields in order to be able to search them. For example, to find all logs associated with a particular event or service.

We can achieve this by using **filters** to highlight the information we need.


#### Filters

Let's add a filter for parsing json logs coming from the post service to the fluentd config.

[logging/fluentd/fluent.conf] (logging/fluentd/fluent.conf)
``xml
<source>
   @type forward
   port 24224
   bind 0.0.0.0
</source>

<filter service.post>
   @type parser
   format json
   key_name log
</filter>

<match *.**>
   @type copy
...
```

Then reassemble the image and restart the fluentd service.

Remote Sensing method
``shell
logging/fluentd $ docker build -t $USER_NAME/fluentd
docker/ $ docker-compose -f docker-compose-logging.yml up -d fluentd
```

But we have fewer letters. The Make method.
``shell
make fluentd_build run_logging
```

Let's turn to Kibana again. Before we look at the logs, let's make sure that the time interval is selected correctly. Click once on the date with the time. It's set correctly!

Let's take a look at one of the messages and see that instead of one log field there are many fields with the information we need... Well, it's not!

The update of fluentd and its plug-ins

[logging/fluentd/Dockerfile] (logging/fluentd/Dockerfile)
``dockerfile
FROM fluent/fluentd:v1.8
USER root
RUN fluent-gem install fluent-plugin-elasticsearch --no-rdoc --no-ri --version 3.7.1
RUN fluent-gem install fluent-plugin-grok-parser --no-rdoc --no-ri --version 2.6.1.
ADD fluent.conf /fluentd/etc
USER fluent
```

Let's look at one of the messages again and see that instead of one log field there are many fields with the information we need!

For example, let's search the event of creating a new post: `event: post_create`.

There are 2 posts that were created after setting up the filter.


### Unstructured logs

Unstructured logs are distinguished by the lack of a clear data structure. It also often happens that the format of log messages is not adapted to the system of centralized logging, which significantly increases the cost of computing and time resources for data processing and allocation of the necessary information.

On the example of the ui service we'll consider an example of logs with an inconvenient message format.


#### Logging of the UI service

By analogy with the post service, let's define the driver for fluentd logging in compose file for the ui service.

[docker/docker-compose.yml](docker/docker-compose.yml)
``Yaml
Services:
  ui:
    environment:
      APP_HOME: ${UI_APP_HOME}
    image: ${USERNAME}/ui:${UI_VERSION}
    ports:
      - ${UI_PORT}:9292/tcp
    Networks:
      - reddit_front
    logging:
      driver: "fluentd"
      Okay:
        fluentd-address: localhost:24224
        tag: service.ui
```

Restart ui service From catalogue `./docker`.

ERS track
```
docker-compose stop ui
docker-compose rm ui
docker-compose up -d
```

The Make path (docker-compose itself to recreate the container)
``shell
make run_app
```
``log
...
Recreating docker_ui_1 ... done
...
```

Let's take a look at the format of the messages we collect
``log
I, [2019-12-17T18:15:04.146453 #1] INFO -- : service=ui | event=show_all_posts | request_id=bf36de91-bf97-4d97-b15a-c66dec6ee581 | message='Successfully showed the home page with posts' | params: "{}".
```


### Parsing

When an application or service does not write structured logs, you have to use good old **regular expressions** to parse them in [/docker/fluentd/fluent.conf](/docker/fluentd/fluent.conf).

The following **regular expression** is needed to successfully select the information we are interested in from the UI service log into the fields

[/docker/fluentd/fluent.conf](/docker/fluentd/fluent.conf)
``xml
source>
  @type forward
  port 24224
  bind 0.0.0.0
</source>

<filter service.post>
  @type parser
  format json
  key_name log
</filter>

<filter service.ui>
  @type parser
  format /\[(?<time>[^\]]*)\] (?<level>\S+) (?<user>\S+)[\W]*service=(?<service>\S+)[\W]*event=(?<event>\S+)[\W]*(?path=(?<path>\S+)[\W]*?request_id=(?<request_id>\S+)[\W]*(?? :remote_addr=(?<remote_addr>\S+)[\W]*)?(?:method= (?<method>\S+)[\W]*)?(?:response_status=(?<response_status>\S+)[\W]*)?(?:message='(?<message>[^\']*)[\W]*)?
  key_name log
</filter>


<match *.**>
  @type copy
  <store>
    @type elasticsearch
    host elasticsearch
    port 9200
    logstash_format true
    logstash_prefix fluentd
    logstash_dateformat %Y%m%d
    include_tag_key true
    type_name access_log
    tag_key @log_name
    flush_interval 1s
  </store>
  <store>
    @type stdout
  </store>
</match>
```

#### Restarting logging

Let's update fluentd and restart logging.
``shell
make fluentd_build run_logging
```


#### Parsing

The result should look like this... Something's not good, there's a message flying into the elastics:
``json
{
  "_index": "fluentd-20191217."
  "_type": "access_log."
  "_id": "GgYWFW8B0lVuIA-sb4VL",
  "_version." 1,
  "_score": null,
  "_source." {
    "worker": 0,
    "message": "fluentd worker is now stopping worker=0",
    "@timestamp": "2019-12-17T18:19:49.446032292+00:00."
    "@log_name": "fluent.info"
  },
  "fields." {
    "@timestamp." [
      "2019-12-17T18:19:49.446Z."
    ]
  },
  "sort." [
    1576606789446
  ]
}
```

Our fluent has fallen.
``shell
cd ./docker && docker-compose -f docker-compose-logging.yml logs -f fluentd; cd -
```
``log
Attaching to docker_fluentd_1
fluentd_1 | /usr/lib/ruby/gems/2.5.0/gems/fluentd-1.8.0/lib/fluent/config/basic_parser.rb:92:in `parse_error!': unmatched end tag at fluent.conf line 6.1 (Fluent::ConfigParseError).
fluentd_1 | 5: </source>
fluentd_1 | 6: 
fluentd_1 | 
fluentd_1 | -^
fluentd_1 | 7: <filter service.post>
fluentd_1 | from /usr/lib/ruby/gems/2.5.0/gems/fluentd-1.8.0/lib/fluent/config/v1_parser.rb:78:in `parse_element'.
fluentd_1 | from /usr/lib/ruby/gems/2.5.0/gems/fluentd-1.8.0/lib/fluent/config/v1_parser.rb:43:in `parse!'.
fluentd_1 | from /usr/lib/ruby/gems/2.5.0/gems/fluentd-1.8.0/lib/fluent/config/v1_parser.rb:33:in `parse'.
fluentd_1 | from /usr/lib/ruby/gems/2.5.0/gems/fluentd-1.8.0/lib/fluent/config.rb:39:in `parse'.
fluentd_1 | from /usr/lib/ruby/gems/2.5.0/gems/fluentd-1.8.0/lib/fluent/supervisor.rb:779:in `read_config'.
fluentd_1 | from /usr/lib/ruby/gems/2.5.0/gems/fluentd-1.8.0/lib/fluent/supervisor.rb:561:in `configure'.
fluentd_1 | from /usr/lib/ruby/gems/2.5.0/gems/fluentd-1.8.0/lib/fluent/command/fluentd.rb:329:in `<top (required)>'.
fluentd_1 | from /usr/lib/ruby/2.5.0/rubygems/core_ext/kernel_require.rb:59:in `require'.
fluentd_1 | from /usr/lib/ruby/2.5.0/rubygems/core_ext/kernel_require.rb:59:in `require'.
fluentd_1 | from /usr/lib/ruby/gems/2.5.0/gems/fluentd-1.8.0/bin/fluentd:8:in `<top (required)>'.
fluentd_1 | from /usr/bin/fluentd:23:in `load'.
fluentd_1 | from /usr/bin/fluentd:23:in `<main>'.
docker_fluentd_1 exited with code 1
```
Cause: <<before the opening tag <source>>.

Fixed: [/docker/fluentd/fluent.conf](/docker/fluentd/fluent.conf)
``xml
<source>
  @type forward
  port 24224
  bind 0.0.0.0
</source>

<filter service.post>
  @type parser
  format json
  key_name log
</filter>

<filter service.ui>
  @type parser
  format /\[(?<time>[^\]]*)\] (?<level>\S+) (?<user>\S+)[\W]*service=(?<service>\S+)[\W]*event=(?<event>\S+)[\W]*(?path=(?<path>\S+)[\W]*?request_id=(?<request_id>\S+)[\W]*(?? :remote_addr=(?<remote_addr>\S+)[\W]*)?(?:method= (?<method>\S+)[\W]*)?(?:response_status=(?<response_status>\S+)[\W]*)?(?:message='(?<message>[^\']*)[\W]*)?
  key_name log
</filter>


<match *.**>
  @type copy
  <store>
    @type elasticsearch
    host elasticsearch
    port 9200
    logstash_format true
    logstash_prefix fluentd
    logstash_dateformat %Y%m%d
    include_tag_key true
    type_name access_log
    tag_key @log_name
    flush_interval 1s
  </store>
  <store>
    @type stdout
  </store>
</match>
```
``shell
make fluentd_build run_logging
```

Now much better: the message in the elastics
`json
{
  "_index": "fluentd-20191217."
  "_type": "access_log."
  "_id": "1QYdFW8B0lVuIA-ssYXr",
  "_version." 1,
  "_score": null,
  "_source." {
    "level." "INFO."
    "user." "--",
    "service": "ui."
    "event." "request."
    "path": "/"
    "request_id": "55504441-6aac-43cf-b22e-006811a30b89",
    "remote_addr": "185.30.195.250."
    "method": "GET."
    "response_status." "200",
    "@timestamp": "2019-12-17T18:27:43.382932000+00:00."
    "@log_name": "service.ui"
  },
  "fields." {
    "@timestamp." [
      "2019-12-17T18:27:43.382Z."
    ]
  },
  "sort." [
    1576607263382
  ]
}
```

The created regulators may have errors, are difficult to change and cannot be read. To facilitate the parsing task, you can use **grok**-templates instead of standard ones. In essence, **grok**'s are named regular expression templates (very similar to functions). You can use a ready-made regexp by simply referring to it as a function

[docker/fluentd/fluent.conf] (docker/fluentd/fluent.conf)
``xml
...
<filter service.ui>
   @type parser
   format grok
   grok_pattern %{RUBY_LOGGER}
   key_name log
</filter>
...
```

It's a grok pattern sewn into a fluentd plugin. When unfolded, it looks like this:
``grok
%{RUBY_LOGGER} [((??<timestamp>?>\d\d){1,2}-(?:0?1-9]|1[0-2])-(?:(?:0[1-9])|(??:[12][0-9])|(?:3[01])|[1-9])[T ](?2[0123]|[01]?[0-9]):? (?:[0-5][0-9])(?::?(?:(?:[0-5]?[0-9]|60)(?:[:.,][0-9]+)?))?(?:Z|[+-](?:2[0123]|[01]?[0-9])(?::?(?:[0-5][0-9])))?) #(?<pid>\b(?:[1-9][0-9]*)\b)\]. *(?<loglevel>(?:DEBUG|FATAL|ERROR|WARN|INFO)). -- +??<progname>.*?): (?<message>.*)
```

As you could see on the previous slide, some of the logs need to be expanded. To do this, we'll use a few Grok's in turn.

[docker/fluentd/fluent.conf] (docker/fluentd/fluent.conf)
``xml
<source>
  @type forward
  port 24224
  bind 0.0.0.0
</source>

<filter service.post>
  @type parser
  format json
  key_name log
</filter>

<filter service.ui>
  @type parser
  key_name log
  format grok
  grok_pattern %{RUBY_LOGGER}
</filter>

<filter service.ui>
  @type parser
  format grok
  grok_pattern service=%{WORD:service} \| event=%{WORD:event} \| request_id=%{GREEDYDATA:request_id} \| message='%{GREEDYDATA:message}'.
  key_name message
  reserve_data true
</filter>

<match *.**>
  @type copy
  <store>
    @type elasticsearch
    host elasticsearch
    port 9200
    logstash_format true
    logstash_prefix fluentd
    logstash_dateformat %Y%m%d
    include_tag_key true
    type_name access_log
    tag_key @log_name
    flush_interval 1s
  </store>
  <store>
    @type stdout
  </store>
</match>
```
``shell
make fluentd_build run_logging
```
Error
``log
Attaching to docker_fluentd_1
fluentd_1 | 2019-12-17 18:34:08 +0000 [info]: parsing config file is succeeded path="/fluentd/etc/fluent.conf".
fluentd_1 | 2019-12-17 18:34:08 +0000 [info]: gem 'fluent-plugin-elasticsearch' version '3.7.1'.
fluentd_1 | 2019-12-17 18:34:08 +0000 [info]: gem 'fluent-plugin-grok-parser' version '2.6.1'.
fluentd_1 | 2019-12-17 18:34:08 +0000 [info]: gem 'fluentd' version '1.8.0'.
fluentd_1 | 2019-12-17 18:34:08 +0000 [error]: config error file="/fluentd/etc/fluent.conf" error_class=Fluent::ConfigError error="no grok patterns. Check configuration, e.g. typo, configuration syntax, etc".
docker_fluentd_1 exited with code 1
```

Dancing m tambourine vokruk this situation (reading ridmi in the repositories of plug-ins, Google and search for suitable issues), led to https://github.com/repeatedly/fluent-plugin-multi-format-parser/issues/6, where to solve the problem recommended to use `v0.12`, which we will do using the latest compatible versions of plug-ins. So our dock file became this:

[logging/fluentd/Dockerfile].
``dockerfile
FROM fluent/fluentd:v0.12
RUN fluent-gem install fluent-plugin-elasticsearch --no-rdoc --no-ri --version 1.18.1
RUN fluent-gem install fluent-plugin-grok-parser --no-rdoc --no-ri --version 1.0.0.
ADD fluent.conf /fluentd/etc
```
Then assembly and depression
``shell
make fluentd_build run_logging
```
Not surprisingly, everything started, including the json parsing from the `post` service.

As a result, we'll get it in Kibana (if we perform actions in ciservice): yes, we got it all right.


### Tasks co ##

#### grok

UI service sends logs in several formats.

``log
service=ui | event=request | path=/ | request_id=96e76ff2-3d06-4ffa-806b-c14d7ca6a78a | remote_addr=185.30.195.250 | method= GET | response_status=200.
```

Such a lair is left undone. Configure fluentd so that both formats of UI service logs (the one before and the current one) are parsed simultaneously.

##### Analysis

We read the documentation at https://github.com/fluent/fluent-plugin-grok-parser/blob/master/README.md.

Parsim ready-made templates https://github.com/fluent/fluent-plugin-grok-parser/tree/master/patterns.

##### Implementation

And we write a config ( handy grok-debagger is in kibana: Dev Tools )

``xml
<filter service.ui>
  @type parser
  format grok
  <grok>
    pattern service=%{WORD:service} \| event=%{WORD:event} \| request_id=%{GREEDYDATA:request_id} \| message='%{GREEDYDATA:message}'.
  </grok>
  <grok>
    pattern service=%{WORD:service} \| event=%{WORD:event} \| path=%{URIPATH:path} \| request_id=%{GREEDYDATA:request_id} \| remote_addr=%{IP:remote_addr} \| method= %{WORD:message} \| response_status=%{INT:response_status}.
  </grok>
  key_name message
  reserve_data true
</filter>
```

It's done. Examples .
`json
{
  "_index": "fluentd-20191217."
  "_type": "access_log."
  "_id": "wgZnFW8B0lVuIA-s_IqS",
  "_version." 1,
  "_score": null,
  "_source." {
    "timestamp": "2019-12-17T19:48:52.681349."
    "pid": "1."
    "loglevel." "INFO."
    "progname": ""
    "message": "Successfully showed the home page with posts."
    "service": "ui."
    "event." "show_all_posts."
    "request_id": "08c3c38a-1725-4b7c-9665-c61e46265219",
    "@timestamp": "2019-12-17T19:48:52+00:00."
    "@log_name": "service.ui"
  },
  "fields." {
    "@timestamp." [
      "2019-12-17T19:48:52.000Z."
    ]
  },
  "sort." [
    1576612132000
  ]
}
```
`json
{
  "_index": "fluentd-20191217."
  "_type": "access_log."
  "_id": "wwZnFW8B0lVuIA-s_IqS",
  "_version." 1,
  "_score": null,
  "_source." {
    "timestamp": "2019-12-17T19:48:52.710553."
    "pid": "1."
    "loglevel." "INFO."
    "progname": ""
    "message": "GET."
    "service": "ui."
    "event." "request."
    "path": "/"
    "request_id": "08c3c38a-1725-4b7c-9665-c61e46265219",
    "remote_addr": "185.30.195.250."
    "response_status." "200",
    "@timestamp": "2019-12-17T19:48:52+00:00."
    "@log_name": "service.ui"
  },
  "fields." {
    "@timestamp." [
      "2019-12-17T19:48:52.000Z."
    ]
  },
  "sort." [
    1576612132000
  ]
}
```


### Distributed tracing

Deal with the topic of distributed trailing and solve the problem at the end of this file.

#### Zipkin

Add to compose file for logging services Zipkin Distributed Trace Service

[docker/docker-compose-logging.yml](docker/docker-compose-logging.yml)
``Yaml
version: '3'

Services:
  zipkin:
    image: openzipkin/zipkin
    ports:
      - "9411:9411"

  ...

  kibana:
    image: kibana
    ports:
      - "8080:5601" # Why 8080???? It's never been like this before... in the composite file, prescribed 5601:5601.
```


### docker-compose.yml

Correct our [docker/docker-compose.yml]([docker/docker-compose.yml]).

Add `ENV` variable support for each service and set the parameterized parameter `ZIPKIN_ENABLED`.

``Yaml
Environment:
   - ZIPKIN_ENABLED=${ZIPKIN_ENABLED}
```

Specify in the `.env` file
``shell
ZIPKIN_ENABLED=true
```

Release the application with the update

Remote Sensing method
``shell
docker-compose up -d
```

Make method
``shell
make run_app
```


#### Networks

Zipkin must be on the same network as the applications, so if you have been doing the job with the networks, you need to declare those networks in [docker-compose-logging.yml](docker/docker-compose-logging.yml) and add zikpkin to them in a similar way:

```yaml
Services:
  ...
  zipkin:
    image: openzipkin/zipkin
    ports:
      - "9411:9411"
    Networks:
      - reddit_front
      - reddit_back

Networks:
  reddit_front:
  reddit_back:
```


#### Re-create our services

Remote Sensing method
``shell
docker-compose -f docker-compose-logging.yml -f docker-compose.yml down
docker-compose -f docker-compose-logging.yml -f docker-compose.yml up -d
```

That's what we'll use (surprise))
P.S. It was necessary to raise the version of the composite file [docker/docker-compose-logging.yml] from `3.0` to `3.3`.
``log
Status: Downloaded newer image for openzipkin/zipkin:latest
Creating docker_kibana_1 ... 
Creating docker_post_db_1 ... 
Creating docker_zipkin_1 ... 
Creating docker_post_1 ... 
Creating docker_kibana_1 ... done  ...
Creating docker_post_db_1 ... done
Creating docker_zipkin_1 ... done

Creating docker_elasticsearch_1 ... done .

Creating docker_fluentd_1 ... done
Creating docker_comment_1 ... done

ERROR: for ui Cannot start service ui: failed to initialize logging driver: dial tcp 127.0.0.1:24224: connect: connection refused

ERROR: for post Cannot start service post: failed to initialize logging driver: dial tcp 127.0.0.1:24224: connect: connection refused
ERROR: Encountered while bringing up the project.
```

Re-starting helped. It looks like the application couldn't start before the zipkin was fully launched.
``shell
docker-compose -f docker-compose-logging.yml -f docker-compose.yml up -d
```
``log
Starting docker_post_1 ... 
docker_elasticsearch_1 is up-to-date
docker_zipkin_1 is up-to-date
Starting docker_ui_1 ... 
docker_kibana_1 is up-to-date
Starting docker_post_1 ... done
Starting docker_ui_1 ... done
Starting docker_comment_1 ... done
```

Let's open Zipkin WEB UI on port 9411, no traces should be found yet, as no requests have been received by our application (it is).

Let's open the main application page and update it several times.

After looking at the Zipkin UI (the page will need to be refreshed), we need to find some traces (traces that left the requests passing through our service system).... Yes, we have.

Click on one of the traces to see how the request went through our microservices system and what the total processing time of the request from our application when requesting the main page.

We see that the first thing our request came to the ui service, which was able to process our request for a total time of **187.566ms**.

Of these **187ms** ms it took **134.155ms** for ui to send a request to the post service on the path `/posts` and get a response from it in the form of a list of posts. The post service in its turn used the function of addressing the database for the list of posts, which took **4.827ms**... Actually, you can't see it in database addressing traces, but let's see what happens next.

Let's repeat the terminology a bit: the blue bars are called **span** with time and represent one operation that took place during the query processing. The set of **span**s is called a trace. The total processing time of our query is equal to the upper **span**-s, which includes the time of all **spans**-s located below it.


### Off Tasks: Problems with comment

``shell
docker-compose ps
```
``log
      Name Command State Ports         
--------------------------------------------------------------------------------
docker_comment_1 puma Exit 1                         
docker_post_1 python3 post_app.py Up                             
docker_post_db_1 docker-entrypoint.sh mongod Up 27017/tcp             
docker_ui_1 puma Up 0.0.0.0:9292->9292/tcp
```

Enable logging for comment

[docker/docker-compose.yml](docker/docker-compose.yml)
``Yaml
Services:
  ...
  comment:
    environment:
      APP_HOME: ${COMMENT_APP_HOME}
      ZIPKIN_ENABLED: ${ZIPKIN_ENABLED}
    image: ${USERNAME}/comment:${COMMENT_VERSION}
    Networks:
      - reddit_front
      - reddit_back
    The links:
      - "post_db:comment_db"
    logging:
      driver: "fluentd"
      Okay:
        fluentd-address: localhost:24224
        tag: service.comment
```

Restart app
``shell
make run_app
```

Look at the logs.
``log
! Unable to load application: TZInfo::DataSourceNotFound: No source of timezone data could be found.
```

Googling. [First link:](https://github.com/tzinfo/tzinfo/wiki/Resolving-TZInfo::DataSourceNotFound-Errors)

Created Issue https://github.com/express42/reddit/issues/9.

Bent the repo. Created a brand `fix-comment` from `logging`. 

Fixed it. Added `gem 'tzinfo-data' to [src/comment/Gemfile] - helped.

Zakommitel. But there's a mistake with the cannon.
``shell
git push
```
``log
ERROR: Permission to express42/reddit.git denied to vscoder.
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
```

Fork https://github.com/vscoder/reddit.

Fixed it. Zakommitel. Created PR https://github.com/express42/reddit/pull/10.

Fixed it in my repository.


### Single task with an asterisk \.

Something strange is going on with our app. Users complain that when they click on a post they have to wait a long time for the page with the post to load. There was no complaint about other pages being loaded. We need to find out what the problem is by using Zipkin.

[Repository link](https://github.com/Artemmkin/bugged-code) with broken application code.

You can publish a description of the problem in PR, in the Job Performance section with an asterisk.

#### Repository

``shell
git clone git@github.com:Artemmkin/bugged-code.git
```

Parameterize the directory with sources in [Makefile](Makefile)
``makefile
# Source code directory
SRC_DIR?=./src.
...
###
# Build
###
build_comment:
	. ./env && \
	cd ${SRC_DIR}/comment && bash ./docker_build.sh

build_post.sh ./docker_build:
	. ./env && \
	cd ${SRC_DIR}/post-py && bash ./docker_build.sh

build_ui:
	. ./env && \
	cd ${SRC_DIR}/ui && bash ./docker_build.sh
```

Each image has a `bugged-code/*/docker_build.sh` tag.

Collecting images.

``shell
make build_comment build_post build_ui SRC_DIR=./bugged-code
```

In `docker/.env` change the services to `bugged`. 

Run the application:
``shell``
make run_app
```


#### Problem

When opening the application page, we see an error
> Can't show blog posts, some problems with the post service. Refresh?

At zipkin:
1. we find the wrong track, open it.
2. We find the wrong span, open it.

We see a mistake.
``log
error Request connection failed.
http.path /posts
Server Address 127.0.0.1:4567 (127)
```

Why is he trying to open the post to `127.0.0.1`? At the time he has to go to a service with the name post...

Solution: In `Dockerfile` of our application the default values with the service addresses were set. This is not the case in the `bugged` version. Let's set these variables via `environment` in [docker-compose.yml](docker/docker-compose.yml).
``Yaml
service:
  ui:
    environment:
      APP_HOME: ${UI_APP_HOME}
      ZIPKIN_ENABLED: ${ZIPKIN_ENABLED}
      POST_SERVICE_HOST: post
      POST_SERVICE_PORT: 5000
      COMMENT_SERVICE_HOST: comment
      COMMENT_SERVICE_PORT: 9292
    image: ${USERNAME}/ui:${UI_VERSION}
```
The values of the variables are set explicitly, because the addresses of the severs are hidden in the composit file itself, and the port numbers are not configured for applications.

Restart the application.
``shell
make down_app
make run_app
```

It all works now. We're continuing our work on the remote sensing.


#### Searching for trouble

The opening of the post page is very slow http://34.69.62.207:9292/post/5dfa57b6ee0fa2000ea79437.

We're watching zipkin:

- Find Trace `3.071s 6 spans`.
- span `post.db_find_single_post: 3.006s`.

Looks like the search for the post is too slow.

Restart normal application (version `logging`): same spawn ~105ms

Problem found.


#### Problem with EFK

Let's look at kibana.

`json
{
  "_index": "fluentd-20191218."
  "_type": "access_log."
  "_id": "aTxvGm8BX5Q2VjUnBF1B",
  "_version." 1,
  "_score": null,
  "_source." {
    "error_class." "Fluent::ElasticsearchErrorHandler::ElasticsearchError."
    "error": "400 - Rejected by Elasticsearch."
    "location": null,
    "tag": "service.post."
    "time": 1576696476,
    "record." {
      "addr": "172.22.0.3",
      "event." "request."
      "level." "info."
      "method": "GET."
      "path": "/post/5dfa57b6ee0fa2000ea79437?"
      "request_id": "e27e47a9-6355-4a19-aeb1-40470d5004dd."
      "response_status." 200,
      "service": "post."
      "timestamp": "2019-12-18 19:14:36."
    },
    "message": "dump an error event: error_class=Fluent::ElasticsearchErrorHandler::ElasticsearchError error=\"400 - Rejected by Elasticsearch\" location=nil tag=\"service.post\" time=157696476 record={\"addr\"=>\"172.22.0. 3\", \"event\"=>\"request\", \"level\"=>\"info\", \"method\"=>\"GET\"=>\"/post/5dfa57b6ee0fa2000ea79437? \", \"request_id\"=>\"e27e47a9-6355-4a19-aeb1-40470d5004dd\", \"response_status\"=>200, \"service\"=>\"post\", \"timestamp\"=>\"2019-12-18 19:14:36\"}",
    "@timestamp": "2019-12-18T19:14:37+00:00."
    "@log_name": "fluent.warn"
  },
  "fields." {
    "@timestamp." [
      "2019-12-18T19:14:37.000Z."
    ]
  },
  "highlight." {
    "tag": [
      "@kibana-highlighted-field@service.post@/kibana-highlighted-field@"
    ],
    "message." [
      "dump an error event: error_class=Fluent::ElasticsearchErrorHandler::ElasticsearchError error=\"400 - Rejected by Elasticsearch\" location=nil tag=\"@kibana-highlighted-field@service.post@/kibana-highlighted-field@\" time=1576696476 record={\"addr\"=>\"172.22.0. 3\", \"event\"=>\"request\", \"level\"=>\"info\", \"method\"=>\"GET\"=>\"/post/5dfa57b6ee0fa2000ea79437? \", \"request_id\"=>\"e27e47a9-6355-4a19-aeb1-40470d5004dd\", \"response_status\"=>200, \"service\"=>\"post\", \"timestamp\"=>\"2019-12-18 19:14:36\"}".
    ],
    "tag.keyword." [
      "@kibana-highlighted-field@service.post@/kibana-highlighted-field@"
    ]
  },
  "sort." [
    1576696477000
  ]
}
```

Strange mistakes. Found Issue https://github.com/uken/fluent-plugin-elasticsearch/issues/467.

Let's try to include the debate in [logging/fluentd/fluent.conf](logging/fluentd/fluent.conf).
``xml
...
<match *.**>
  @type copy
  <store>
    @log_level debug
    @type elasticsearch
    host elasticsearch
...
```

``shell
make run_logging
```

Let's refresh the page...
There are no errors missing in es. The ES Logue:
``log
elasticsearch_1 | {"type": "server", "timestamp": "2019-12-18T19:24:39,220Z", "level": "DEBUG", "component": "o.e.a.b.TransportShardBulkAction", "cluster.name": "docker-cluster", "node.name": "elasticsearch", "message": "[fluentd-20191218][0] failed to execute bulk item (index) index {[fluentd-20191218][access_log][fjx4Gm8BX5Q2VjUnJV2n], source[{\"addr\":\"172. 22.0.3\",\ "event\":\ "request\",\ "level\":\ "info\",\ "method\":\ "GET\",\ "path\":\"/post/5dfa57b6ee0fa2000ea79437? \",\"request_id\":\"ce9c55fb-6522-4723-8769-c0a12f090b36\",\"response_status\":200,\"service\": \"post\",\"timestamp\":\"2019-12-18 19:24:38\",\"@timestamp\":\"2019-12-18T19:24:38+00:00\",\"@log_name\":\"service. post\"}]}", "cluster.uuid": "Tm7FR-K9RGmirE07d8jmsQ", "node.id": "R6gRLHXhQgWyqbXc3DY5iQ". , 
| "stacktrace." ["org.elasticsearch.index.mapper.MapperParsingException: failed to parse field [timestamp] of type [date] in document with id 'fjx4Gm8BX5Q2VjUnJV2n'. Preview of field's value: '2019-12-18 19:24:38',
```

Couldn't paint the field "timestamp"? Let's make it a line))

In Kibana: Management -> Index Patterns -> page 7 -> `timestamp` change -> Format: **String**

Now the newly arrived messages look normal.

The debug of the plugin in [logging/fluentd/fluent.conf] (logging/fluentd/fluent.conf) has disabled `make fluentd_build run_logging`.


### How to start a project:

#### Preparations

Preliminarily it is necessary to fill in the ./env and ./monitoring/alertmanager/env files, following the example of env.example, in the corresponding directories, as well as to perform authorization in gcloud

``shell
# Installing docker-machine
make install_docker_machine

# Creating docker-machine
make docker_machine_create_logging

# The use of docker-machine
eval $(docker-machine env logging)

# Find out about docker-machine ip
make docker_machine_ip_logging
```

#### Starting

- `make run_logging run_app` - only application and logging.
- Or ``make run`` - launching everything.


## HomeWork 19: Introduction to Kubernetes

### Making primitives

Let's describe the application in the context of Kubernetes using the YAML format. The main primitive is *Deployment*. The main tasks of the essence of *Deployment*:

- Create an *Replication Controller* (makes sure that the number of running *Pods* corresponds to the number described above);
- Maintaining the history of versions of running *Pods* (for different deploying strategies, for rollback opportunities);
- Description of the deploying process (strategy, strategy parameters).

Example *Deployment*:
`post-deployment.yml'.
``Yaml
---
apiVersion: apps/v1beta2
kind: Deployment
metadata:
  name: post-deployment
spec:
  replicas: 1
  selector:
    matchLabels:
      app: post
  Oh..:
    metadata:
      name: post
      The labels:
        app: post
    spec:
      containers:
      - image: vscoder/post
        name: post
```

### Task

- Create a directory of `kubernetes` in the root of the repository;
- Inside `kubernetes` create a directory `reddit`;
- Save the file [post-deployment.yml] (kubernetes/reddit/post-deployment.yml) in `kubernetes/reddit`;
- Create your own files with *Deployment* application manifest and save them in `kubernetes/reddit`;
  - [ui-deployment.yml](kubernetes/reddit/ui-deployment.yml)
  - [comment-deployment.yml](kubernetes/reddit/comment-deployment.yml)
  - [mongo-deployment.yml](kubernetes/reddit/mongo-deployment.yml)

P.S. This directory and the files in it will be further developed (as long as they are not working copies).


### Kubernetes The Hard Way

["Difficult path"] (https://github.com/kelseyhightower/kubernetes-the-hard-way) install Kubernetes.

As your homework assignment, you can go through [Kubernetes The Hard Way] (https://github.com/kelseyhightower/kubernetes-the-hard-way) developed by Google engineer Kelsey Hightower.
The tutorial represents..: 
- Step-by-step guide for manual installation of main components of the Kubernetes cluster;
- Brief description of necessary actions and objects.

At the moment:

- The Kubernetes version in this guide hangs on 1.15.

For those who have already passed THW before, we advise you to try to install version 1.17 by yourself without using the repository.

### Task

- Create a separate directory `the_hard_way` in the directory `kubernetes`;
- Go **Kubernetes The Hard Way**;
- Check that `kubectl apply -f <filename>` goes through the previously created subdirectories (`ui`, `post`, `mongo`, `comment`) and the subdirectories are started;
- Remove the cluster after passing THW;
- All files created during the passage of THW (except binary files) should be placed in the folder `kubernetes/the_hard_way` of the repository (certificates and keys can also be committed, but only after deleting the cluster).

### Possible problems

If at step **Bootstrapping the etcd Cluster** you don't have the command `sudo systemctl start etcd` running, you probably don't use parallel input with tmux, but rather execute commands for each server separately. For the command to run successfully, install `etcd` on each of the necessary instances and **run it on all instances at once**.

If an error `(gcloud.compute.addresses.describe) argument --region: expected one argument` occurs during the command execution process, make sure that you execute the command in the right place. This usually happens when the command needs to be executed on the local machine and the command is executed in some instance. If the command is exactly executed locally, then run it:
```
{
  gcloud config set compute/region us-west1
  gcloud config set compute/zone us-west1-c
}
```

### Task from \ ##

- Describe the installation of Kubernetes components from THW as Ansible Playbook in the folder `Kubernetes/ansible`;
- The task is enough to execute in the form of Proof of Concept, simply automation of some actions tutorial.

I won't perform the task with *, because no practical application is expected, besides [KubeSpray] (https://github.com/kubernetes-sigs/kubespray).

### task fulfillment

The task execution will be described in a separate file [kubernetes/the_hard_way/README.md](kubernetes/the_hard_way/README.md).

### Deployments check

The cluster is expanded by THW: [process description](./kubernetes/the_hard_way/README.md).

Next, the depressed bottom of our application:

``shell
cd kubernetes/reddit
kubectl apply -f ./
```
``log
deployment.apps/comment-deployment created
deployment.apps/mongo-deployment created
deployment.apps/post-deployment created
deployment.apps/ui-deployment created
```

``shell
kubectl get pods
```
``log
NAME READY STATUS RESTARTS AGE
busybox 1/1 Running 0 51m
comment-deployment-5bb6744cdd-rprz9 1/1 Running 0 32s
mongo-deployment-86d49445c4-fzsbp 1/1 Running 0 31s
nginx-554b9c67f9-zkpn2 1/1 Running 0 42m
post-deployment-7576fb4896-m9tm7 1/1 Running 0 31s
ui-deployment-57d7c9fd56-s7gcq 1/1 Running 0 30s
```

As you can see, it works. Next is cleaning and commit.


## HomeWork 20: Kubernetes. Running cluster and application. Security model.

### Plan

- Deploy the local environment to work with Kubernetes
- Deploy Kubernetes in GKE 
- Run reddit on Kubernetes.


### Expanding Kubernetes locally

For further work we need to prepare the local environment, which will consist of:

1. **kubectl** - actually, the main utility for working with the Kubernetes API (everything that kubectl does can be done using HTTP requests to the k8s API)
2. Directories `~/.kube` - contains service info for kubectl (configs, caches, API schemes)
3. **minikube** - utilities to deploy local Kubernetes installation.


#### Kubectl

You must install kubectl: All installation methods are available at [link] (https://kubernetes.io/docs/tasks/tools/install-kubectl/).

We'll put `kubectl` version compatible with the minikube version of kubernetes.


#### minikube

To run Minukube you will need a local hypervisor: 

1. For OS X: or xhyve driver, or VirtualBox, or VMware Fusion
2. For Linux: VirtualBox or KVM.
3. For Windows: VirtualBox or Hyper-V.

In general, VirtualBox is our everything))). It's already installed.

### Minikube

Instructions for installing Minikube for different operating systems: https://kubernetes.io/docs/tasks/tools/install-minikube/.

#### Before you begin

Virtualization support test
``shell
grep -E --color 'vmx|svm' /proc/cpuinfo
```
``log
flags: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault invpcid_single pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid ept_ad fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 erms invpcid rtm mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp md_clear flush_l1d
...
```
We know how to do everything.

#### Installing minikube

install latest kubectl
``shell
cd ~/bin
curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl
chmod +x kubectl
mv kubectl kubectl-v1.17.0
ln -s kubectl-v1.17.0 kubectl
kubectl version --client
```
``log
Client Version: version.Info{Major: "1", Minor: "17", GitVersion: "v1.17. 0", GitCommit: "70132b0f130acc0bed193d9ba59dd186f0e634cf", GitTreeState: "clean", BuildDate: "2019-12-07T21:20:10Z", GoVersion: "go1.13.4", Compiler: "gc", Platform: "linux/amd64".}
```

Install Minikube via direct download

``shell
curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 \.
  && chmod +x minikube
mv minikube minikube-v1.6.2
ln -s minikube-v1.6.2 minikube
minikube version
```
``log
minikube version: v1.6.2
commit: 54f28ac5d3a815d1196cd5d57d707439ee4bb392
```

Give more memory
``shell
minikube config set memory 4096
```
``log
⚠️ These changes will take effect upon a minikube delete and then a minikube start
```

Let's launch our Minukube-cluster.
" hell
minikube start
```
``log
😄 minikube v1.6.2 on Ubuntu 18.04
✨ Automatically selected the 'virtualbox' driver (alternates: [none]).
💿 Downloading VM boot image ...
    > minikube-v1.6.0.iso.sha256: 65 B / 65 B [--------------] 100.00% ? p/s 0s
    > minikube-v1.6.0.iso: 150.93 MiB / 150.93 MiB [] 100.00% 10.95 MiB p/s 14s
🔥 Creating virtual box VM (CPUs=2, Memory=4096MB, Disk=20000MB) ...
🐳 Preparing Kubernetes v1.17.0 on Docker '19.03.5' ...
💾 Downloading Kubeadm v1.17.0
💾 Downloading kubelet v1.17.0
🚜 Pulling images ...
🚀 Launching Kubernetes ... 
⌛ Waiting for cluster to come online ...
🏄 Done! kubectl is now configured to use "minikube"
```

P.S. If you need a specific version of kubernetes, specify the `--kubernetes-version <version>' flag (v1.8.0).
P.P.S. Use VirtualBox by default. If you have a different hypervisor, set the `--vm-driver=<hypervisor>' flag.


#### Kubectl

Our Minikube-cluster has been deployed. The kubectl config was automatically set up.

Let's see if that's true:
``shell.
kubectl get nodes
```
``log
NAME STATUS ROLES AGE VERSION
minikube Ready master 14m v1.17.0
```

The kubectl configuration is **context**.

Context is a combination:

1. **cluster** - API server
2. **user** - user to connect to the cluster
3. **namespace** - scope (not required, default)

Information about kubectl contexts is saved in the file `~~/.kube/config`.

File `~/.kube/config` is the same kubernetes manifest in YAML format (there is both Kind and ApiVersion). 
``Yaml
apiVersion: v1
clusters: # List of clusters
- It's a cluster:
    # the root certificate (with which the SSL certificate of the server itself is signed),
    # to make sure we're not being fooled and we're facing the same server
    Authority: /home/vscoder/.minikube/ca.crt
    # kubernetes API server address
    server: https://192.168.99.100:8443
  # (Name) for identification in config
  name: minikube
contexts: # List of contexts
# Context (context) is:
- context:
    # cluster name from the clusters list 
    cluster: minikube
    # user name from the list of users 
    user: minikube
    # namespace: default visibility area (optional)
  # (Name) for identification in config
  name: minikube
current-context: minikube
kind: Config
I'm sorry: {}
users: # List of users
# The user is..: 
- name: minikube # name for identification in the config
  A user:
    # Data for authentication (depends on how the server is configured). 
    # It can be:
    # - username + password (Basic Auth
    # - client key + client certificate
    # - token
    # - auth-provider config (like GCP)
    client-certificate: /home/vscoder/.minikube/client.crt
    client-key: /home/vscoder/.minikube/client.key
```

Usually the order of configuring kubectl is as follows:

1. Create cluster:
    ``hell
    kubectl config set-cluster ... cluster_name
    ```
2. Create user data (credentials)
    ``shell
    kubectl config set-credentials ... user_name
    ```
3. Create a context
    ``shell
    kubectl config set-context context_name \
      -cluster=cluster_name \
      --user=user_name
    ```
4. use context
    ``shell
    kubectl config use-context context_name
    ```

This way kubectl is configured to connect to different clusters, under different users.

The current context can be seen as follows: 
``shell
kubectl config current-context
```
``log
minikube
```

The list of all contexts can be seen as follows:
``shell
kubectl config get-contexts
```
``log
CURRENT NAME CLUSTER AUTHINFO NAMESPACE
* minikube minikube minikube *
```

#### Let's run the application

To work in kubernetes applications, we need to describe their desired state either in YAML-manifests or using the command line.

Place the entire configuration in the `./kubernetes/reddit` directory inside your repository.

##### Deployment

The main objects are resources **Deployment**.

As we remember from the previous lesson, its main tasks:
- Create a ReplicationSet (makes sure that the number of running Pods corresponds to the number described above)
- Maintaining the history of versions of running Pods (for different deploying strategies, for rollback opportunities).
- Deploying process description (strategy, strategy parameters)

##### UI

ui-deployment.yml

``Yaml
---
apiVersion: apps/v1beta2
kind: Deployment
metadata: # Depletion metadata block
  name: ui
  The labels:
    app: reddit
    component: ui
spec: # Deploy Specification Unit
  replicas: 3
  # selector describes how he can track PODs.
  # In this case, the controller will read PODs with labels:
  # app=reddit And component=ui.
  # It is therefore important to specify the labels in the POD description. 
  # P.S. For more flexible sampling, enter 2 labels (app and component).
  selector:
    matchLabels:
      app: reddit
      component: ui
  # POD description block
    metadata:
      name: ui-pod
      The labels:
        app: reddit
        component: ui
    spec:
      containers:
        - image: vscoder/ui
          name: ui
```

Let's run the Minikube ui component.

``shell
cd kubernetes/reddit
kubectl apply -f ui-deployment.yml
```
``log
error: unable to recognize "ui-deployment.yml": no matches for kind of "Deployment" in version "apps/v1beta2"
```

Search and find https://stackoverflow.com/questions/58481850/no-matches-for-kind-deployment-in-version-extensions-v1beta1.
``shell
kubectl api-resources
```
``log
NAME SHORTNAMES APIGROUP NAMESPACED KIND
...
deployments deploy apps true Deployment
...
```
> It means that only apiVersion with apps is correct for Deployments (extensions is not supporting Deployment).

OK [kubernetes/reddit/ui-deployment.yml](kubernetes/reddit/ui-deployment.yml).
``Yaml
---
apiVersion: apps/v1
kind: Deployment
...
```

Repeat .
``shell
kubectl apply -f ui-deployment.yml
```
``log
deployment.apps/ui created
```

Check out .
``shell
kubectl get pods
```
``log
NAME READY STATUS RESTARTS AGE
ui-db4c86d69-4pbzg 1/1 Running 0 98s
ui-db4c86d69-94lm4 1/1 Running 0 98s
ui-db4c86d69-vrnnk 1/1 Running 0 98s
```

Make sure that 2, 3, 4 and 5 columns have number 3 (number of ui lines):
``shell
kubectl get deployment
```
``log
NAME READY UP-TO-DATE AVAILABLE AGE
ui 3/3 3 11m
```

P.S. `kubectl apply -f <filename>` can accept not only a single file, but also a folder with them. For example `kubectl apply -f ./kubernetes/reddit`.

So far, we can't use our application fully because we have no network configured to communicate with it.

But kubectl knows how to dump POD ports on the local machine.

We'll find POD applications using the selector:
``shell
kubectl get pods --selector component=ui
kubectl port-forward ui-db4c86d69-4pbzg 8080:9
```
``log
.Forwarding from 127.0.0.1:8080 -> 9292
Forwarding from [::1]:8080 -> 9292
```

Go to http://localhost:8080/ in your browser.

The UI is working, let's connect the other components

##### Comment

[kubernetes/reddit/comment-deployment.yml](kubernetes/reddit/comment-deployment.yml)
``Yaml
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: comment
  The labels:
    app: reddit
    component: comment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: reddit
      component: comment
  Oh..:
    metadata:
      name: comment
      The labels:
        app: reddit
        component: comment
    spec:
      containers:
      - image: vscoder/comment
        name: comment
```

The comment component is described in a similar way. Only the image name and tags are changed and applied (kubectl apply).
``shell
kubectl apply -f comment-deployment.yml
```
``log
deployment.apps/comment created
```
``shell
kubectl get deployment
```
``log
NAME READY UP-TO-DATE AVAILABLE AGE
comment 3/3 3 2m52s
ui 3/3 3 19m
```

You can also check it by quoting <local-port>: 9292 and going to http://localhost:<local-port>/healthcheck.
``shell
kubectl get pods --selector component=comment
kubectl port-forward comment-7c997b69c9-976wq 8080:9292
```
``log
Forwarding from 127.0.0.1:8080 -> 9292
Forwarding from [::1]:8080 -> 9292
```

Successfully

##### Post

Configure the post-deployment component in the same way yourself and test it.

Remember that post is listening by default on port 5000.

``Yaml
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: post
  The labels:
    app: reddit
    post
spec:
  replicas: 3
  selector:
    matchLabels:
      app: reddit
      post
  Oh..:
    metadata:
      name: post
      The labels:
        app: reddit
        post
    spec:
      containers:
        - image: vscoder/post
          name: post
```

``shell
kubectl apply -f post-deployment.yml
```
``log
deployment.apps/post created
```
``shell
kubectl get deployment
```
``log
NAME READY UP-TO-DATE AVAILABLE AGE
comment 3/3 3 12m
post 3/3 3 3 14s
ui 3/3 3 3 29m
```

``shell
kubectl get pods --selector component=post
kubectl port-forward post-57dd96857f-sm8d7 8080:5000
```
``log
Forwarding from 127.0.0.1:8080 -> 5000
Forwarding from [::1]:8080 -> 5000
```

It works (though not found)

##### MongoDB

Let's place the database All similar, but only the images and label values change.
``Yaml
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: mongo
  The labels:
    app: reddit
    mongo
spec:
  replicas: 1
  selector:
    matchLabels:
      app: reddit
      mongo
  Oh..:
    metadata:
      name: mongo
      The labels:
        app: reddit
        mongo
    spec:
      containers:
        - image: mongo:3.2
          name: mongo
```

We will also mount a standard Volume to store data outside the container.
``Yaml
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: mongo
  The labels:
    app: reddit
    mongo
spec:
  replicas: 1
  selector:
    matchLabels:
      app: reddit
      mongo
  Oh..:
    metadata:
      name: mongo
      The labels:
        app: reddit
        mongo
    spec:
      containers:
        - image: mongo:3.2
          name: mongo
          volumeMounts:
            - name: mongo-persistent-storage
              mountPath: /data/db
      Oh..:
        - name: mongo-persistent-storage
          emptyDir: {}
```

``shell
kubectl apply -f mongo-deployment.yml
```
``log
deployment.apps/mongo created
```

``shell
kubectl get deployment               
```
``log
NAME READY UP-TO-DATE AVAILABLE AGE
comment 3/3 3 16m
mongo 1/1 1 1 26s
post 3/3 3 3 4m45s
ui 3/3 3 33m
```

#### Services

In the current state the application will not work, so its components do not know how to find each other yet.

To connect the components to each other and to the outside world, a Service object is used - an abstraction that defines a set of PODs (Endpoints) and how to access them.

To connect ui to post and comment, you need to create them by the Service object.

When the service object is created:
1. The record for comment will appear in DNS
2. When addressing the post:9292 address from within any of the PODs of the current namespace we will be forwarded to the 9292 port of one of the PODs of the post application selected by labels.

[kubernetes/reddit/comment-service.yml](kubernetes/reddit/comment-service.yml)
``Yaml
---
apiVersion: v1
kind: Service
metadata:
  name: comment
  The labels:
    app: reddit
    component: comment
spec:
  ports:
    - port: 9292
      protocol: TCP
      targetPort: 9292
  Selector:
    app: reddit
    component: comment
```

Appropriate PODs should have been found on the label. You can look at them with the help: 
``shell
kubectl describe service comment | grep Endpoints
```
But we couldn't find it, because the name of the yamlice wasn't mentioned.)
``shell
kubectl apply -f ./comment-service.yml
```
``log
service/comment created
```

But nothing has been found.
``shell
kubectl describe service comment | grep Endpoints
```
``log
Endpoints:
```

Checking the hem.
``shell
kubectl get pods
```
``log
NAME READY STATUS RESTARTS AGE
comment-7c997b69c9-976wq 1/1 Running 2 3h22m
comment-7c997b69c9-rlndx 1/1 Running 2 3h22m
comment-7c997b69c9-x87lf 1/1 Running 1 3h22m
mongo-7fb8945897-d9h9j 1/1 Running 0 3h6m
post-57dd96857f-sm8d7 1/1 Running 0 3h10m
post-57dd96857f-sr98f 1/1 Running 0 3h10m
post-57dd96857f-twsdj 1/1 Running 0 3h10m
ui-db4c86d69-4pbzg 1/1 Running 0 3h39m
ui-db4c86d69-94lm4 1/1 Running 0 3h39m
ui-db4c86d69-vrnnk 1/1 Running 0 3h39m
```
Got .

Checking deployments.
``shell
kubectl get deployments
```
``log
NAME READY UP-TO-DATE AVAILABLE AGE
comment 0/3 3 0 3h22m
mongo 0/1 1 0 3h6m
post 0/3 3 0 3h10m
ui 0/3 3 0 3h39m
```

Checking to see if we're still alive
``shell
kubectl get componentstatuses
```
``log
NAME STATUS MESSAGE ERROR
controller-manager Unhealthy Get http://127.0.0.1:10252/healthz: dial tcp 127.0.0.1:10252: connect: connection refused   
Healthy ok                                                                                          
etcd-0 Healthy {"health": "true" }
```
Apparently, this is where the dog rushed through. A minicube is such a minicube...

Restart .
``shell
minikube stop
minikube start
kubectl get componentstatuses
```
``log
NAME STATUS MESSAGE ERROR
Healthy ok                  
controller-manager Healthy ok                  
etcd-0 Healthy {"health": "true" }
```

Repeat check from the remote control.
``shell
kubectl describe service comment | grep Endpoints
```
``log
Endpoints: 172.17.0.10:9292,172.17.0.5:9292,172.17.0.8:9292
```

And from within any POD must be allowed:
``shell
kubectl exec -ti post-57dd96857f-sr98f nslookup comment
```
``log
nslookup: can't resolve '(null)': Name does not resolve

Name: comment
Address 1: 10.96.204.230 comment.default.svc.cluster.local
```

#### Assignment

By analogy, create a Service object in the postservice.yml file for the post component (don't forget the label and correct tcp ports).

[kubernetes/reddit/post-service.yml](kubernetes/reddit/post-service.yml)
``Yaml
---
apiVersion: v1
kind: Service
metadata:
  name: post
  The labels:
    app: reddit
    post
spec:
  ports:
    - port: 5000
      protocol: TCP
      targetPort: 5000
  Selector:
    app: reddit
    post
```

And we apply
``shell
kubectl apply -f ./post-service.yml   
```
``log
service/post created
```

And we're checking
``shell
kubectl describe service post | grep Endpoints
```
``log
Endpoints: 172.17.0.11:5000,172.17.0.2:5000,172.17.0.9:5000
```

##### Services

Post and Comment also use mongodb, so it also needs a Service object.

[kubernetes/reddit/mongodb-service.yml](kubernetes/reddit/mongodb-service.yml)
``Yaml
---
apiVersion: v1
kind: Service
metadata:
  name: mongodb
  The labels:
    app: reddit
    mongo
spec:
  ports:
    - port: 27017
      protocol: TCP
      targetPort: 27017
  Selector:
    app: reddit
    mongo
```

In fact, it's all pretty much like a depression: 
" hell
kubectl apply -f mongodb-service.yml 
```
``log
service/mongodb created
```

something's gone down again
``shell
kubectl get componentstatuses
```
``log
NAME STATUS MESSAGE ERROR
scheduler Unhealthy Get http://127.0.0.1:10251/healthz: dial tcp 127.0.0.1:10251: connect: connection refused   
controller-manager Unhealthy Get http://127.0.0.1:10252/healthz: dial tcp 127.0.0.1:10252: connect: connection refused   
etcd-0 Healthy {"health": "true" }
```

run again
``shell
minikube stop && minikube start
```

Check out .
``shell
kubectl describe service mongodb | grep Endpoints
```
``log
Endpoints: 172.17.0.3:27017
```

Check: Throw the port on the ui pod.
``shell
kubectl get pods --selector component=ui  
```
``log
NAME READY STATUS RESTARTS AGE
ui-db4c86d69-4pbzg 1/1 Running 2 4h37m
ui-db4c86d69-94lm4 1/1 Running 2 4h37m
ui-db4c86d69-vrnnk 1/1 Running 2 4h37m
```

``shell
kubectl port-forward ui-db4c86d69-4pbzg 9292:9292
```
``log
Forwarding from 127.0.0.1:9292 -> 9292
Forwarding from [::1]:9292 -> 9292
```

When you open http://localhost:9292/, he thinks long and curses. 
> Can't show blog posts, some problems with the post service. Refresh?

While searching for the reason, I found out that the host name from the database for `post` is set to [src/post-py/Dockerfile](src/post-py/Dockerfile) of the environment variable `POST_DATABASE_HOST` and is set to `post_db` by default.

I've read more about RS - and it says the same)))). Well, it happens!

Let's go to the remote control.

Let's look at the logs, like comment: 
``shell
kubectl get pods --selector component=comment
```
``log
NAME READY STATUS RESTARTS AGE
comment-7c997b69c9-976wq 1/1 Running 8 26h
comment-7c997b69c9-rlndx 1/1 Running 10 26h
comment-7c997b69c9-x87lf 1/1 Running 9 26h
```
``shell
kubectl logs -f comment-7c997b69c9-976wq
```
``log
Puma starting in single mode...
* Version 3.12.0 (ruby 2.2.10-p489), codename: Llamas in Pajamas
* Min threads: 0, max threads: 16
* Environment: development
* Listening on tcp://0.0.0.0:9292
Use Ctrl-C to stop
I, [2019-12-24T18:02:35.924035 #1] INFO -- : service=comment | event=request | path=/healthcheck
request_id=null | remote_addr=172.17.0.9 | method= GET | response_status=200
I, [2019-12-24T18:02:45.389633 #1] INFO -- : service=comment | event=request | path=/healthcheck
request_id=null | remote_addr=172.17.0.9 | method= GET | response_status=200
I, [2019-12-24T18:02:47.939377 #1] INFO -- : service=comment | event=request | path=/healthcheck
request_id=null | remote_addr=172.17.0.6 | method= GET | response_status=200
I, [2019-12-24T18:02:50.178634 #1] INFO -- : service=comment | event=request | path=/healthcheck
request_id=null | remote_addr=172.17.0.9 | method= GET | response_status=200
I, [2019-12-24T18:02:55.322827 #1] INFO -- : service=comment | event=request | path=/healthcheck
request_id=null | remote_addr=172.17.0.9 | method= GET | response_status=200
I, [2019-12-24T18:02:55.558306 #1] INFO -- : service=comment | event=request | path=/healthcheck
...
I, [2019-12-24T18:25:22.939060 #1] INFO -- : service=comment | event=request | path=/healthcheck
request_id=null | remote_addr=172.17.0.6 | method= GET | response_status=200
I, [2019-12-24T18:25:29.711918 #1] INFO -- : service=comment | event=request | path=/healthcheck
request_id=null | remote_addr=172.17.0.11 | method= GET | response_status=200
I, [2019-12-24T18:25:32.967963 #1] INFO -- : service=comment | event=request | path=/healthcheck
request_id=null | remote_addr=172.17.0.6 | method= GET | response_status=200
I, [2019-12-24T18:25:43.715830 #1] INFO -- : service=comment | event=request | path=/healthcheck
request_id=null | remote_addr=172.17.0.6 | method= GET | response_status=200
I, [2019-12-24T18:25:45.831078 #1] INFO -- : service=comment | event=request | path=/healthcheck
request_id=e36bcff5-d544-4ba7-8824-ac16df7524cc | remote_addr=172.17.0.9 | method= GET | response_status=200
```
There's nothing about the DB, as promised in the DZ...

All we have to do is believe the word, that's how it should be:
``Log.
$ kubectl logs post-56bbf6795-7btnm
D, [2017-11-23T11:58:14.036381 #1] DEBUG -- : MONGODB | Topology type 'unknown' initializing.
D, [2017-11-23T11:58:14.036584 #1] DEBUG -- : MONGODB | Server comment_db:27017 initializing.
D, [2017-11-23T11:58:14.041398 #1] DEBUG -- : MONGODB | getaddrinfo: Name does not resolve
D, [2017-11-23T11:58:14.090421 #1] DEBUG -- : MONGODB | getaddrinfo: Name does not resolve 
```

Oh, maybe you need a debug. And there is no debag?? log level `WARN` is hidden in [src/comment/comment_app.rb](src/comment/comment_app.rb) line 19.

It seems that the problem was that in my scripts `src/<service>/docker_build.sh` I had the `logging` tag inherited from the previous RS. Fixing it again.

I also had to change the code into [src/comment/comment_app.rb](src/comment/comment_app.rb) as it was mentioned above. Changed .
``Ruby
configure do
  Mongo::Logger.logger.level = Logger::WARN
  db = Mongo::Client.new(DB_URL, database: COMMENT_DATABASE,
                                 heartbeat_frequency: 2)
  set :mongo_db, db[:comments]
  set :bind, '0.0.0.0.0'.
  set :server, :puma
  set :logging, false
  set :mylogger, Logger.new(STDOUT)
end
```
at
``Ruby
configure do
  Mongo::Logger.logger.level = Logger::DEBUG
  db = Mongo::Client.new(DB_URL, database: COMMENT_DATABASE,
                                 heartbeat_frequency: 2)
  set :mongo_db, db[:comments]
  set :bind, '0.0.0.0.0'.
  set :server, :puma
  set :logging, false
  set :mylogger, Logger.new(STDOUT)
end
```

After the reassembly, rebuilds to the hub and remodeling, everything ** worked as specified in the RS**.

The application is looking for a completely different address: `comment_db` rather than `mongodb`. Similarly, the service `comment` is looking for `post_db`.

These addresses are set in their Dockerfile as environment variables:
`post/Dockerfile`.
``dockerfile
…
ENV POST_DATABASE_HOST=post_db
```
`comment/Dockerfile`
``dockerfile
…
ENV COMMENT_DATABASE_HOST=comment_db
```

In Docker Swarm, the problem of accessing the same resource under different names was solved by using network aliases.

There is no such functionality in Kubernetes. We can solve this problem with the help of the same services.

We will make a Service for the comment database.
[kubernetes/reddit/comment-mongodb-service.yml](kubernetes/reddit/comment-mongodb-service.yml)
``Yaml
---
apiVersion: v1
kind: Service
metadata:
  name: comment-db
  The labels:
    app: reddit
    mongo
    comment-db: "true"
spec:
  ports:
    - port: 27017
      protocol: TCP
      targetPort: 27017
  Selector:
    app: reddit
    mongo
    comment-db: "true"
```
P.S. Boolean values must be specified in quotation marks.

You will also have to update the deployment file for mongodb so that the new Service can find the right POD (remember to fix `apiVersion:` to `apps/v1`).
[kubernetes/reddit/mongo-deployment.yml](kubernetes/reddit/mongo-deployment.yml)
``Yaml
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: mongo
  The labels:
    app: reddit
    mongo
    comment-db: "true" # Label in deployment to make it clear what's deployed
spec:
  replicas: 1
  selector:
    matchLabels:
      app: reddit
      mongo
  Oh..:
    metadata:
      name: mongo
      The labels:
        app: reddit
        mongo
        comment-db: "true" # label in the pod that needs to be found
    spec:
      containers:
        - image: mongo:3.2
          name: mongo
          volumeMounts:
            - name: mongo-persistent-storage
              mountPath: /data/db
      Oh..:
        - name: mongo-persistent-storage
          emptyDir: {}
```

Let's set the pod-am comment environment variable for accessing the database (see slide 34)
[kubernetes/reddit/comment-deployment.yml](kubernetes/reddit/comment-deployment.yml)
``Yaml
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: comment
  The labels:
    app: reddit
    component: comment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: reddit
      component: comment
  Oh..:
    metadata:
      name: comment
      The labels:
        app: reddit
        component: comment
    spec:
      containers:
        - image: vscoder/comment:latest
          name: comment
          I'm sorry:
            - name: COMMENT_DATABASE_HOST
              value: comment-db
```

We made the base available for comment. 

Do the same for the service. The name of the service must be `post-db'.

So, create [kubernetes/reddit/post-mongodb-service.yml](kubernetes/reddit/post-mongodb-service.yml).
``Yaml
---
apiVersion: v1
kind: Service
metadata:
  name: post-db
  The labels:
    app: reddit
    mongo
    post-db: "true"
spec:
  ports:
    - port: 27017
      protocol: TCP
      targetPort: 27017
  Selector:
    app: reddit
    mongo
    post-db: "true"
```
[kubernetes/reddit/mongo-deployment.yml](kubernetes/reddit/mongo-deployment.yml)
``Yaml
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: mongo
  The labels:
    app: reddit
    mongo
    comment-db: "true"
    post-db: "true" # Label in deployment so it's clear what's deployed
spec:
  replicas: 1
  selector:
    matchLabels:
      app: reddit
      mongo
  Oh..:
    metadata:
      name: mongo
      The labels:
        app: reddit
        mongo
        comment-db: "true"
        post-db: "true" # label in the pod that needs to be found
    spec:
      containers:
        - image: mongo:3.2
          name: mongo
          volumeMounts:
            - name: mongo-persistent-storage
              mountPath: /data/db
      Oh..:
        - name: mongo-persistent-storage
          emptyDir: {}
```

[kubernetes/reddit/post-deployment.yml](kubernetes/reddit/post-deployment.yml)
``Yaml
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: post
  The labels:
    app: reddit
    post
spec:
  replicas: 3
  selector:
    matchLabels:
      app: reddit
      post
  Oh..:
    metadata:
      name: post
      The labels:
        app: reddit
        post
    spec:
      containers:
        - image: vscoder/post
          name: post
          I'm sorry:
            - name: POST_DATABASE_HOST
              value: post-db
```

``shell
kubectl apply -f ./kubernetes/reddit
```
``log
deployment.apps/comment unchanged
service/comment-db created
service/comment unchanged
deployment.apps/mongo configured
service/mongodb unchanged
deployment.apps/post configured
service/post-db created
service/post
deployment.apps/ui unchanged
```

Then do port-forwarding on the UI again and make sure that the application started without errors and the posts are created. **It's all working**.

Let's check the post logs again.
``shell
kubectl get pods --selector component=comment
kubectl logs -f comment-68cdb988fd-9c9dd
```
``log
request_id=null | remote_addr=172.17.0.8 | method= GET | response_status=200
D, [2019-12-25T05:26:40.628648 #1] DEBUG -- : MONGODB | Topology type 'unknown' initializing.
D, [2019-12-25T05:26:40.629523 #1] DEBUG -- : : MONGODB | Server comment-db:27017 initializing.
D, [2019-12-25T05:26:40.722276 #1] DEBUG -- : MONGODB | Topology type 'unknown' changed to type 'single'.
D, [2019-12-25T05:26:40.731802 #1] DEBUG -- : MONGODB | Server description for comment-db:27017 changed from 'unknown' to 'standalone'.
D, [2019-12-25T05:26:40.732365 #1] DEBUG -- : MONGODB | There was a change in the members of the 'single' topology.
D, [2019-12-25T05:26:40.737144 #1] DEBUG -- : : MONGODB | comment-db:27017 | admin.listDatabases | STARTED | {"listDatabases"=>1}
D, [2019-12-25T05:26:40.745121 #1] DEBUG -- : MONGODB | comment-db:27017 | admin.listDatabases | SUCCEEDED | 0.00496289s
```

Delete mongodb-service object 
``shell
cd kubernetes/reddit
kubectl delete -f mongodb-service.yml
```
``log
mongodb service deleted
```


We need to somehow provide access to the ui service from the outside. To do that, we'll need a Service for the UI components.

[kubernetes/reddit/ui-service.yml](kubernetes/reddit/ui-service.yml)
``Yaml
---
apiVersion: v1
kind: Service
metadata:
  name: ui
  The labels:
    app: reddit
    component: ui
spec:
  type: NodePort # Throw the port at node
  ports:  
    - port: 9292
      protocol: TCP
      targetPort: 9292
  Selector:
    app: reddit
    component: ui
```

By default, all services are of ClusterIP type - this means that the service is located on the internal IP address range of the cluster. It is not accessible from the outside.

Type **NodePort** - on each cluster node opens a port from the range **30000-32767** and forwards traffic from this port to the one specified in the targetPort Pod (similar to standard expose in docker)

Now you can reach the service by <Node-IP>:<NodePort>.

You can also specify NodePort itself (but still from the range):
```yaml
---
apiVersion: v1
kind: Service
metadata:
  name: ui
  The labels:
    app: reddit
    component: ui
spec:
  type: NodePort
  ports:
    - nodePort: 32092 # Specify port number on node
      port: 9292
      protocol: TCP
      targetPort: 9292
  Selector:
    app: reddit
    component: ui

```

I mean, in the description of the service 

**NodePort** - for access outside the cluster
**port** - to access the service from within the cluster

Let's apply:
``shell
kubectl apply -f ui-service.yml
```
``log
service/ui created
```


### Minikube

Minikube can produce web pages with services that have been marked as NodePort Try: 
``shell
minikube service ui
```
``log
| ----------- | ------ | ------------- | ----------------------------- |
| NAMESPACE | NAME | TARGET PORT | URL |
| ----------- | ------ | ------------- | ----------------------------- |
| default | ui | | http://192.168.99.103:32092 |
| ----------- | ------ | ------------- | ----------------------------- |
🎉 Opening service default/ui in default browser...
```

Minikube can redirect to web pages with services that have been labeled as NodePort Look at the list of services:
``shell
minikube service list   
```
``log


| NAMESPACE | NAME | TARGET PORT | URL |


| default | comment | No node port |
| default | comment-db | No node port |
| default | kubernetes | No node port |
| default | mongodb | No node port |
| default | post | No node port |
| default | post-db | No node port |
| default | ui | http://192.168.99.100:32092 |
| kube-system | kube-dns | No node port |


```

Minikube also comes with several standard addons (extensions) for Kubernetes (kube-dns, dashboard, monitoring,...). Each extension is the same PODs and services as we created, only they still communicate with the Kubernetes API itself.

Get a list of extensions:
``shell
minikube addons list
```
``log
- addon-manager: enabled
- dashboard: disabled
- default-storageclass: enabled
- efk: disabled
- freshpod: disabled
- gvisor: disabled
- helm-tiller: disabled
- ingress: disabled
- ingress-dns: disabled
- logviewer: disabled
- metrics-server: disabled
- nvidia-driver-installer: disabled
- nvidia-gpu-device-plugin: disabled
- registry: disabled
- registry-creds: disabled
- storage-provisioner: enabled
- storage-provisioner-gluster: disabled
```

Interesting addon - dashboard. It's a UI for working with kubernetes. It is enabled by default in new versions. Like many kubernetes add-on's, dashboard runs as a pod.

If we look at the running pods with the `kubectl get pods' command, we will only find our application.

Because the pods and services for **dashboard**-a were run in **namespace** (namespace) `kube-system`. We requested the `default` namespace.


#### Namespaces

**Namespace** is basically a virtual Kubernetes cluster inside the Kubernetes itself. Inside each such cluster there are different objects (PODs, Service-s, Deployment-s, etc.), except for objects common to all namespace objects (nodes, ClusterRoles, PersistentVolumes).

Different namespace may contain objects with the same name, but within the same namespace object names must be unique.

At the start of Kubernetes the cluster already has 3 namespace:

- **default** - for the objects for which no other Namespace is defined (we have been working in it all this time)
- **kube-system** - for objects created by Kubernetes and for its management
- **kube-public** - for objects that need access from any point in the cluster

In order to select a specific namespace, you need to specify the flag `-n <namespace>` or `--namespace <namespace>` when running `kubectl`.

Before you look for the dashboard, you need to turn it on.
``shell
minikube dashboard
```
``log
🔌 Enabling dashboard ...
🤔 Verifying dashboard health ...
🚀 Launching proxy ...
🤔 Verifying proxy health ...
🎉 Opening http://127.0.0.1:37429/api/v1/namespaces/kubernetes-dashboard/services/http:kubernetes-dashboard:/proxy/ in your default browser...
^C
```
``shell
minikube addons list
```
``log
- addon-manager: enabled
- dashboard: enabled # now it's on
- default-storageclass: enabled
- efk: disabled
- freshpod: disabled
- gvisor: disabled
- helm-tiller: disabled
- ingress: disabled
- ingress-dns: disabled
- logviewer: disabled
- metrics-server: disabled
- nvidia-driver-installer: disabled
- nvidia-gpu-device-plugin: disabled
- registry: disabled
- registry-creds: disabled
- storage-provisioner: enabled
- storage-provisioner-gluster: disabled
```

Let's find the objects of our dashboard (in the RS command was wrong `kubectl get all -n kube-system --selector k8s-app=kubernetes-dashboard`).

``shell
kubectl get all -n kubernetes-dashboard --selector k8s-app=kubernetes-dashboard+
```
```
NAME READY STATUS RESTARTS AGE
pod/kubernetes-dashboard-79d9cd965-pmntx 1/1 Running 0 5m53s

NAME TYPE CLUSTER-IP EXTERNAL-IP PORT(S) AGE
service/kubernetes-dashboard ClusterIP 10.96.254.145 <none> 80/TCP 5m57s

NAME READY UP-TO-DATE AVAILABLE AGE
deployment.apps/kubernetes-dashboard 1/1 1 1 5m53s

NAME DESIRED CURRENT READY AGE
replicaset.apps/kubernetes-dashboard-79d9cd965 1 1 1 5m53s
```

And let's see for ourselves the Kubernetes-dashboard...
``shell
kubectl get all -n kubernetes-dashboard
```
``log
NAME READY STATUS RESTARTS AGE
pod/dashboard-metrics-scraper-7b64584c5c-pl8sg 1/1 Running 0 4m13s
pod/kubernetes-dashboard-79d9cd965-pmntx 1/1 Running 0 4m13s

NAME TYPE CLUSTER-IP EXTERNAL-IP PORT(S) AGE
service/dashboard-metrics-scraper ClusterIP 10.96.199.122 <none> 8000/TCP 4m17s
service/kubernetes-dashboard ClusterIP 10.96.254.145 <none> 80/TCP 4m17s

NAME READY UP-TO-DATE AVAILABLE AGE
deployment.apps/dashboard-metrics-scraper 1/1 1 4m13s
deployment.apps/kubernetes-dashboard 1/1 1 1 4m13s

NAME DESIRED CURRENT READY AGE
replicaset.apps/dashboard-metrics-scraper-7b64584c5c 1 1 1 4m13s
replicaset.apps/kubernetes-dashboard-79d9cd965 1 1 4m13s
```


#### Dashboard

Let's go to Dashboard:
``shell
minikube dashboard
```
``log
🤔 Verifying dashboard health ...
🚀 Launching proxy ...
🤔 Verifying proxy health ...
🎉 Opening http://127.0.0.1:36773/api/v1/namespaces/kubernetes-dashboard/services/http:kubernetes-dashboard:/proxy/ in your default browser...
```

In the Dashboard itself you can:

- track the status of the cluster and its workloads
- create new objects (upload YAML files)
- Delete and modify objects (number of replicas, yaml files)
- track logs in the Pods
- when you turn on the Heapster Addon, watch the load on the POS.
- and so on.

Get acquainted, cry - in minikube it is not afraid to break anything (if you raise it again).

We use it for our purposes. We will separate the application development environment from the rest of the cluster. For this purpose, let's create our own Namespace dev

``Yaml
---
apiVersion: v1
kind: Namespace
metadata:
  name: dev
```

``shell
kubectl apply -f dev-namespace.yml
```
``log
namespace/dev created
```

Let's run an application in the `dev' Neimscape:
``shell``
kubectl apply -n dev -f .
```
``log
deployment.apps/comment created
service/comment-db created
service/comment created
namespace/dev unchanged
deployment.apps/mongo created
service/mongodb created
deployment.apps/post created
service/post-db created
service/post created
deployment.apps/ui created
service/ui created
```

If there is a port conflict at **ui-service**, then remove the value `NodePort` from the description.

Let's see the result:
``shell
minikube service ui -n dev
```
Yeah, it's opening up.

Let's add environment info inside the UI container.

[kubernetes/reddit/ui-deployment.yml](kubernetes/reddit/ui-deployment.yml)
``Yaml
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: ui
  The labels:
    app: reddit
    component: ui
spec:
  replicas: 3
  selector:
    matchLabels:
      app: reddit
      component: ui
  Oh..:
    metadata:
      name: ui-pod
      The labels:
        app: reddit
        component: ui
    spec:
      containers:
        - image: vscoder/ui
          name: ui
          I'm sorry:
            - name: ENV
              valueFrom:
                fieldRef:
                  fieldPath: metadata.space
```

``shell
kubectl apply -f ui-deployment.yml -n dev
```
``log
deployment.apps/ui configured
```
On the dashboard, you can see that in the Neimscape dev, the deployment-ui was recreated...

Checking. Yes.
> Microservices Reddit in dev ui-687c9cfd9-6pjk9 container


### Unrolling Kubernetes

We prepared our application in a local environment. Now it's time to run it on a real Kubernetes cluster.

We will use Google Kubernetes Engine as the main platform.

Go to your gcloud console, go to "Kubernetes clusters".

Click Create Cluster"

Specify the following cluster settings:
- Machine type - small machine (**g1-small** 1.7 GB) (to save)
resources)
- Size - 2 (didn't find one, maybe - **Number of nodes**?).
- Basic Authentication - disabled (didn't find one)
- Outdated access rights - disabled (didn't find it)
- Kubernetes control panel - off (didn't find it)
- Boot disk size - 20 GB (to save) (made)

Click "Create" and wait for the cluster to come up.


### GKE

The cluster management components are run in the container engine and
are run by Google:
- kube-apiserver
- kube-scheduler
- kube-controller-manager
- etcd

Work load (own PODs), addons, monitoring, logging, etc. are run on work nodes

Working nodes are standard Google compute engine nodes. You can see them in the list of running nodes.
They can always be accessed by ssh 
They can be stopped and started.

Connect to GKE to run our application.

_Clusters_ -> **Connect**

Click and copy the view command:
``shell
gcloud container clusters get-credentials your-first-cluster-1 --zone us-central1-a --project docker-XXXXXX
```

Enter the command you copied into the console. 

This will add user, cluster and context to the ~/.kube/config file to connect to the cluster in GKE. The current context will also be set to connect to this cluster. You can verify this by entering
``shell
kubectl config current-context
```
``log
gke_docker-XXXXXX_us-central1-a_your-first-cluster-1
```

Run our application in GKE.

Let's create dev namespace
``shell
kubectl apply -f ./kubernetes/reddit/dev-namespace.yml
```
``log
namespace/dev created
```

Let's embed all application components in namespace dev:
``shell
kubectl apply -f ./kubernetes/reddit/ -n dev
```

Let's open Reddit to the outside world:

Go to "firewall rules" _VPC Network_ -> _Firewall rules_

Click "create firewall rule". **Create firewall rule**

Open the kubernetes port range for publishing services

Set it up:
- Title - arbitrary, but understandable.
- Targeted instances - all instances on the network
- Source IP address ranges - **0.0.0.0/0**

Protocols and ports - Specified protocols and ports **tcp:30000-32767**

**Create**

Find the external IP address of any node from the cluster in either the web console or the External IP in the output:
``shell
kubectl get nodes -o wide
```
``log
NAME STATUS ROLES AGE VERSION INTERNAL-IP EXTERNAL-IP OS-IMAGE KERNEL-VERSION CONTAINER-RUNTIME
gke-your-first-cluster-1-pool-1-c8223392-0btx Ready <none> 27m v1.15.4-gke.22 10.128.0.6 35.225.38.22 Container-Optimized OS from Google 4.19.76+ docker://19.3.1
gke-your-first-cluster-1-pool-1-c8223392-bz3m Ready <none> 27m v1.15.4-gke.22 10.128.0.7 34.69.56.68 Container-Optimized OS from Google 4.19.76+ docker://19.3.1
```

Find the ui service publishing port
``shell
kubectl describe service ui -n dev | grep NodePort
```
``log
Type: NodePort
NodePort: <unset> 32164/TCP
```

Go to http://35.225.38.22:32164.

#### Error: No comments displayed.

There's no way to leave comments on the ui. No comment application is displayed.

To start with, let's run the application in minikube (as far as I remember, everything worked there before).

``shell
minikube delete
minikube config set memory 4096
minikube start
```
``log
😄 minikube v1.6.2 on Ubuntu 18.04
✨ Automatically selected the 'virtualbox' driver (alternates: [none]).
🔥 Creating virtual box VM (CPUs=2, Memory=4096MB, Disk=20000MB) ...
🐳 Preparing Kubernetes v1.17.0 on Docker '19.03.5' ...
🚜 Pulling images ...
🚀 Launching Kubernetes ... 
⌛ Waiting for cluster to come online ...
🏄 Done! kubectl is now configured to use "minikube."
```

Checking the context
``shell
kubectl config get-contexts
```
``log
CURRENT NAME CLUSTER AUTHINFO NAMESPACE
          gke_docker-257914_us-central1-a_your-first-cluster-1 gke_docker-257914_us-central1-a_your-first-cluster-1 gke_docker-257914_us-central1-a_your-first-cluster-1   
* minikube minikube minikube *
```


``shell
kubectl apply -f ./kubernetes/reddit/dev-namespace.yml 
```
``log
namespace/dev created
```
``shell
kubectl apply -f ./kubernetes/reddit/ -n dev
```
``log
deployment.apps/comment created
service/comment-db created
service/comment created
namespace/dev unchanged
deployment.apps/mongo created
service/mongodb created
deployment.apps/post created
service/post-db created
service/post created
deployment.apps/ui created
service/ui created
```
Testing showed that the mini-cube also has a problem.

Back to working with GKE.
``shell
kubectl config use-context gke_docker-<project-id>_us-central1-a_your-first-cluster-1
```
``log
Switched to context "gke_docker-257914_us-central1-a_your-first-cluster-1".
```

A post `5e08b33850fa42000e78bd01` has been created through the application web-interface.

We are connected to podu `ui-595f89d499-44bjf`.
``shell
kubectl -n dev exec -it ui-595f89d499-44bjf -- /bin/sh
# Put curl
apk update && apk add curl
```
Check out .
``shell
curl http://comment:9292/5e08b33850fa42000e78bd01/comments
```
``log
[]
```
The comment service is available, the result is returned (no comments, so the list is empty). **Exclusion:** the problem should be searched in the _ui_ component.

Check your health at http://23.251.155.88:30927/healthcheck.
`json
{"status":1, "dependent_services":{"comment":1, "post":1}, "version": "0.0.1"}.
```
All healthy O_o

Accidentally, it turns out the make-up artist isn't a good person. At a certain size of the browser window (just I had one) you can't see div with the interface of adding a comment. When the scale or size of the window was changed, the controls for adding a comment appeared.
https://otus-devops.slack.com/archives/CMSD007E0/p1577619070042800.

### Task

The PR must have a configuration to deploy the Reddit application in kubernetes (deployments, services, namespace) in a separate directory.

The PR should have a screenshot of the application web interface in GKE (if desired) or a link to it.


### GKE Dashboard

In GKE you can also run the Dashboard for the cluster.

Click on cluster name -> __Edit__.

In this menu you can change the cluster configuration. We need to enable the "Kubernetes Control Panel" add-on - they said... Liar, you can't do anything like that, there's no button.

Let's read off-docs https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/.

From the off-docks, we have to apply:
``shell
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.0.0-beta8/aio/deploy/recommended.yaml
```
``log
namespace/kubernetes-dashboard unchanged
serviceaccount/kubernetes-dashboard created
service/kubernetes-dashboard created
secret/kubernetes-dashboard-certs created
secret/kubernetes-dashboard-csrf created
secret/kubernetes-dashboard-key-holder created
configmap/kubernetes-dashboard-settings created
role.rbac.authorization.k8s.io/kubernetes-dashboard created
clusterrole.rbac.authorization.k8s.io/kubernetes-dashboard unchanged
rolebinding.rbac.authorization.k8s.io/kubernetes-dashboard created
clusterrolebinding.rbac.authorization.k8s.io/kubernetes-dashboard unchanged
deployment.apps/kubernetes-dashboard created
service/dashboard-metrics-scraper created
deployment.apps/dashboard-metrics-scraper created
```

See .
``shell
kubectl proxy
```
``log
Starting to serve on 127.0.0.1:8001
```

Kubectl will make Dashboard available at http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/.

Requires authorization. Can't miss it, no **Skip** button.

Google: https://stackoverflow.com/questions/50747783/how-to-access-gke-kubectl-proxy-dashboard

> Provided you are authenticated with gcloud auth login and the current project and k8s cluster is configured to the one you need, authenticate kubectl to the cluster (this will write ~/.kube/config):
>
> ``shell
> gcloud container clusters get-credentials <cluster name> --zone <zone> --project <project>
> ```
> 
> retrieve the auth token that the kubectl itself uses to authenticate as you
> 
> ``shell
> gcloud config-helper --format=json | jq -r '.credential.access_token'.
> ```
> 
> run
> ``shell
> kubectl proxy
> ```
> 
> Then open a local machine web browser on
> 
> http://localhost:8001/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy (This will only work if you checked the checkbox Deploy Dashboard in GCP console).
> 
> and use the token from the second command to log in with your Google Account's permissions.

We enter the token and get the dashboard.

The dashboard displays everything, it has enough rights, unlike what is said in the RS. Apparently, because we gave him a service account token. But it's probably not right. So we're gonna re-create the dashboard and try to do the RS actions.

The dashboard doesn't have enough rights to look at the cluster. It's not allowed by RBAC (role-based access control system). We need our Service Account to assign a role with sufficient rights to view information about the cluster.

The cluster already has a ClusterRole object called cluster-admin. The person to whom this role is assigned has full access to all objects in the cluster.
``shell
kubectl create clusterrolebinding kubernetes-dashboard --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
```
``log
Error from server (AlreadyExists): clusterrolebindings.rbac.authorization.k8s.io "kubernetes-dashboard" already exists
```
Well, then we already have (all we needed was a depressed dashboard).

For clusterrole, serviceaccount `--serviceaccount=kube-system:kubernetes-dashboard` is a combination of serviceaccount and namespace, in which it is created.

### Task from \ ##

1. Deploy the Kubenetes cluster in GKE using the [Terraform module] (https://www.terraform.io/docs/providers/google/r/container_cluster.html). 
2. Create YAML Manifests to describe created entities to enable dashboard.
3. Attach configuration to PR

Found 2 modules to create a GKE cluster

1. From google https://github.com/terraform-google-modules/terraform-google-kubernetes-engine
2. From gruntwork-io https://registry.terraform.io/modules/gruntwork-io/gke/google/0.3.9.

Since there are already examples in the repositories of colleagues using the module from google, for possible future use, let's try the module from gruntwork-io https://registry.terraform.io/modules/gruntwork-io/gke/google/0.3.9.

Terraform infrastructure in `./kubernetes/terraform` is created.
``log
├── main.tf
├── outputs.tf
├── terraform.tfvars
├─ terraform.tfvars.example
└──.tf
```

Created by [kubernetes/terraform/Makefile](kubernetes/terraform/Makefile)

A file with the variables [kubernetes/terraform/terraform.tfvars](kubernetes/terraform/terraform.tfvars) was created.

Syntax check carried out
``shell
make tflint validate 
```
``log
~/bin/tflint
~/bin/terraform --version
Terraform v0.12.18
+ provider.external v1.2.0
+ provider.google v2.9.1
+ provider.google-beta v2.9.1
+ provider.helm v0.10.4
+ provider.kubernetes v1.7.0 0 + provider.google-beta v2.9.1 + provider.helm v0.10.4
+ provider.null v2.1.2
+ provider.random v2.2.1
+ provider.template v2.1.2
+ provider.tls v2.1.1
~/bin/terraform validate

Warning: External references from destroyers are deprecated

  on .terraform/modules/gke.tiller/modules/k8s-tiller/main.tf line 275, in resource "null_resource" "tiller_tls_ca_certs":
 275: command = <<-EOF
 276: ${var.kubectl_server_endpoint != "" ? "echo \"$KUBECTL_CA_DATA\" > ${path.module}/kubernetes_server_ca.pem" : ""}
 277: ${lookup(module.require_executables.executables, "kubectl", "")} ${local.esc_newl}
 278: ${local.kubectl_auth_params} ${local.esc_newl}
 279: --namespace ${var.tiller_tls_ca_cert_secret_namespace} ${local.esc_newl}
 280: delete secret ${local.tiller_tls_ca_certs_secret_name}.
 281: EOF

Destroy-time provisioners and their connection configurations may only
reference attributes of the related resource, via 'self', 'count.index', or
'each.key'.

References to other resources during the destruction phase can cause dependency
and interact poorly with creating_before_destroy.

(and 23 more similar warnings elsewhere)

Success! The configuration is valid, but there were some validation warnings as shown above.
```

Apply (the state will be local)
``shell
cd ./kubernetes/terraform
make apply
```

The infrastructure is being built...

There's been a mistake.
``log
Error: Get http://localhost/api/v1/namespaces/kube-system/serviceaccounts/tiller: dial tcp 127.0.0.1:80: connect: connection refused
```
And a few others like that when trying to remove the infrastructure.

After **reasonable reading** [documentation] (https://registry.terraform.io/modules/gruntwork-io/gke/google/0.3.9), in particular [gke-private-tiller example documentation] (https://github.com/gruntwork-io/terraform-google-gke/tree/master/examples/gke-private-tiller), I came to the conclusion that I should install [kubergrunt] (https://github.com/gruntwork-io/kubergrunt), which in turn requires [gruntwork-installer] (https://github.com/gruntwork-io/gruntwork-installer).

Well, here we go.

In [Makefile](kubernetes/terraform/Makefile) let's add the necessary targets and variables.
``makefile
# gruntwork-install
GRUNTWORK_INSTALL_VERSION?=v0.0.23

install_gruntwork_install:
	curl -LsS https://raw.githubusercontent.com/gruntwork-io/gruntwork-installer/master/bootstrap-gruntwork-installer.sh | bash /dev/stdin --version $GRUNTWORK_INSTALL_VERSION
```
Install: in the process the script asks for ruth. It's not okay. See [installation script sources] (https://github.com/gruntwork-io/gruntwork-installer/blob/master/bootstrap-gruntwork-installer.sh) and see there `readonly BIN_DIR="/usr/local/bin"`. Sadly, I don't put binary sources in the system from outside the packages.

Exits 3: 
- change the script
- source sth.
- google

To finish the started case, let's install `kubergrunt` from sources (at the same time let's see what kind of utility this is).

Remove the previously added target `install_gruntwork_install` from [Makefile] (kubernetes/terraform/Makefile) and add a target to install `kubergrunt`.
``makefile
# kubergrunt
KUBERGRUNT_VERSION?=v0.5.8
KUBERGRUNT_URL=https://github.com/gruntwork-io/kubergrunt/releases/download/${KUBERGRUNT_VERSION}/kubergrunt_linux_amd64
KUBERGRUNT?=${BIN_DIR}/kubergrunt.

install_kubergrunt:
	wget ${KUBERGRUNT_URL} -O ${TEMP_DIR}/kubergrunt-${KUBERGRUNT_VERSION}
	mv ${TEMP_DIR}/kubergrunt-${KUBERGRUNT_VERSION} ${BIN_DIR}/kubergrunt-${KUBERGRUNT_VERSION}
	ln -sf kubergrunt-${KUBERGRUNT_VERSION} ${BIN_DIR}/kubergrunt
	chmod +x ${BIN_DIR}/kubergrunt
	${BIN_DIR}/kubergrunt --version
```
Install .
``shell
make install_kubergrunt
```

Let's try to raise the inferno again.
" hell
make apply
```

Here come our mistakes))
``log
...
module.gke.null_resource.configure_kubectl: Creating...
module.gke.null_resource.configure_kubectl: Provisioning with 'local-exec'...
module.gke.null_resource.configure_kubectl (local-exec): Executing: ["/bin/sh" "-c" "gcloud beta container clusters get-credentials reddit-private --region us-central1 --project docker-257914"]
module.gke.null_resource.configure_kubectl (local-exec): Fetching cluster endpoint and auth data.
module.gke.null_resource.configure_kubectl (local-exec): ERROR: (gcloud.beta.container.clusters.get-credentials) ResponseError: code=404, message=Not found: projects/docker-257914/locations/us-central1/clusters/reddit private.
module.gke.null_resource.configure_kubectl (local-exec): Could not find [reddit-private] in [us-central1].
module.gke.null_resource.configure_kubectl (local-exec): Did you mean [reddit-private] in [us-central1-a]?


Error: Error running command 'gcloud beta container clusters get-credentials reddit-private --region us-central1 --project docker-257914': exit status 1. Output: Fetching cluster endpoint and auth data.
ERROR: (gcloud.beta.container.clusters.get-credentials) ResponseError: code=404, message=Not found: projects/docker-257914/locations/us-central1/clusters/reddit-private.
Could not find [reddit-private] in [us-central1].
Did you mean [reddit-private] in [us-central1-a]?




Error: Get https://35.238.240.243/apis/apps/v1/namespaces/kube-system/deployments/tiller-deploy: dial tcp 35.238.240.243:443: connect: connection refused

  on .terraform/modules/gke.tiller/modules/k8s-tiller/main.tf line 38, in resource "kubernetes_deployment" "tiller":
  38: resource "kubernetes_deployment" "tiller" {


Makefile:68: recipe for target 'apply' failed
make: *** [apply] Error 1
```
In this case, the cluster was not created.

A bit of dancing with a tambourine did not work. It's time for bed.

Destroying the inferno.
``hell.
terraform state rm module.gke.kubernetes_service_account.tiller
terraform state rm module.gke.kubernetes_cluster_role_binding.user
terraform state rm module.gke.module.tiller.kubernetes_service.tiller
make destroy
```


Let's use an example from https://github.com/gruntwork-io/terraform-google-gke/tree/master/examples/gke-private-cluster.

Let's move the current non-operating configuration to `kubernetes/terraform/donotwork`.

Let's add `gke-cluster` and `gke-cluster-account` modules to `kubernetes/terraform/modules`.

Take the files `main.tf`, `variables.tf` and `outputs.tf` from Pyrrhic https://github.com/gruntwork-io/terraform-google-gke/tree/master/examples/gke-private-cluster.

In [kubernetes/terraform/main.tf] (kubernetes/terraform/main.tf) correct the paths to the modules

File `kubernetes/terraform/terraform.tfvars` we have left from the previous attempt. It's relevant.

Let's initialize it.
``shell
make init
```

Let's check it out.
``shell
make tflint validate
```
``log
~/bin/tflint
~/bin/terraform --version
Terraform v0.12.18
+ provider.google v2.9.1
+ provider.google-beta v2.9.1
+ provider.random v2.2.1
~/bin/terraform validate
Success! The configuration is valid.
```

Let's apply infra
``shell
make apply
```
Yoo-hoo!
``log
...
Apply complete! Resources: 16 added, 0 changed, 0.

Outputs:

client_certificate = 
client_key = <sensitive>
cluster_ca_certificate = <sensitive>
cluster_endpoint = <sensitive>
```

Configure `Kubectl`
``shell
gcloud container clusters get-credentials reddit-private --zone us-central1-a --project docker-<project_id>
```

Check out .
``shell
kubectl cluster-info
```
``log
Kubernetes master is running at https://35.222.6.91.
calico-typha is running at https://35.222.6.91/api/v1/namespaces/kube-system/services/calico-typha:calico-typha/proxy.
GLBCDefaultBackend is running at https://35.222.6.91/api/v1/namespaces/kube-system/services/default-http-backend:http/proxy.
Heapster is running at https://35.222.6.91/api/v1/namespaces/kube-system/services/heapster/proxy.
KubeDNS is running at https://35.222.6.91/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy.
Metrics-server is running at https://35.222.6.91/api/v1/namespaces/kube-system/services/https:metrics-server:/proxy.
```

Let's create a neimscape.
``shell
kubectl apply -f ./kubernetes/reddit/dev-namespace.yml 
```
``log
namespace/dev created
```

Deploymer application
``shell
kubectl -n dev apply -f ./kubernetes/reddit/                 
```
``log
deployment.apps/comment created
service/comment-db created
service/comment created
namespace/dev unchanged
deployment.apps/mongo created
service/mongodb created
deployment.apps/post created
service/post-db created
service/post created
deployment.apps/ui created
service/ui created
```

Check out .
``shell
kubectl -n dev get deployments 
```
``log
NAME READY UP-TO-DATE AVAILABLE AGE
comment 3/3 3 3 39s
mongo 1/1 1 1 55s
post 3/3 3 3 54s
ui 3/3 3 3 52s
```
``shell
kubectl -n dev get services
```
``log
NAME TYPE CLUSTER-IP EXTERNAL-IP PORT(S) AGE
comment ClusterIP 10.4.13.2 <none> 9292/TCP 2m15s
comment-db ClusterIP 10.4.3.21 <none> 27017/TCP 2m16s
mongodb ClusterIP 10.4.14.40 <none> 27017/TCP 2m31s
post ClusterIP 10.4.0.179 <none> 5000/TCP 2m30s
post-db ClusterIP 10.4.4.7 <none> 27017/TCP 2m30s
ui NodePort 10.4.9.143 <none> 9292:30652/TCP 2m29s
```
``shell
kubectl -n dev get pods --selector component=ui
```
``log
NAME READY STATUS RESTARTS AGE
ui-595f89d499-9qmsm 1/1 Running 0 3m18s
ui-595f89d499-d5b47 1/1 Running 0 3m18s
ui-595f89d499-z57wg 1/1 Running 0 3m18s
```
``shell
kubectl -n dev port-forward ui-595f89d499-9qmsm 9292:9292
```
``log
Forwarding from 127.0.0.1:9292 -> 9292
Forwarding from [::1]:9292 -> 9292
```
The application is available at http://127.0.0.1:9292 and works.

``shell
kubectl describe service ui -n dev | grep NodePort
```
``log
Type: NodePort
NodePort: <unset> 30652/TCP
```
``shell
kubectl get nodes -o wide
```
``log
NAME STATUS ROLES AGE VERSION INTERNAL-IP EXTERNAL-IP OS-IMAGE KERNEL-VERSION CONTAINER-RUNTIME
gke-reddit-private-private-pool-02dd335c-65rz Ready <none> 26m v1.15.4-gke.22 10.3.0.4 Container-Optimized OS from Google 4.19.76+ docker://19.3.1
gke-reddit-private-private-pool-02dd335c-j19w Ready <none> 34m v1.15.4-gke.22 10.3.0.3 Container-Optimized OS from Google 4.19.76+ docker://19.3.1
```

Since the cluster is private, no external addresses. There's nothing to connect to =)

Destroy:
``shell
cd kubernetes/terraform
make destroy
```
``log
Destroy complete! Resources: 16.
```

Move the current configuration to `kubernetes/terraform/private-cluster`.


Let's try the **public-cluster**, again without the killer.

Take a sample configuration from https://github.com/gruntwork-io/terraform-google-gke/tree/master/examples/gke-public-cluster.

In [kubernetes/terraform/main.tf] (kubernetes/terraform/main.tf) correct the paths to the modules

In the file `kubernetes/terraform/terraform.tfvars` let's correct the cluster name to `reddit-public` and remove the unused variable `master_ipv4_cidr_block = "10.5.0.0/28".

Let's initialize
``shell
make init
```

Let's check it out.
``shell
make tflint validate
```
all right

We apply .
``shell
make apply
```
``log
Apply complete! Resources: 16 added, 0 changed, 0.

Outputs:

client_certificate = 
client_key = <sensitive>
cluster_ca_certificate = <sensitive>
cluster_endpoint = <sensitive>
```

kubectl
``shell
gcloud container clusters get-credentials reddit-public --zone us-central1-a --project docker-<project_id>
```

Deploym
``shell
kubectl apply -f ./kubernetes/reddit/dev-namespace.yml
kubectl -n dev apply -f ./kubernetes/reddit/
```

Check out .
``shell
kubectl -n dev get nodes -o wide
```
``log
NAME STATUS ROLES AGE VERSION INTERNAL-IP EXTERNAL-IP OS-IMAGE KERNEL-VERSION CONTAINER-RUNTIME
gke-reddit-public-main-pool-55932370-0jm2 Ready <none> 73s v1.15.4-gke.22 10.3.0.6 35.226.120.37 Container-Optimized OS from Google 4.19.76+ docker://19.3.1
gke-reddit-public-main-pool-55932370-6fg2 Ready <none> 6m46s v1.15.4-gke.22 10.3.0.4 35.192.163.208 Container-Optimized OS from Google 4.19.76+ docker://19.3.1
gke-reddit-public-main-pool-55932370-fvqw Ready <none> 2m41s v1.15.4-gke.22 10.3.0.5 35.225.118.4 Container-Optimized OS from Google 4.19.76+ docker://19.3.1
gke-reddit-public-main-pool-55932370-pwcw Ready <none> 14m v1.15.4-gke.22 10.3.0.3 35.238.28.0 Container-Optimized OS from Google 4.19.76+ docker://19.3.1
```

``shell
kubectl describe service ui -n dev | grep NodePort
```
``log
Type: NodePort
NodePort: <unset> 31572/TCP
```

Check out http://35.192.163.208:31572.

The application opens.
![reddit-gke.png](kubernetes/img/reddit-gke.png)


## HomeWork 21: Kubernetes. Networks, Storages

### Plan

- Ingress Controller
- Ingress
- Secret
- TLS
- LoadBalancer Service
- Network Policies
- PersistentVolumes
- PersistentVolumeClaims .


### Networking

In our previous work we have already configured network communication with the application in Kubernetes using **Service** - an abstraction that defines the access endpoints and how to communicate with them (nodePort, LoadBalancer, ClusterIP). Let's take a closer look at what this gives us in reality.

**Service** - defines **endpoints** (Endpoints):
- selector services (k8s finds PODs by label itself).
- selectorless services (we manually describe specific endpoints)

and **the way to communicate** with them (type of service):
- ClusterIP - you can reach the service only from inside the cluster
- nodePort - the client outside the cluster comes to the published port
- LoadBalancer - client comes to the cloud (aws elb, Google gclb) balancing resource
- ExternalName - external resource in relation to the cluster


#### Service

Let's remember what the services looked like:
``Yaml
---
apiVersion: v1
kind: Service
metadata:
  name: post
  The labels:
    app: reddit
    post
spec:
  ports:
  - port: 5000
    protocol: TCP
    targetPort: 5000
  Selector:
    app: reddit
    post
```
This is a **ClusetrIP** type selector service (the type is not specified since this type is the default one).

**ClusterIP** is a virtual (in reality there is no interface, pod or machine with such address) IP address from address range for operation inside, hiding the IP addresses of real PODs. The service ** of any type** (except ExternalName) is assigned this IP address. 

``shell
kubectl get services -n dev
```
``log
NAME TYPE CLUSTER-IP EXTERNAL-IP PORT(S) AGE
comment ClusterIP 10.4.11.91 <none> 9292/TCP 37s
comment-db ClusterIP 10.4.1.197 <none> 27017/TCP 37s
mongodb ClusterIP 10.4.8.107 <none> 27017/TCP 36s
post ClusterIP 10.4.14.164 <none> 5000/TCP 34s
post-db ClusterIP 10.4.2.83 <none> 27017/TCP 35s
ui NodePort 10.4.14.189 <none> 9292:31596/TCP 33s
```

The scheme of interaction
! [Communication Scheme Service](kubernetes/img/scheme-service.png)


#### Kube-dns

It should be noted that **Service** is just an abstract and description of how to access the service. But it relies on real mechanisms and objects: DNS-server, balancers, iptables.

In order to get to the service, we need to know its address by name. Kubernetes does not have its own DNS server for name resolution. So the **kube-dns** plugin is used (it's also Pod).

Its tasks:
- go to the Kubernetes API and track service-objects
- maintain a DNS record of the Services
- provide a DNS service to resolve names in IP addresses (both internal and external)

The scheme takes the following form
![Kube-dns interaction scheme](kubernetes/img/scheme-kube-dns.png)

You can make sure that with the **kube-dns** service disabled, the connectivity between the components of the reddit-app will disappear and it will stop working.

1. Proskaylim at 0 is the service that makes sure that there are always enough dns-kube-dns**.
   ``shell
   kubectl scale deployment --replicas 0 -n kube-system kube-dns-autoscaler
   ```
   ``log
   deployment.extensions/kube-dns-autoscaler scaled
   ```
2. Proskaylim at 0 kube-dns himself.
   ``shell
   kubectl scale deployment --replicas 0 -n kube-system kube-dns
   ```
   ``log
   deployment.extensions/kube-dns scaled
   ```
3. Try to get through to any service by name. For example .
   ``shell
   kubectl exec -ti -n dev post-f669799bf-dw6d9 ping comment
   ```
   ``log
   ping: bad address 'comment'
   command terminated with exit code 1
   ```
4. Let's get the kube-dns-autoscale back to the original...
   ``shell
   kubectl scale deployment --replicas 1 -n kube-system kube-dns-autoscaler
   ```
   ``log
   deployment.extensions/kube-dns-autoscaler scaled
   ```
5. Check that the application is running (in your browser).
   Yes, it does.


#### Service

As already mentioned, **ClusterIP** is virtual and does not belong to any real physical entity. Its reading and further actions with packets belonging to it are performed in our case by **iptables**, which is configured by **kube-proxy** utility (taking info from API-server).

The kube-proxy itself can be configured to receive traffic, but this is outdated behavior and **kube-proxy** is not recommended to apply it.

You can see these IPTABLES rules on any of the cluster nodes (this is not a task).

I'll just save it here...

<details><summary>Memory =))</summary>.
<p>

``shell
sudo iptables -vnL
```
``log
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target prot opt in out source destination         
53438 361M cali-INPUT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:Cz_u1IQiXIMmKD4c */
  814 47087 KUBE-SERVICES all -- * * 0.0.0.0/0 0.0.0/0 ctstate NEW /* kubernetes service portals */
  814 47087 KUBE-EXTERNAL-SERVICES all -- * * 0.0.0.0/0 0.0.0/0 ctstate NEW /* kubernetes externally-visible service portals */
65799 652M KUBE-FIREWALL all -- * 0.0.0.0/0 0.0.0/0           
65880 675M ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 state RELATED,ESTABLISHED
  698 41880 ACCEPT all -- lo * 0.0.0.0/0 0.0.0/0           
    1 68 ACCEPT icmp -- * * 0.0.0.0/0 0.0.0/0           
    7 404 ACCEPT tcp -- * * 0.0.0.0/0 0.0.0/0 tcp dpt:22
  163 6880 ACCEPT tcp -- * * 0.0.0.0/0 0.0.0.0/0           
    4 243 ACCEPT udp -- * * 0.0.0.0/0 0.0.0/0           
    0 0 ACCEPT icmp -- * * 0.0.0.0/0 0.0.0/0           
    0 0 ACCEPT sctp -- * * 0.0.0.0/0 0.0.0/0           

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target prot opt in out source destination         
 208K 56M cali-FORWARD all -- * * 0.0.0.0/0 0.0.0/0 /* cali:wUHhoiAYhphO9Mso */
    0 0 KUBE-FORWARD all -- * * 0.0.0.0/0 0.0.0/0 /* kubernetes forwarding rules */
    0 0 KUBE-SERVICES all -- * * 0.0.0.0/0 0.0.0/0 ctstate NEW /* kubernetes service portals */
    0 0 DOCKER-USER all -- * * 0.0.0.0/0 0.0.0/0           
    0 0 DOCKER-ISOLATION-STAGE-1 all -- * 0.0.0.0/0 0.0.0/0           
    0 0 ACCEPT all -- * docker0 0.0.0.0/0 0.0.0/0 ctstate RELATED,ESTABLISHED
    0 0 DOCKER all -- * docker0 0.0.0.0/0 0.0.0/0           
    0 0 ACCEPT all -- docker0 !docker0 0.0.0.0/0 0.0.0/0           
    0 0 ACCEPT all -- docker0 docker0 0.0.0.0/0 0.0.0/0           
    0 0 ACCEPT tcp -- * * 0.0.0.0/0 0.0.0/0           
    0 0 ACCEPT udp -- * * 0.0.0.0/0 0.0.0/0           
    0 0 ACCEPT icmp -- * * 0.0.0.0/0 0.0.0/0           
    0 0 ACCEPT sctp -- * * 0.0.0.0/0 0.0.0/0           

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target prot opt in out source destination         
46607 51M cali-OUTPUT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:tVnHkvAo15HuiPy0 */
 7676 463K KUBE-SERVICES all -- * * 0.0.0.0/0 0.0.0/0 ctstate NEW /* kubernetes service portals */
65017 53M KUBE-FIREWALL all -- * 0.0.0.0/0 0.0.0/0           
66006 53M ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 state NEW,RELATED,ESTABLISHED
    0 0 ACCEPT all -- * lo 0.0.0.0/0 0.0.0/0           

Chain DOCKER (1 references)
 pkts bytes target prot opt in out source destination         

Chain DOCKER-ISOLATION-STAGE-1 (1 reference)
 pkts bytes target prot opt in out source destination         
    0 0 DOCKER-ISOLATION-STAGE-2 all -- docker0 !docker0 0.0.0.0/0 0.0.0.0/0           
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0           

Chain DOCKER-ISOLATION-STAGE-2 (1 reference)
 pkts bytes target prot opt in out source destination         
    0 0 DROP all -- * docker0 0.0.0.0/0 0.0.0/0           
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0           

Chain DOCKER-USER (1 references)
 pkts bytes target prot opt in out source destination         
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0           

Chain KUBE-EXTERNAL-SERVICES (1 reference)
 pkts bytes target prot opt in out source destination         

Chain KUBE-FIREWALL (2 references)
 pkts bytes target prot opt in out source destination         
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* kubernetes firewall for dropping marked packets */ mark match 0x8000/0x8000

Chain KUBE-FORWARD (1 references)
 pkts bytes target prot opt in out source destination         
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 ctstate INVALID
    0 0 ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* kubernetes forwarding rules */ mark match 0x4000/0x4000
    0 0 ACCEPT all -- * * 10.4.0.0/20 0.0.0.0/0 /* kubernetes forwarding conntrack pod source rule */ ctstate RELATED,ESTABLISHED
    0 0 ACCEPT all -- * * 0.0.0.0/0 10.4.0.0/20 /* kubernetes forwarding conntrack pod destination rule */ ctstate RELATED,ESTABLISHED

Chain KUBE-SERVICES (3 references)
 pkts bytes target prot opt in out source destination         

Chain cali-FORWARD (1 references)
 pkts bytes target prot opt in out source destination         
 208K 56M MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:vjrMJCRpqwy5oRoX */ MARK and 0xfff1ffffff
 208K 56M cali-from-hep-forward all -- * * 0.0.0.0/0 0.0.0/0 /* cali:A_sPAO0mcxbT9mOV */ mark match 0x0/0x10000
 169K 29M cali-from-wl-dispatch all -- cali+ * 0.0.0.0/0 0.0.0/0 /* cali:8ZoYfO5HKXWbB3pk */
50081 28M cali-to-wl-dispatch all -- * cali+ 0.0.0.0/0 0.0.0/0 / * cali:jdEuaPBe14V2hutn */
14867 1010K cali-to-hep-forward all -- * * 0.0.0.0/0 0.0.0/0 /* cali:12bc6HljsMKsmfr -- */
14867 1010K ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:MH9kMp5aNICL-Olv */ /* Policy explicitly accepted packet. */ mark match 0x10000/0x10000

Chain cali-INPUT (1 references)
 pkts bytes target prot opt in out source destination         
 5314 864K cali-wl-to-host all -- cali+ * 0.0.0.0/0 0.0.0.0/0 [goto] /* cali:FewJpBykm9iJ-YNH */
    0 0 ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:hder3ARWznqqv8Va */ mark match 0x10000/0x10000
48124 360M MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:xgOu2uJft6H9oDGF */ MARK and 0xfff0ffffff.
48124 360M cali-from-host-endpoint all -- * * 0.0.0.0/0 0.0.0/0 /* cali:_-d-qojMfHM6NwBo */
    0 0 ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:LqmE76MP94lZTGhA */ /* Host endpoint policy accepted packet. */ mark match 0x10000/0x10000

Chain cali-OUTPUT (1 references)
 pkts bytes target prot opt in out source destination         
    0 0 ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:Mq1_rAdXXH3YkrzW */ mark match 0x10000/0x10000
 6470 7016K RETURN all -- * cali+ 0.0.0.0/0 0.0.0/0 /* cali:69FkRTJDvD5Vu6Vl */
40137 44M MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:Fskumj4SGQtDV6GC */ MARK and 0xfff0ffffff.
40137 44M cali-to-host-endpoint all -- * * 0.0.0.0/0 0.0.0/0 /* cali:8rXMdo5sNesjJxGc */
    0 0 ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:Ja-pnrHi-PrNKxgd */ /* Host endpoint policy accepted packet. */ mark match 0x10000/0x10000

Chain cali-failsafe-in (0 references)
 pkts bytes target prot opt in out source destination         
    0 0 ACCEPT tcp -- * * 0.0.0.0/0 0.0.0/0 /* cali:wWFQM43tJU7wwnFZ */ multiport dports 22
    0 0 ACCEPT udp -- * * 0.0.0.0/0 0.0.0/0 /* cali:LwNV--R8MjeUYacw */ multiport dports 68
    0 0 ACCEPT tcp -- * * 0.0.0.0/0 0.0.0/0 /* cali:QOO5NUOqOSS1_Iw0 */ multiport dports 179
    0 0 ACCEPT tcp -- * * 0.0.0.0/0 0.0.0/0 /* cali:cwZWoBSwVeIAZmVN */ multiport dports 2379
    0 0 ACCEPT tcp -- * * 0.0.0.0/0 0.0.0/0 /* cali:7FbNXT91kugE_upR */ multiport dports 2380
    0 0 ACCEPT tcp -- * * 0.0.0.0/0 0.0.0/0 /* cali:ywE9WYUBEpve70WT */ multiport dports 6666
    0 0 ACCEPT tcp -- * * 0.0.0.0/0 0.0.0/0 /* cali:l-WQSVBf_lygPR0J */ multiport dports 6667

Chain cali-failsafe-out (0 references)
 pkts bytes target prot opt in out source destination         
    0 0 ACCEPT udp -- * * 0.0.0.0/0 0.0.0/0 /* cali:82hjfji-wChFhAqL */ multiport dports 53
    0 0 ACCEPT udp -- * * 0.0.0.0/0 0.0.0/0 /* cali:TNM3RfEjbNr72hgH */ multiport dports 67
    0 0 ACCEPT tcp -- * * 0.0.0.0/0 0.0.0/0 /* cali:ycxKitIl4u3dK0HR */ multiport dports 179
    0 0 ACCEPT tcp -- * * 0.0.0.0/0 0.0.0/0 /* cali:hxjEWyxdkXXkdvut */ multiport dports 2379
    0 0 ACCEPT tcp -- * * 0.0.0.0/0 0.0.0/0 /* cali:cA_GLtruuvG88KiO */ multiport dports 2380
    0 0 ACCEPT tcp -- * * 0.0.0.0/0 0.0.0/0 /* cali:Sb1hkLYFMrKS6r01 */ multiport dports 6666
    0 0 ACCEPT tcp -- * * 0.0.0.0/0 0.0.0/0 /* cali:UwLSebGONJUG4yG- */ multiport dports 6667

Chain cali-from-hep-forward (1 references)
 pkts bytes target prot opt in out source destination         

Chain cali-from-host-endpoint (1 references)
 pkts bytes target prot opt in out source destination         

Chain cali-from-wl-dispatch (2 references)
 pkts bytes target prot opt in out source destination         
26847 10M cali-from-wl-dispatch-0 all -- cali0+ * 0.0.0.0/0 0.0.0/0 [goto] /* cali:eBnVcASLTvMFg9XV */
22141 1898K cali-fw-cali1c39897f10f all -- cali1c39897f10f * 0.0.0.0/0 0.0.0/0 [goto] /* cali:YwGqMCK1MmmSv6Le */
20956 1805K cali-fw-cali22841037ef8 all -- cali22841037ef8 * 0.0.0.0/0 0.0.0/0 [goto] /* cali:JFYgBz0ZNFTssa-f */
19319 1674K cali-fw-cali363f791ae66 all -- cali363f791ae66 * 0.0.0.0/0 0.0.0/0 [goto] /* cali:ajMSJf0l60P0Gtp5 */
 6803 732K cali-from-wl-dispatch-4 all -- cali4+ * 0.0.0.0/0 0.0.0/0 [goto] /* cali:a6kOIPK0SZHufacD */
 6706 592K cali-fw-cali923f86f51da all -- cali923f86f51da * 0.0.0.0/0 0.0.0/0 [goto] /* cali:3u_wj81qX_vEk3Q- */
 1823 253K cali-fw-caliaf6bd9e3dd6 all -- caliaf6bd9e3dd6 * 0.0.0.0/0 0.0.0/0 [goto] /* cali:eAeOnHbk1kpin4em */
 8768 1015K cali-from-wl-dispatch-b all -- calib+ * 0.0.0.0/0 0.0.0/0 [goto] /* cali:tzMfaZdywQYSvoo2 */
 5884 2792K cali-from-wl-dispatch-c all -- calic+ * 0.0.0.0/0 0.0.0/0 [goto] /* cali:3MJs-_opMia0f4Rm */
 6246 743K cali-from-wl-dispatch-d all -- calid+ * 0.0.0.0/0 0.0.0/0 [goto] /* cali:Tl1PKTnmPw9uzJkx */
39727 6345K cali-fw-calie2cee35dbce all -- calie2cee35dbce * 0.0.0.0/0 0.0.0/0 [goto] /* cali:QSJVZTBpAsx1zvNp */
  967 70682 cali-from-wl-dispatch-f all -- calif+ * 0.0.0.0/0 0.0.0/0 [goto] /* cali:NcnkXfjTNRTtWF2U */
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:2kcJkvBUN9sENHd4 */ /* Unknown interface */

Chain cali-from-wl-dispatch-0 (1 references)
 pkts bytes target prot opt in out source destination         
 1139 109K cali-fw-cali001f6121953 all -- cali001f6121953 * 0.0.0.0/0 0.0.0/0 [goto] /* cali:jBZAU2VaZGUh77Xm */
 7527 665K cali-fw-cali02bcd13d7d7 all -- cali02bcd13d7d7 * 0.0.0.0/0 0.0.0/0 [goto] /* cali:HOqxFqWLr-ZO36Xi */
12084 6413K cali-fw-cali0e254ef053c all -- cali0e254ef053c * 0.0.0.0/0 0.0.0/0 [goto] /* cali:DGFf8o_63lIC1otM */
 3253 330K cali-fw-cali0e4c83da0c2 all -- cali0e4c83da0c2 * 0.0.0.0/0 0.0.0/0 [goto] /* cali:68YMcLF3QFfEPeDd */
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:H6oxmvQm7jzkmVvz */ /* Unknown interface */

Chain cali-from-wl-dispatch-4 (1 references)
 pkts bytes target prot opt in out source destination         
 3548 402K cali-fw-cali487296ebfc4 all -- cali487296ebfc4 * 0.0.0.0/0 0.0.0/0 [goto] /* cali:ys2-Uaw6Jsde6svB */
 3255 330K cali-fw-cali4bbcf1021d6 all -- cali4bbcf1021d6 * 0.0.0.0/0 0.0.0/0 [goto] /* cali:v9yFglWgSTCDBg9D */
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:OgoZoDSsTNY81Q81 */ /* Unknown interface */

Chain cali-from-wl-dispatch-b (1 references)
 pkts bytes target prot opt in out source destination         
 8535 997K cali-fw-calib56d958096f all -- calib56d958096f * 0.0.0.0/0 0.0.0/0 [goto] /* cali:ONtrypv994sUb1ed */
  233 17576 cali-fw-calibafc89b76e6 all -- calibafc89b76e6 * 0.0.0.0/0 0.0.0/0 [goto] /* cali:VkGOpe9vy9gvtIQj */
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:riCKkh0gDzA7JgZC */ /* Unknown interface */

Chain cali-from-wl-dispatch-c (1 references)
 pkts bytes target prot opt in out source destination         
 3334 372K cali-fw-calic0784236d5f all -- calic0784236d5f * 0.0.0.0/0 0.0.0/0 [goto] /* cali:A7lfuX6Uyl3hmrIr */
 3266 2674K cali-fw-calicf8b0d0baf2 all -- calicf8b0d0baf2 * 0.0.0.0/0 0.0.0/0 [goto] /* cali:mFmTsLZB2xSiPZVH */
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:_uFal064WAFqpoLc */ /* Unknown interface */

Chain cali-from-wl-dispatch-d (1 references)
 pkts bytes target prot opt in out source destination         
  627 388K cali-fw-calid7820f5c789 all -- calid7820f5c789 * 0.0.0.0/0 0.0.0/0 [goto] /* cali:FiKz92o2owXLNkgB */
 6183 546K cali-fw-calid9ba32f8b18 all -- calid9ba32f8b18 * 0.0.0.0/0 0.0.0/0 [goto] /* cali:H_jyYB-0cHpir3EP */
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:whN6qOf6uJ_l5Vsf */ /* Unknown interface */

Chain cali-from-wl-dispatch-f (1 references)
 pkts bytes target prot opt in out source destination         
  557 57701 cali-fw-calif320a18605b all -- calif320a18605b * 0.0.0.0/0 0.0.0/0 [goto] /* cali:m9FbNszH5xdcZ_mp */
  983 71983 cali-fw-calif9eb280ec40 all -- calif9eb280ec40 * 0.0.0.0/0 0.0.0/0 [goto] /* cali:7F05c3vUzG6GggKUi */
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:ta-GyXjBcPdloCT5 */ /* Unknown interface */

Chain cali-fw-cali001f6121953 (1 reference)
 pkts bytes target prot opt in out source destination         
 1139 109K ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:Px3fyfs-OWCy61Fl */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:Y9DW__V6n_-VSzBo */ ctstate INVALID
    0 0 MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:qTP6GkhkhwIj7jqfz1 */ MARK and 0xfffeffff.
    0 0 DROP udp -- * * 0.0.0.0/0 0.0.0/0 /* cali:TdxzA6P0wnrzwjhf */ /* Drop VXLAN encapped packets originating in pods */ multiport dports 4789
    0 0 DROP 4 -- * * 0.0.0.0/0 0.0.0/0 /* cali:_ZJ4AcbqEy-Pb4-K */ /* Drop IPinIP encapped packets originating in pods */
    0 0 cali-pro-kns.kube-system all -- * * 0.0.0.0/0 0.0.0/0 /* cali:vgCKwslxqisvRpnH */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:NUbo3vj4Nla9dWQS */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pro-_hNSGmJYNT8uLIzxesP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:bGQfPPstg74m3Ut4 */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:JNkN9_LyoIusLt8s */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:03KT1t2H33gpjqWj */ /* Drop if no profiles matched */

Chain cali-fw-cali02bcd13d7d7 (1 reference)
 pkts bytes target prot opt in out source destination         
 6032 562K ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:-ubTqYvbNLHMpUL2 */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:Po2AtsMlhCakv67L */ ctstate INVALID
 1495 104K MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:WbUkeqZd1jfS-AXN */ MARK and 0xfffeffffff
    0 0 DROP udp -- * * 0.0.0.0/0 0.0.0/0 /* cali:Tv9OVyHpF-BLc9C7 */ /* Drop VXLAN encapped packets originating in pods */ multiport dports 4789
    0 0 DROP 4 -- * * 0.0.0.0/0 0.0.0/0 /* cali:1VBYHKj5xiai5T9k */ /* Drop IPinIP encapped packets originating in pods */
 1495 104K cali-pro-kns.dev all -- * * 0.0.0.0/0 0.0.0/0 /* cali:JO19z2-iPX9eCo2 -- */
 1495 104K RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:7flArWKMyjuwNBst */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pro-ksa.dev.default all -- * * 0.0.0.0/0 0.0.0/0 / * cali:-K6eVH-i5lhI1Cg9 */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:I-tr78bwhFGKSNKG */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:iL90AUvCPJaYbBnh */ /* Drop if no profiles matched */

Chain cali-fw-cali0e254ef053c (1 reference)
 pkts bytes target prot opt in out source destination         
14858 9257K ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:rB1B8PH9cT32R9Fx */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:gyCHJdHrKX7weSSe */ ctstate INVALID
   70 6535 MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:cjP76otkjm7KCkmN */ MARK and 0xfffeffffff
    0 0 DROP udp -- * * 0.0.0.0/0 0.0.0/0 /* cali:BizL9CdUPwTN6COy */ /* Drop VXLAN encapped packets originating in pods */ multiport dports 4789
    0 0 DROP 4 -- * * 0.0.0.0/0 0.0.0/0 /* cali:qYTXtdBd7DKNX3M9 */ /* Drop IPinIP encapped packets originating in pods */
   70 6535 cali-pro-kns.kube-system all -- * * 0.0.0.0/0 0.0.0/0 /* cali:AQWbI54CY1Gz9abM */
   70 6535 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:GvPfDHhRzgM3HkdX */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pro-_lk3uafp1xALKGJtCJN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:MThb8FJGWiQxTm3V */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:9rcGbODIUvLrP96p */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:7MOsCXvGUVrul2ck */ /* Drop if no profiles matched */

Chain cali-fw-cali0e4c83da0c2 (1 reference)
 pkts bytes target prot opt in out source destination         
 2717 298K ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:T7njsLRsI4-DKevm */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:l6xmXEYRtIuefGnN */ ctstate INVALID
  536 32160 MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:BztoOpiIwM8cScN2 */ MARK and 0xfffeffffff
    0 0 DROP udp -- * * 0.0.0.0/0 0.0.0/0 /* cali:b1uXclaSNDmxNC72 */ /* Drop VXLAN encapped packets originating in pods */ multiport dports 4789
    0 0 DROP 4 -- * * 0.0.0.0/0 0.0.0/0 /* cali:BYWqaPtLwiXmvFtj */ /* Drop IPinIP encapped packets originating in pods */
  536 32160 cali-pro-kns.dev all -- * * 0.0.0.0/0 0.0.0/0 /* cali:gOnaMLdf5DSZR4LT */
  536 32160 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:_YCv79TVIvJtFs8Y */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pro-ksa.dev.default all -- * * 0.0.0.0/0 0.0.0/0 /* cali:ydGmoBx9icARsgNy */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:31eTAImBf743KdIs */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:FrXrIk51ablmxrCs */ /* Drop if no profiles matched */

Chain cali-fw-cali1c39897f10f (1 reference)
 pkts bytes target prot opt in out source destination         
19191 1697K ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:zKLbgosYtLwC2ZdP */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:jlp45WaMWuFK2eOq */ ctstate INVALID
 2950 201K MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:uSX5XitJSgV4ueIi */ MARK and 0xfffeffffff
    0 0 DROP udp -- * * 0.0.0.0/0 0.0.0/0 /* cali:nY5hfNZo1C1eT-GG */ /* Drop VXLAN encapped packets originating in pods */ multiport dports 4789
    0 0 DROP 4 -- * * 0.0.0.0/0 0.0.0/0 /* cali:y6VEH15_knOZLezT */ /* Drop IPinIP encapped packets originating in pods */
 2950 201K cali-pro-kns.dev all -- * * 0.0.0.0/0 0.0.0/0 /* cali:pF1qhzzPrwVHmBBj */
 2950 201K RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:NSLCmAP_Wd9Hwxzy */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pro-ksa.dev.default all -- * * 0.0.0.0/0 0.0.0/0 /* cali:Vs_vNuPH0vMWur6t */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:I_4Y8zytOI2joqzj */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:5ONqSgwqeyep5ypF */ /* Drop if no profiles matched */

Chain cali-fw-cali22841037ef8 (1 reference)
 pkts bytes target prot opt in out source destination         
18086 1610K ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:41aWNLYH-fr3kjHy */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:Wctx9C3OtM1a8SOp */ ctstate INVALID
 2870 195K MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:dq0eD_ntajlHtCbB */ MARK and 0xfffeffffff.
    0 0 DROP udp -- * * 0.0.0.0/0 0.0.0/0 /* cali:RKP6LBVa5C4CSxJf */ /* Drop VXLAN encapped packets originating in pods */ multiport dports 4789
    0 0 DROP 4 -- * * 0.0.0.0/0 0.0.0/0 /* cali:eN1-pKoGffZViHTa */ /* Drop IPinIP encapped packets originating in pods */
 2870 195K cali-pro-kns.dev all -- * * 0.0.0.0/0 0.0.0/0 /* cali:gibx0MyqxYcXwj3B */
 2870 195K RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:y71_PBR7EFqifgKI */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pro-ksa.dev.default all -- * * 0.0.0.0/0 0.0.0/0 /* cali:jSTDx39U7eVulnYJ */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:MSnJV624_KG6Ds5t */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:HjAsM9kgaU11n64P */ /* Drop if no profiles matched */

Chain cali-fw-cali363f791ae66 (1 reference)
 pkts bytes target prot opt in out source destination         
16526 1486K ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:LHhoddF8XNyPBnxV */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:UT1rYd8HTaHEWhE5 */ ctstate INVALID
 2793 188K MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:_rBRj325qL2ktGMF */ MARK and 0xfffffeffff
    0 0 DROP udp -- * * 0.0.0.0/0 0.0.0/0 /* cali:JC4wmVlaQRf3X20d */ /* Drop VXLAN encapped packets originating in pods */ multiport dports 4789
    0 0 DROP 4 -- * * 0.0.0.0/0 0.0.0/0 /* cali:EIhzpNWMX7LJ4eds */ /* Drop IPinIP encapped packets originating in pods */
 2793 188K cali-pro-kns.dev all -- * * 0.0.0.0/0 0.0.0/0 /* cali:HpaeIzE3DbE8WYFN */
 2793 188K RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:BG90qH-6fixMEM8V */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pro-ksa.dev.default all -- * * 0.0.0.0/0 0.0.0/0 /* cali:OHKRBS4ENbGqNHIg */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:0t4jEFIoDPywD3p0 */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:86kR-N5VOVKaRtjv */ /* Drop if no profiles matched */

Chain cali-fw-cali487296ebfc4 (1 references)
 pkts bytes target prot opt in out source destination         
 4197 480K ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:gEomKhQ3MxACCjxD */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:jSXbW6Akfeh6taeu */ ctstate INVALID
    4 240 MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:fSjrSFg1pYo4ofVd */ MARK and 0xfffeffffff
    0 0 DROP udp -- * * 0.0.0.0/0 0.0.0/0 /* cali:hOVwrJLfIoFyKtTW */ /* Drop VXLAN encapped packets originating in pods */ multiport dports 4789
    0 0 DROP 4 -- * * 0.0.0.0/0 0.0.0/0 /* cali:6xQcOY2whnhC3CrT */ /* Drop IPinIP encapped packets originating in pods */
    4 240 cali-pro-kns.kube-system all -- * * 0.0.0.0/0 0.0.0/0 /* cali:0cSkFwTcW20apNeN */
    4 240 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:_LGkVSdp3S3cZEHe */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pro-_CVSZITRyIpEmH8AB6H all -- * * 0.0.0.0/0 0.0.0/0 /* cali:93p6RJ4LxCnXES0i */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:42HQ6FjjcFfIvV_ */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:bINO6OKSK50vsyUT */ /* Drop if no profiles matched */

Chain cali-fw-cali4bbcf1021d6 (1 reference)
 pkts bytes target prot opt in out source destination         
 2719 298K ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:39JfnVcYUQVU6M2D */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:VSQBf2jNy_pdamSL */ ctstate INVALID
  536 32160 MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:SvbuuYJ5nijxSj-u */ MARK and 0xfffeffffff.
    0 0 DROP udp -- * * 0.0.0.0/0 0.0.0/0 /* cali:lcFJ2tXIB1IXI9ag */ /* Drop VXLAN encapped packets originating in pods */ multiport dports 4789
    0 0 DROP 4 -- * * 0.0.0.0/0 0.0.0/0 /* cali:bvjb4Amag9c_WDYW */ /* Drop IPinIP encapped packets originating in pods */
  536 32160 cali-pro-kns.dev all -- * * 0.0.0.0/0 0.0.0/0 /* cali:C4cwgo9kCSls1_Wn */
  536 32160 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:5AKZqRMWR1Kj1v20 */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pro-ksa.dev.default all -- * * 0.0.0.0/0 0.0.0/0 /* cali:XZ5N-G1IduFhtfsq */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:JZNVKe1S1gH5OBOQ */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:iP9Z5Q9jWZIzwHVD */ /* Drop if no profiles matched */

Chain cali-fw-cali923f86f51da (1 references)
 pkts bytes target prot opt in out source destination         
 5396 502K ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:NMxuRJguwazvTdX1 */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:NZjs4pI79aS18SNE */ ctstate INVALID
 1310 90660 MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:pb0acG60DMo5Mk_8 */ MARK and 0xfffeffffff
    0 0 DROP udp -- * * 0.0.0.0/0 0.0.0/0 /* cali:ixg3-KMGe0QcA656 */ /* Drop VXLAN encapped packets originating in pods */ multiport dports 4789
    0 0 DROP 4 -- * * 0.0.0.0/0 0.0.0/0 /* cali:LZbp8ZpehVjHnxIK */ /* Drop IPinIP encapped packets originating in pods */
 1310 90660 cali-pro-kns.dev all -- * * 0.0.0.0/0 0.0.0/0 /* cali:A729Chz1ggFR2gzU */
 1310 90660 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:hvgiu_o-7wPl2RxM */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pro-ksa.dev.default all -- * * 0.0.0.0/0 0.0.0/0 /* cali:JWLmD0vBmtWDAXCL */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:fM5mzFRcA7ShLSHa */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:tbOX4-Bk9vyXuIos */ /* Drop if no profiles matched */

Chain cali-fw-caliaf6bd9e3dd6 (1 reference)
 pkts bytes target prot opt in out source destination         
 2131 304K ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:QEC5Y5tdh7SQlSek */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:OoHvYq1ISCRhYy8a */ ctstate INVALID
  131 7860 MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:lKw6a5Hp74p5GUXQ */ MARK and 0xfffeffffff
    0 0 DROP udp -- * * 0.0.0.0/0 0.0.0/0 /* cali:0jCi9I9CVRhL4WxR */ /* Drop VXLAN encapped packets originating in pods */ multiport dports 4789
    0 0 DROP 4 -- * * 0.0.0.0/0 0.0.0/0 /* cali:k0cW0pLemgy7ZWPD */ /* Drop IPinIP encapped packets originating in pods */
  131 7860 cali-pro-kns.kube-system all -- * * 0.0.0.0/0 0.0.0/0 /* cali:_nhCToLujHXu2ja9 */
  131 7860 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:A1GrPtX_x1Mxp2qc */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pro-_eSTHMIkNVbw_XFlWMl all -- * * 0.0.0.0/0 0.0.0/0 /* cali:GWdWyI_kXYCx5ewf */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:YbhN2lG9DbdLTOUT */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:8xNbYCCdNNAdi1gM */ /* Drop if no profiles matched */

Chain cali-fw-calib56d958096f (1 reference)
 pkts bytes target prot opt in out source destination         
 8525 996K ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:lm4VrVp7tzwZxhnq */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:aQC_LrZ9ajLR_XGR */ ctstate INVALID
   10 642 MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:VbZ6bCbDPO9tI0Mm */ MARK and 0xfffeffffff
    0 0 DROP udp -- * * 0.0.0.0/0 0.0.0/0 /* cali:u7YrkmvbEPfaBFM8 */ /* Drop VXLAN encapped packets originating in pods */ multiport dports 4789
    0 0 DROP 4 -- * * 0.0.0.0/0 0.0.0/0 /* cali:bY_8sZ5EXr7z1vxh */ /* Drop IPinIP encapped packets originating in pods */
   10 642 cali-pro-kns.kube-system all -- * * 0.0.0.0/0 0.0.0/0 /* cali:9dkDOvvvwyJfKjbbN */
   10 642 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:MtLrwxZJNdrijqrj */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pro-_cHTcjx4Xi7rghi4C9T all -- * * 0.0.0.0/0 0.0.0/0 /* cali:kPrOlU7IJXRfNiA8 */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:bJwnOUH3koeFcKsR */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:PUubp9Ycggsbm0b8 */ /* Drop if no profiles matched */

Chain cali-fw-calibafc89b76e6 (1 reference)
 pkts bytes target prot opt in out source destination         
  460 44287 ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:Y15SV3lmmqVQ_Dk2 */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:9wa-FwrMh_eHvPS1 */ ctstate INVALID
    3 180 MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:amBwWAgmKftdswzO */ MARK and 0xfffeffffff
    0 0 DROP udp -- * * 0.0.0.0/0 0.0.0/0 /* cali:gneME_L-9d6GTwjM */ /* Drop VXLAN encapped packets originating in pods */ multiport dports 4789
    0 0 DROP 4 -- * * 0.0.0.0/0 0.0.0/0 /* cali:r3X7Wrm9QxSXk__n */ /* Drop IPinIP encapped packets originating in pods */
    3 180 cali-pro-kns.kube-system all -- * * 0.0.0.0/0 0.0.0/0 /* cali:sdGAahAIsWkc3PzE */
    3 180 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:NSnHnCT5EJccX-WA */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pro-_hMH3axmCSxXO8wa164 all -- * * 0.0.0.0/0 0.0.0/0 /* cali:r99fXV1Tt-UeOZiq */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:bvAiUO86QMR-0SSE */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:Y8W0qqYS5-DXciYG */ /* Drop if no profiles matched */

Chain cali-fw-calic0784236d5f (1 references)
 pkts bytes target prot opt in out source destination         
 2790 339K ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:z8DLU4WH0tK_pNeY */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:i0s0NyvePQrKIv-E */ ctstate INVALID
  544 32640 MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:dKIU3RTctpdWmZYN */ MARK and 0xfffeffffff
    0 0 DROP udp -- * * 0.0.0.0/0 0.0.0/0 /* cali:eN8azJJSc57wBvCR */ /* Drop VXLAN encapped packets originating in pods */ multiport dports 4789
    0 0 DROP 4 -- * * 0.0.0.0/0 0.0.0/0 /* cali:Od2uQ5Rb2KLJw7I- */ /* Drop IPinIP encapped packets originating in pods */
  544 32640 cali-pro-kns.dev all -- * * 0.0.0.0/0 0.0.0/0 /* cali:M2fr7iRMY5cVDVNk */
  544 32640 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:MFlRYm4wwNusPDti */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pro-ksa.dev.default all -- * * 0.0.0.0/0 0.0.0/0 /* cali:rpjXnOnnTbvuHvmD */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:grhTzA94GHI73n4J */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:kXtwi8eSlfrO_Y6p */ /* Drop if no profiles matched */

Chain cali-fw-calicf8b0d0baf2 (1 reference)
 pkts bytes target prot opt in out source destination         
 3612 2826K ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:f-7GkEhlvJDQtejO */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:L918sIkgv6qRz9Cl */ ctstate INVALID
   83 7142 MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:9coQUxeVTvsF5zJ9 */ MARK and 0xfffeffffff
    0 0 DROP udp -- * * 0.0.0.0/0 0.0.0/0 /* cali:nLJ5HIDE2Sb_veS4 */ /* Drop VXLAN encapped packets originating in pods */ multiport dports 4789
    0 0 DROP 4 -- * * 0.0.0.0/0 0.0.0/0 /* cali:vf3v8IuXd1ZWl8rE */ /* Drop IPinIP encapped packets originating in pods */
   83 7142 cali-pro-kns.kube-system all -- * * 0.0.0.0/0 0.0.0/0 /* cali:wSKh0jJek9J7Bk4r */
   83 7142 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:WGpcERBUkZmJzmTC */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pro-_k7av1ffJ_LM_ftvh6m all -- * * 0.0.0.0/0 0.0.0/0 /* cali:pYeDldaKuF36Tvp4 */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:tVxzbDNzf4Xy91oC */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:s2pyVBi1sQBgR3mW */ /* Drop if no profiles matched */

Chain cali-fw-calid7820f5c789 (1 reference)
 pkts bytes target prot opt in out source destination         
 1102 830K ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:5RzDg_BdLFSPRXXZ */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:unoqDgBvVmB0kpF- */ ctstate INVALID
  111 9821 MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:S2CVqDDuV5sHU-0Z */ MARK and 0xfffeffffff
    0 0 DROP udp -- * * 0.0.0.0/0 0.0.0/0 /* cali:ajaQcu1bCEthAXTb */ /* Drop VXLAN encapped packets originating in pods */ multiport dports 4789
    0 0 DROP 4 -- * * 0.0.0.0/0 0.0.0/0 /* cali:kh5JEAcrSfhDXkkU */ /* Drop IPinIP encapped packets originating in pods */
  111 9821 cali-pro-kns.kube-system all -- * * 0.0.0.0/0 0.0.0/0 /* cali:1wyxHdU8w9209pxf */
  111 9821 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:JwTuAOpXVi0oIiTTT */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pro-_hHPqAGO7Sc_GcoojC_ all -- * * 0.0.0.0/0 0.0.0/0 /* cali:_PaL5Rs4B4WsNs37 */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:6DmxiAz9j64XMEAC */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:dzcVhIokWPTLDmgt */ /* Drop if no profiles matched */

Chain cali-fw-calid9ba32f8b18 (1 reference)
 pkts bytes target prot opt in out source destination         
 4982 463K ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:1Wfqk5REeoO1niMi */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:UBy-4KrMfLeqdh8p */ ctstate INVALID
 1201 83160 MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:dzaSerZ88KY7HHp7 */ MARK and 0xfffeffffff
    0 0 DROP udp -- * * 0.0.0.0/0 0.0.0/0 /* cali:v4L2w0qp6Biy8suR */ /* Drop VXLAN encapped packets originating in pods */ multiport dports 4789
    0 0 DROP 4 -- * * 0.0.0.0/0 0.0.0/0 /* cali:YPxpfd6BvbfxIQV */ /* Drop IPinIP encapped packets originating in pods */
 1201 83160 cali-pro-kns.dev all -- * * 0.0.0.0/0 0.0.0/0 /* cali:uOOCL15jiqGK03HC */
 1201 83160 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:ofSMeTJn2NOSHhQP */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pro-ksa.dev.default all -- * * 0.0.0.0/0 0.0.0/0 /* cali:J4kHvDMKEuhOfCdu */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:9QgGWyDoVLJv4LUf */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:-SZ59Etli-iVOIkh */ /* Drop if no profiles matched */

Chain cali-fw-calie2cee35dbce (1 references)
 pkts bytes target prot opt in out source destination         
40923 6518K ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:eHqmBNceeqXjDgBJ */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:jVQzxLMleWPJr7Vv */ ctstate INVALID
    0 0 MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:gef21Qa-EE-gMXpY */ MARK and 0xfffeffff.
    0 0 DROP udp -- * * 0.0.0.0/0 0.0.0/0 /* cali:YpLFY8QbFC8Cm8Ca */ /* Drop VXLAN encapped packets originating in pods */ multiport dports 4789
    0 0 DROP 4 -- * * 0.0.0.0/0 0.0.0/0 /* cali:iFE54T_3kSllIYKa */ /* Drop IPinIP encapped packets originating in pods */
    0 0 cali-pro-kns.dev all -- * * 0.0.0.0/0 0.0.0/0 /* cali:5f9ktfJM5j-38NPv */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:rMc4kzq4p3rf1Uhe */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pro-ksa.dev.default all -- * * 0.0.0.0/0 0.0.0/0 /* cali:JyBXrNV0ZRZdL4cE */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:o-GUf7WZP3w0j4AO */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:KvY_z2WTESM_gKhT */ /* Drop if no profiles matched */

Chain cali-fw-calif320a18605b (1 reference)
 pkts bytes target prot opt in out source destination         
  552 57401 ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:pOY6B-wCoyR3sp4H */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:wtl_5iZ-J8O4PHgX */ ctstate INVALID
    5 300 MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:g4uUlVgOGuTW7FWF */ MARK and 0xfffeffffff
    0 0 DROP udp -- * * 0.0.0.0/0 0.0.0/0 /* cali:0zxAsZyufLs_EExA */ /* Drop VXLAN encapped packets originating in pods */ multiport dports 4789
    0 0 DROP 4 -- * * 0.0.0.0/0 0.0.0/0 /* cali:CqX5Faqu3KdO5Kzy */ /* Drop IPinIP encapped packets originating in pods */
    5 300 cali-pro-kns.kube-system all -- * * 0.0.0.0/0 0.0.0/0 /* cali:0oj7zIfyw-4CTO3c */
    5 300 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:39JVLitK7h-fvyek */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pro-_hMH3axmCSxXO8wa164 all -- * * 0.0.0.0/0 0.0.0/0 /* cali:57McTa-EapLeGpOB */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:lIZsE2Y2v --rTWNf */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:GC6SJlT9oO7u1wzK */ /* Drop if no profiles matched */

Chain cali-fw-calif9eb280ec40 (1 reference)
 pkts bytes target prot opt in out source destination         
  982 71923 ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:KTvIvHb1oVxTwCu6 */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:TiSk3GM-tvwvvTSN */ ctstate INVALID
    1 60 MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:XjnpbzKuGGa29fjK */ MARK and 0xfffeffffff
    0 0 DROP udp -- * * 0.0.0.0/0 0.0.0/0 /* cali:L0xIIWP1I5lHx9Z5 */ /* Drop VXLAN encapped packets originating in pods */ multiport dports 4789
    0 0 DROP 4 -- * * 0.0.0.0/0 0.0.0/0 /* cali:rcO03ViiLJHegU9b */ /* Drop IPinIP encapped packets originating in pods */
    1 60 cali-pro-kns.kube-system all -- * * 0.0.0.0/0 0.0.0/0 /* cali:pZU8CRgfAZONXwpY */
    1 60 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:cK7Jlfw8H4F0z9vP */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pro-_uWYVxQhEtQLr5GFz7e all -- * * 0.0.0.0/0 0.0.0/0 /* cali:fMy8-GzbQF6i_CZl */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:rqUBlCWl1xbMUi1N */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:vKE9F3mGYhY4hvhe */ /* Drop if no profiles matched */

Chain cali-pri-_CVSZITRyIpEmH8AB6H (1 reference)
 pkts bytes target prot opt in out source destination         

Chain cali-pri-_cHTcjx4Xi7rghi4C9T (1 reference)
 pkts bytes target prot opt in out source destination         

Chain cali-pri-_eSTHMIkNVbw_XFlWMl (1 references)
 pkts bytes target prot opt in out source destination         

Chain cali-pri-_hHPqAGO7Sc_GcoojC_ (1 references)
 pkts bytes target prot opt in out source destination         

Chain cali-pri-_hMH3axmCSxXO8wa164 (2 references)
 pkts bytes target prot opt in out source destination         

Chain cali-pri-_hNSGmJYNT8uLIzxesP (1 reference)
 pkts bytes target prot opt in out source destination         

Chain cali-pri-_k7av1ffJ_LM_ftvh6m (1 reference)
 pkts bytes target prot opt in out source destination         

Chain cali-pri-_lk3uafp1xALKGJtCJN (1 references)
 pkts bytes target prot opt in out source destination         

Chain cali-pri-_uWYVxQhEtQLr5GFz7e (1 reference)
 pkts bytes target prot opt in out source destination         

Chain cali-pri-kns.dev (10 references)
 pkts bytes target prot opt in out source destination         
 7957 477K MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:Sb51wH5sSX-RNC8y */ MARK or 0x10000
 7957 477K RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:-YIiZJ8tSinqvR8O */ mark match 0x10000/0x10000

Chain cali-pri-kns.kube-system (10 references)
 pkts bytes target prot opt in out source destination         
 3334 262K MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:zoH5gU6U55FKZxEo */ MARK or 0x10000
 3334 262K RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:bcGRIJcyOS9dgBiB */ mark match 0x10000/0x10000

Chain cali-pri-ksa.dev.default (10 references)
 pkts bytes target prot opt in out source destination         

Chain cali-pro-_CVSZITRyIpEmH8AB6H (1 references)
 pkts bytes target prot opt in out source destination         

Chain cali-pro-_cHTcjx4Xi7rghi4C9T (1 reference)
 pkts bytes target prot opt in out source destination         

Chain cali-pro-_eSTHMIkNVbw_XFlWMl (1 references)
 pkts bytes target prot opt in out source destination         

Chain cali-pro-_hHPqAGO7Sc_GcoojC_ (1 references)
 pkts bytes target prot opt in out source destination         

Chain cali-pro-_hMH3axmCSxXO8wa164 (2 references)
 pkts bytes target prot opt in out source destination         

Chain cali-pro-_hNSGmJYNT8uLIzxesP (1 references)
 pkts bytes target prot opt in out source destination         

Chain cali-pro-_k7av1ffJ_LM_ftvh6m (1 reference)
 pkts bytes target prot opt in out source destination         

Chain cali-pro-_lk3uafp1xALKGJtCJN (1 references)
 pkts bytes target prot opt in out source destination         

Chain cali-pro-_uWYVxQhEtQLr5GFz7e (1 references)
 pkts bytes target prot opt in out source destination         

Chain cali-pro-kns.dev (10 references)
 pkts bytes target prot opt in out source destination         
14235 958K MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:Rq36gCa4CVFnKg-l */ MARK or 0x10000
14235 958K RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:AfNHltey0pfPbADe */ mark match 0x10000/0x10000

Chain cali-pro-kns.kube-system (10 references)
 pkts bytes target prot opt in out source destination         
  631 51728 MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:-50oJuMfLVO3LkBk */ MARK or 0x10000
  631 51728 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:ztVPKv1UYejNzm1g */ mark match 0x10000/0x10000

Chain cali-pro-ksa.dev.default (10 references)
 pkts bytes target prot opt in out source destination         

Chain cali-to-hep-forward (1 references)
 pkts bytes target prot opt in out source destination         

Chain cali-to-host-endpoint (1 references)
 pkts bytes target prot opt in out source destination         

Chain cali-to-wl-dispatch (1 references)
 pkts bytes target prot opt in out source destination         
21509 8343K cali-to-wl-dispatch-0 all -- * cali0+ 0.0.0.0/0 0.0.0/0 [goto] /* cali:dIkHjFD9PelLx7cm */
  841 80466 cali-tw-cali1c39897f10f all -- * cali1c39897f10f 0.0.0.0/0 0.0.0/0 [goto] /* cali:mjMiCxqvQ25LXH36 */
  869 83390 cali-tw-cali22841037ef8 all -- * cali22841037ef8 0.0.0/0 0.0.0.0/0 [goto] /* cali:1Bksax_YlcxK4Dj9 */
  835 79258 cali-tw-cali363f791ae66 all -- * cali363f791ae66 0.0.0.0/0 0.0.0.0/0 [goto] /* cali:ZhJ8R0gw7oF0J41l */
 2414 3928K cali-to-wl-dispatch-4 all -- * cali4+ 0.0.0.0/0 0.0.0/0 [goto] /* cali:X0zDVeDiHVol_ezt */
  770 71500 cali-tw-cali923f86f51da all -- * cali923f86f51da 0.0.0/0 0.0.0.0/0 [goto] /* cali:BJ9koW7kAXg5kG1E */
 1565 1098K cali-tw-caliaf6bd9e3dd6 all -- * caliaf6bd9e3dd6 0.0.0.0/0 0.0.0/0 [goto] /* cali:JQxniRlVOSdPLAKt */
 5288 2446K cali-to-wl-dispatch-b all -- * calib+ 0.0.0.0/0 0.0.0.0/0 [goto] /* cali:r9R8jA3zQl8F-ATq */
 2465 4128K cali-to-wl-dispatch-c all -- * calic+ 0.0.0.0/0 0.0.0.0/0 [goto] /* cali:Bi0C9ib0kd-VLiB- */
 1061 669K cali-to-wl-dispatch-d all -- * calid+ 0.0.0.0/0 0.0.0.0/0 [goto] /* cali:g5IMWbzehVXuxKC6 */
 6126 368K cali-tw-calie2cee35dbce all -- * calie2cee35dbce 0.0.0.0/0 0.0.0.0/0 [goto] /* cali:Ii2zTkQH1fTJnWg6 */
 1009 1332K cali-to-wl-dispatch-f all -- * calif+ 0.0.0.0/0 0.0.0.0/0 [goto] /* cali:wVIiMK5-E4ZJQwnq */
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:1Dqp_Do1wwHfEFs4 */ /* Unknown interface */

Chain cali-to-wl-dispatch-0 (1 reference)
 pkts bytes target prot opt in out source destination         
 1566 125K cali-tw-cali001f6121953 all -- * cali001f6121953 0.0.0/0 0.0.0.0/0 [goto] /* cali:L1tauWEUAXNPBGud */
  887 82420 cali-tw-cali02bcd13d7d7 all -- * cali02bcd13d7d7 0.0.0.0/0 0.0.0.0/0 [goto] /* cali:_kvShSEx4iI7md2I */
15619 5463K cali-tw-cali0e254ef053c all -- * cali0e254ef053c 0.0.0.0/0 0.0.0/0 [goto] /* cali:LU8juuhKmvKBL6xq */
    0 0 cali-tw-cali0e4c83da0c2 all -- * cali0e4c83da0c2 0.0.0.0/0 0.0.0.0/0 [goto] /* cali:qX1sFb5_0snBg_LH */
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:EnaUkyIqcT8I6y80 */ /* Unknown interface */

Chain cali-to-wl-dispatch-4 (1 reference)
 pkts bytes target prot opt in out source destination         
 2409 3927K cali-tw-cali487296ebfc4 all -- * cali487296ebfc4 0.0.0.0/0 0.0.0/0 [goto] /* cali:shCTscVbGhWnmndc */
    5 244 cali-tw-cali4bbcf1021d6 all -- * cali4bbcf1021d6 0.0.0.0/0 0.0.0.0/0 [goto] /* cali:E63OSiGMK9mVsXnw */
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:j0rotOeqW3Dg1jT9 */ /* Unknown interface */

Chain cali-to-wl-dispatch-b (1 references)
 pkts bytes target prot opt in out source destination         
 5100 1853K cali-tw-calib56d958096f all -- * calib56d958096f 0.0.0/0 0.0.0.0/0 [goto] /* cali:fkTWALhSeeO0d6ve */
  188 592K cali-tw-calibafc89b76e6 all -- * calibafc89b76e6 0.0.0.0/0 0.0.0.0/0 [goto] /* cali:qY5_Jd1wlfYaJEu */
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:DYADondVgQ8oOjtl */ /* Unknown interface */

Chain cali-to-wl-dispatch-c (1 references)
 pkts bytes target prot opt in out source destination         
   26 9544 cali-tw-calic0784236d5f all -- * calic0784236d5f 0.0.0.0/0 0.0.0.0/0 [goto] /* cali:meiz7ZtlnuUH8eyc */
 2882 5046K cali-tw-calicf8b0d0baf2 all -- * calicf8b0d0baf2 0.0.0.0/0 0.0.0/0 [goto] /* cali:pZRl1frF-E8xGPzL */
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:JfONqjZkYI3P8VG7 */ /* Unknown interface */

Chain cali-to-wl-dispatch-d (1 references)
 pkts bytes target prot opt in out source destination         
  705 752K cali-tw-calid7820f5c789 all -- * calid7820f5c789 0.0.0.0/0 0.0.0/0 [goto] /* cali:6fZT2wr4CzRGj8hy */
  698 64680 cali-tw-calid9ba32f8b18 all -- * calid9ba32f8b18 0.0.0/0 0.0.0.0/0 [goto] /* cali:4PoQY_-rtITnzy8F */
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:yH5yTRWx958TKkSp */ /* Unknown interface */

Chain cali-to-wl-dispatch-f (1 references)
 pkts bytes target prot opt in out source destination         
  474 824K cali-tw-calif320a18605b all -- * calif320a18605b 0.0.0.0/0 0.0.0.0/0 [goto] /* cali:ADLBor9HQznv3rXi */
 1086 1010K cali-tw-calif9eb280ec40 all -- * calif9eb280ec40 0.0.0.0/0 0.0.0.0/0 [goto] /* cali:a_qGfoBTL27efSbE */
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:08sJ_1yK54nT-Ii7 */ /* Unknown interface */

Chain cali-tw-cali001f6121953 (1 reference)
 pkts bytes target prot opt in out source destination         
    0 0 ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:RZ8y89bIXGAaVu3n */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:yb9GkCnGxP5V8fq6 */ ctstate INVALID
 1566 125K MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:PkYBXA-xdyTrhh6o */ MARK and 0xfffeffffff
 1566 125K cali-pri-kns.kube-system all -- * * 0.0.0.0/0 0.0.0/0 /* cali:g3ftsvmAGqPFb1c- */
 1566 125K RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:PkEBMOS5rlF-xjFN */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pri-_hNSGmJYNT8uLIzxesP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:qp5zyjrJ1wvxyJKW */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:l54GqDlz6OkJnRBg */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:6uBWxadt_-y7adbv */ /* Drop if no profiles matched */

Chain cali-tw-cali02bcd13d7d7 (1 reference)
 pkts bytes target prot opt in out source destination         
  584 64240 ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:kMMwzcbuv4QsOLZs */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:M7hgmAK2oQ0Zhs1J */ ctstate INVALID
  303,18180 MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:2MNmYedXuBEpbiYe */ MARK and 0xfffeffff.
  303,18180 cali-pri-kns.dev all -- * * 0.0.0.0/0 0.0.0/0 /* cali:PLEx7wMntF19VNmh */
  303 18180 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:pum18TA75RGVBX6H */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pri-ksa.dev.default all -- * * 0.0.0.0/0 0.0.0/0 /* cali:SMqy0kc9gDMHzVMg */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:qJwVPQb610zQoDpl */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:N9F3dPUehd8CniMv */ /* Drop if no profiles matched */

Chain cali-tw-cali0e254ef053c (1 reference)
 pkts bytes target prot opt in out source destination         
19056 8136K ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:INW55mws5a3ktnRC */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:6zCJSK5njJNPup9Y */ ctstate INVALID
    0 0 MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:6pIEjy3gqKNbEocL */ MARK and 0xfffeffffff
    0 0 cali-pri-kns.kube-system all -- * * 0.0.0.0/0 0.0.0/0 /* cali:e3vy7zByLlvKdlQw */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:qV87q4WlJZSnlh3Z */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pri-_lk3uafp1xALKGJtCJN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:IdqXOFRR9C5pMtvA */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:ohy2k2tmZxNwJUw1 */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:QyCd03UBnbbpgUuH */ /* Drop if no profiles matched */

Chain cali-tw-cali0e4c83da0c2 (1 reference)
 pkts bytes target prot opt in out source destination         
    0 0 ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:oGDZGxFgpEBjtAls */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:ZVhiuE6FO2wKr8jQ */ ctstate INVALID
    0 0 MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:ghOygebGi_bag3Dv */ MARK and 0xfffeffff.
    0 0 cali-pri-kns.dev all -- * * 0.0.0.0/0 0.0.0/0 /* cali:B1xWPyLCKm5jzzh- */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:G-7beqJWAjlLHDcW */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pri-ksa.dev.default all -- * * 0.0.0.0/0 0.0.0/0 /* cali:NIpacA_HFIGXEn_j */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:6oAlV1pLmoGsQkSy */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:lCNESbG1tmSFmGuB */ /* Drop if no profiles matched */

Chain cali-tw-cali1c39897f10f (1 reference)
 pkts bytes target prot opt in out source destination         
  577 64626 ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:JSbTs6bIVCZeSm3T */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:KMPWGFyBLgqoft3v */ ctstate INVALID
  264 15840 MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:FuKeTG_bXIqLJ2DS */ MARK and 0xfffeffffff
  264 15840 cali-pri-kns.dev all -- * * 0.0.0.0/0 0.0.0/0 / * cali:WET33tYDarDVkAwf */
  264 15840 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:JUmOzF0jPZwGP1GZ */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pri-ksa.dev.default all -- * * 0.0.0.0/0 0.0.0/0 /* cali:uszJvCywL8XaKV79 */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:2APRNY9bEeSTKIoQ */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:QIqa9o4h54jcNBqQ */ /* Drop if no profiles matched */

Chain cali-tw-cali22841037ef8 (1 reference)
 pkts bytes target prot opt in out source destination         
  600 67250 ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:ldy7EOaGbhH6L8uc */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:2ZE2HalSH0nfDoI4 */ ctstate INVALID
  269 16140 MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:EQALvTIp8Yg7oqzl */ MARK and 0xfffeffffff
  269 16140 cali-pri-kns.dev all -- * * 0.0.0.0/0 0.0.0/0 /* cali:DL6RDiBpZOl5CbLN */
  269 16140 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:BXSaaAGJdYwC1P5H */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pri-ksa.dev.default all -- * * 0.0.0.0/0 0.0.0/0 /* cali:6hi70q7nzhqlc2xs */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:gp5HrvaoutbRSKnx */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:zU2EnCYFAEeywkJj */ /* Drop if no profiles matched */

Chain cali-tw-cali363f791ae66 (1 reference)
 pkts bytes target prot opt in out source destination         
  561 62818 ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:ojkLA4yzC9y5mn75 */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:jMoGNStHfVJIFZM8 */ ctstate INVALID
  274 16440 MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:XFQRdC-m-3hDVMHY */ MARK and 0xfffeffffff
  274 16440 cali-pri-kns.dev all -- * * 0.0.0.0/0 0.0.0/0 /* cali:7vtleWdL2nI3YHu4 */
  274 16440 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:41qbsyI_viLwe4sy */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pri-ksa.dev.default all -- * * 0.0.0.0/0 0.0.0/0 /* cali:Vo6m5RIPfJJZbvDW */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:t_sry0_BmNHJ2SEV */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:dF5phH_MKPvL5p_k */ /* Drop if no profiles matched */

Chain cali-tw-cali487296ebfc4 (1 reference)
 pkts bytes target prot opt in out source destination         
 2762 4475K ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:cp9YYLRQz7fnVPZa */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:XtRnH-KLaqcc4Qpn */ ctstate INVALID
    0 0 MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:D0tXTK7f0QBSL3qs */ MARK and 0xfffeffffff
    0 0 cali-pri-kns.kube-system all -- * * 0.0.0.0/0 0.0.0/0 /* cali:sl8nRs0Zy8awWFCl */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:KwLz45WGan3dF40u */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pri-_CVSZITRyIpEmH8AB6H all -- * * 0.0.0.0/0 0.0.0/0 /* cali:dkiEzZaU3YtDoDRy */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:XEXr9WiUpfN8DmEE */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:SY8ii-0S3LEJ4M-S */ /* Drop if no profiles matched */

Chain cali-tw-cali4bbcf1021d6 (1 reference)
 pkts bytes target prot opt in out source destination         
    4 184 ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:GnDrZT_nMthXVc7Z */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:nGIO6VYMuhE3f2Bl */ ctstate INVALID
    1 60 MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:GDlYgij0L48vIyIC */ MARK and 0xfffeffff.
    1 60 cali-pri-kns.dev all -- * * 0.0.0.0/0 0.0.0/0 /* cali:-W77jXsUcZMNrsqh */
    1 60 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:_nPsJShkybZcIeZZZ */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pri-ksa.dev.default all -- * * 0.0.0.0/0 0.0.0/0 /* cali:Lfa-GxVRMWYLPa26 */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:dtGC8o9y9Ifb6zhh */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:yBkWt4MD_sbrNNVI */ /* Drop if no profiles matched */

Chain cali-tw-cali923f86f51da (1 references)
 pkts bytes target prot opt in out source destination         
  506 55660 ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:Q_UW4cx0aweMEE1_ */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:Vip4gWubCSGLNu9b */ ctstate INVALID
  264 15840 MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:Yoc5AWQ0znVl-Q9g */ MARK and 0xfffeffffff
  264 15840 cali-pri-kns.dev all -- * * 0.0.0.0/0 0.0.0/0 /* cali:voBva_wWW61yoUmOX */
  264 15840 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:qWXMATqSLaJHwdhh */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pri-ksa.dev.default all -- * * 0.0.0.0/0 0.0.0/0 /* cali:PavDCu6mIatppAld */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:uSO2ej-N6JRkLzC6 */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:E87ICzXmcasjPfsh */ /* Drop if no profiles matched */

Chain cali-tw-caliaf6bd9e3dd6 (1 reference)
 pkts bytes target prot opt in out source destination         
 1987 1355K ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:fpyoVBDWeGUPeSuD */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:UnBp_zs45ig_yanI */ ctstate INVALID
    0 0 MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:2e5-JyX7P2a_ng0J */ MARK and 0xfffeffffff
    0 0 cali-pri-kns.kube-system all -- * * 0.0.0.0/0 0.0.0/0 /* cali:I-HmNr-F4H7VYHTP */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:KJvtGyAjRXjD-1yg */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pri-_eSTHMIkNVbw_XFlWMl all -- * * 0.0.0.0/0 0.0.0/0 /* cali:aYBUbA7ArQEjP39j */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:eQIdkJIn_-wUX5Xa */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:hx_ePJfKQKki1qkQ */ /* Drop if no profiles matched */

Chain cali-tw-calib56d958096f (1 reference)
 pkts bytes target prot opt in out source destination         
 3651 1742K ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:TD4RUjCGAQI_a9qX */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:FospUN_owKpXeWjy */ ctstate INVALID
 1449 111K MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:8qdrvxYpXLhT4-DE */ MARK and 0xfffeffffff
 1449 111K cali-pri-kns.kube-system all -- * * 0.0.0.0/0 0.0.0/0 /* cali:SDFohewdjcq8gv9X */
 1449 111K RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:ZoDZDba1xJn3oHqU */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pri-_cHTcjx4Xi7rghi4C9T all -- * * 0.0.0.0/0 0.0.0/0 /* cali:lHdWQycRzxXBCHmy */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:h4GBVRMcvATs9TsQ */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:L0xUrVY9Vhdzlgqw */ /* Drop if no profiles matched */

Chain cali-tw-calibafc89b76e6 (1 reference)
 pkts bytes target prot opt in out source destination         
  407 781K ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:OVBtdaZk7hXigtmI */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:ojqlfc1ltalIiVAz */ ctstate INVALID
    0 0 MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:1IXIN0mET2eqoGgc */ MARK and 0xfffeffffff
    0 0 cali-pri-kns.kube-system all -- * * 0.0.0.0/0 0.0.0/0 /* cali:hEEkZ4UzfoO0yg8i */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:3oeHdgiPoMXpcvBk */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pri-_hMH3axmCSxXO8wa164 all -- * * 0.0.0.0/0 0.0.0/0 /* cali:Gi1IOWEWyQJcnypy */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:lI2CLKWKJPNIjcA2 */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:cpy57rSYDsdynWsy */ /* Drop if no profiles matched */

Chain cali-tw-calic0784236d5f (1 reference)
 pkts bytes target prot opt in out source destination         
   24 9424 ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:5P8AbQaM9iijluwH */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:DkyW8PnO7137TDCS */ ctstate INVALID
    2 120 MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:l3L_oG__YemkOhH4 */ MARK and 0xfffeffffff
    2 120 cali-pri-kns.dev all -- * * 0.0.0.0/0 0.0.0/0 /* cali:57ybLIAQ5u5cSDYL */
    2 120 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:M0aVrEkCxdAXi5RI */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pri-ksa.dev.default all -- * * 0.0.0.0/0 0.0.0/0 /* cali:ULZpaaC2FSTBCIlT */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:C-9fJN27M96N3VL8 */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:cGVYWqUNZViCdywJ */ /* Drop if no profiles matched */

Chain cali-tw-calicf8b0d0baf2 (1 reference)
 pkts bytes target prot opt in out source destination         
 3253 5490K ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:xZ26f3Ixq_L0in8c */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:_OJOuvK7DiRe0fYv */ ctstate INVALID
    0 0 MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:-5fEcIVVWG2ZWfyq */ MARK and 0xfffeffff.
    0 0 cali-pri-kns.kube-system all -- * * 0.0.0.0/0 0.0.0/0 /* cali:Zrc6DVGyCxmhgnay */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:lGi1ZRFs1a_aMUdI */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pri-_k7av1ffJ_LM_ftvh6m all -- * * 0.0.0.0/0 0.0.0/0 /* cali:4yttEsBIhfsy6Z4o */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:mIlIlrPdP_Xf5ilJ */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:bssrbsWtpHXzcxL2 */ /* Drop if no profiles matched */

Chain cali-tw-calid7820f5c789 (1 reference)
 pkts bytes target prot opt in out source destination         
 1227 1416K ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:v7E3GvxW64tCJPk -- */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:rZh0FF8p-uNQgL0s */ ctstate INVALID
    0 0 MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:Dllz-7SEpLwB5Hwz */ MARK and 0xfffeffff.
    0 0 cali-pri-kns.kube-system all -- * * 0.0.0.0/0 0.0.0/0 /* cali:Jb-1C-K1rKexYpI2 */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:kDBLAdbJdBjeRo19 */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pri-_hHPqAGO7Sc_GcoojC_ all -- * * 0.0.0.0/0 0.0.0/0 /* cali:prioov3kP1MwKhsy */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:PLZNiRmdfjUzlwEp */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:r1mw6VNOAT0uMek5 */ /* Drop if no profiles matched */

Chain cali-tw-calid9ba32f8b18 (1 reference)
 pkts bytes target prot opt in out source destination         
  456 50160 ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:UxcCoeDJPSgyIotN */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:0NcOH1lKBV1y6wju */ ctstate INVALID
  242,14520 MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:kv25sVl5I-X00svN */ MARK and 0xfffeffff.
  242,14520 cali-pri-kns.dev all -- * * 0.0.0.0/0 0.0.0/0 /* cali:s8-FRiaDBb9EjaOV */
  242 14520 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:S5C6r4r5lJbIo21w */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pri-ksa.dev.default all -- * * 0.0.0.0/0 0.0.0/0 /* cali:T6Dc-YR3z4gow-uH */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:8k8kMu2lkpmbizdR */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:v5xvz8qIZqVQ3DQe */ /* Drop if no profiles matched */

Chain cali-tw-calie2cee35dbce (1 references)
 pkts bytes target prot opt in out source destination         
    0 0 ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:UzLAG6BamDggjJ1N */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:R-tSbr_PLg5XXhWm */ ctstate INVALID
 6338 380K MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:OSrW88-mT2gChaMX */ MARK and 0xfffeffff.
 6338 380K cali-pri-kns.dev all -- * * 0.0.0.0/0 0.0.0/0 /* cali:6_hUlZOWSi7GcH1h */
 6338 380K RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:8yg3V7OYRNyV9ndX */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pri-ksa.dev.default all -- * * 0.0.0.0/0 0.0.0/0 /* cali:yfKSPYBIwHrzdCG4 */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:QWw7RdU8TCMuSrBZ */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:06RMSNOkKJALe__2 */ /* Drop if no profiles matched */

Chain cali-tw-calif320a18605b (1 reference)
 pkts bytes target prot opt in out source destination         
  474 824K ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:YgyD-CnqRaH6r_7s */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:I3lybd5EXq7nFVaB */ ctstate INVALID
    0 0 MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:I5e_DgK_cJrEfF6J */ MARK and 0xfffeffffff
    0 0 cali-pri-kns.kube-system all -- * * 0.0.0.0/0 0.0.0/0 /* cali:ArYxT_36TVgwxFNG */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:kJVoBxD5iJYvJ7No */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pri-_hMH3axmCSxXO8wa164 all -- * * 0.0.0.0/0 0.0.0/0 /* cali:4khFhfSay0qf58zq */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:18dEGH8L8ALAjndo */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:zFA05GRsNaek0mqJ */ /* Drop if no profiles matched */

Chain cali-tw-calif9eb280ec40 (1 reference)
 pkts bytes target prot opt in out source destination         
 1086 1010K ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:0ZsmajcyNXCzY9QR */ ctstate RELATED,ESTABLISHED
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:cPhD0yL6X_H-hZ8a */ ctstate INVALID
    0 0 MARK all -- * * 0.0.0.0/0 0.0.0/0 /* cali:NjpBj8NZ0UEgt91q */ MARK and 0xfffeffffff
    0 0 cali-pri-kns.kube-system all -- * * 0.0.0.0/0 0.0.0/0 /* cali:o4Misn9tsIoEo7sj */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:3Yg2OiaJdWPWbPr1 */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 cali-pri-_uWYVxQhEtQLr5GFz7e all -- * * 0.0.0.0/0 0.0.0/0 /* cali:c9w6tIH2ijxItrAl */
    0 0 RETURN all -- * * 0.0.0.0/0 0.0.0/0 /* cali:Lpfxp5gll-2AcGys */ /* Return if profile accepted */ mark match 0x10000/0x10000
    0 0 DROP all -- * * 0.0.0.0/0 0.0.0/0 /* cali:x2_QM3AYjz-tnCGx */ /* Drop if no profiles matched */

Chain cali-wl-to-host (1 references)
 pkts bytes target prot opt in out source destination         
 5314 864K cali-from-wl-dispatch all -- * * 0.0.0.0/0 0.0.0/0 /* cali:Ee9Sbo10IpVujdIY */
    2 120 ACCEPT all -- * * 0.0.0.0/0 0.0.0/0 /* cali:nSZbcOoG1xPONxb8 */ /* Configured DefaultEndpointToHostAction */
```
</p>
</details>


#### kube-dns

The scheme takes the following form
![scheme-kube-dns-kube-proxy.png](kubernetes/img/scheme-kube-dns-kube-proxy.png)

##### And within the cluster?

In fact, regardless of whether there are pods on one node or on different nodes - the traffic goes through the chain depicted on the previous slide.

Kubernetes does not have a mechanism for organizing networks (like Docker Swarm). It only provides an interface for this. Separate addons are used to create Overlay networks: Weave, Calico, Flannel, ... . Google Kontainer Engine (GKE) uses its own plugin **kubenet** (it is a part of kubelet).

It works only** together with the **GCP** platform and basically does what it does to configure Google networks to transmit Kubernetes traffic. So in the Docker configuration you will not see any Overlay networks now.

#### kubenet

The scheme takes the following form
![scheme-kubenet.png](kubernetes/img/scheme-kubenet.png)

##### And within the cluster?

To see the rules according to which traffic is sent to nodes, please, click here: https://console.cloud.google.com/networking/routes/.

#### nodePort

Service with type **NodePort** - is similar to service with type **ClusterIP**, only it adds listening to the node ports (all nodes) to access services ** outside**.  In this case ClusterIP is also assigned to this service to access it from within the cluster.

**kube-proxy** is listening to either the specified port (`nodePort: 32092`) or the port from the range **30000-32670**.

Next _IPTables_ decides which Pod will receive the traffic.

We have already published the UI service outside with the help of **NodePort**.

`ui-service.yml`
``Yaml
---
apiVersion: v1
kind: Service
metadata:
  name: ui
  The labels:
    app: reddit
    component: ui
spec:
  type: NodePort
  ports:
  - port: 9292
    nodePort: 32092
    protocol: TCP
    targetPort: 9292
  Selector:
    app: reddit
    component: ui
```

The scheme takes the following form
![scheme-nodeport.png](kubernetes/img/scheme-nodeport.png)


#### LoadBalancer

Type **NodePort** although it provides access to the service from the outside, it is not very convenient to open all ports from outside or search for IP addresses of our nodes (which are dynamic at all).

The **LoadBalancer** type allows us to use an external cloud load balancer as a single point of entry into our services, rather than relying on IPTables and not opening up the entire cluster outwards.

The schema takes the following form
![scheme-loadbalancer.png](kubernetes/img/scheme-loadbalancer.png)

Configure the Service UI accordingly
``Yaml
---
apiVersion: v1
kind: Service
metadata:
  name: ui
  The labels:
    app: reddit
    component: ui
spec:
  type: LoadBalancer
  ports:
    - port: 80 # The port to be opened on the balancer
      nodePort: 32092 # Also a port will be opened on the node, but we don't need it and it can even be removed.
      protocol: TCP
      targetPort: 9292 # POD port
  Selector:
    app: reddit
    component: ui
```

Configure the Service UI accordingly
``shell
kubectl apply -f ui-service.yml -n dev
```

Let's see what it is.
``shell
kubectl get service -n dev --selector component=ui
```
``log
NAME TYPE CLUSTER-IP EXTERNAL-IP PORT(S) AGE
ui LoadBalancer 10.4.7.57 34.67.99.206 80:32092/TCP 2m39s
```

Check in your browser: http://34.67.99.206:80.

All application components work.

A rule will be created for balancing: _Network services_ -> _Load balancing_.
![screenshot-loadbalancer.png](kubernetes/img/screenshot-loadbalancer.png)

Service Type LoadBalancing has a number of drawbacks:
- can not be controlled with http URI (L7-balancing)
- used ** only** cloud balancers (AWS, GCP)
- no flexible traffic rules

#### Ingress

Another Kubernetes object - **Ingress** - can be used to manage incoming traffic from outside more conveniently and to solve LoadBalancer shortcomings.

**Ingress** is a set of rules within a Kubernetes cluster designed to allow inbound connections to reach Services.

The Ingress are just rules in themselves. You need **Ingress Controller** to apply them.

#### Ingress Conroller ###

**Ingress Controller** is required for the Ingress operation. Unlike other k8s controllers - it does not start together with the cluster.

**Ingress Controller** is rather a plugin (and therefore a separate POD), which consists of 2 functional parts: 
- An application that tracks new Ingress objects through the k8s API and updates the balancer configuration.
- Balancer (Nginx, haproxy, traefik,...) who manages network traffic.

##### Ingress

The main tasks solved with the help of Ingress:
- Organizing a single point of entry into applications from the outside
- Ensuring traffic balancing
- SSL term 
- Virtual name-based hosting, etc.

As far as we have a web application, it would be logical for us to use an L7 Balancer instead of a Service LoadBalancer.

Google in GKE already provides the possibility to use their own balancer solutions as Ingress controllers.

Go to the cluster settings at [gcloud web console] (https://console.cloud.google.com/kubernetes).

Make sure the built-in Ingress is on. If not, turn it on.

Create Ingress for UI service
`yi-ingress.yml`
``Yaml
---
apiVersion: extensions/v1beta1
kind: Ingress
metadata:
  name: ui
spec:
  backend:
    serviceName: ui
    servicePort: 80
```
This **Singe Service Ingress** means that the entire ingress controller will simply balance the load on the nodes for one service (very similar to Service LoadBalancer).

We'll apply config.
``shell
kubectl apply -f ui-ingress.yml -n dev
```
``log
ingress.extensions/ui created
```

Let's go to [GCP console] (https://console.cloud.google.com/net-services/loadbalancing/loadBalancers/list) and see some rules.
![screenshot-loadbalancers.png](kubernetes/img/screenshot-loadbalancers.png)

We are interested in the 1st
![screenshot-loadbalancer-ingress.png](kubernetes/img/screenshot-loadbalancer-ingress.png)

We see the NodePort of the published service. I.e. to work with Ingress in GCP we need a minimum Service with type **NodePort** (we already have it).

Let's look at the cluster itself:
``shell
kubectl get ingress -n dev
```
``log
NAME HOSTS ADDRESS PORTS AGE
ui * 34.95.116.107 80 5m52s
```

The scheme takes the following form
![scheme-ingress.png](kubernetes/img/scheme-ingress.png)

There are several disadvantages to the current scheme:
- we have 2 balancers for 1 service.
- We don't know how to manage HTTP-level traffic.

One balancer can be safely removed. Update service for UI
`kubernetes/reddit/ui-service.yml`
``Yaml
---
apiVersion: v1
kind: Service
metadata:
  name: ui
  The labels:
    app: reddit
    component: ui
spec:
  type: NodePort
  ports:
    - port: 9292
      protocol: TCP
      targetPort: 9292
  Selector:
    app: reddit
    component: ui
```

We apply .
``shell
kubectl apply -f ui-service.yml -n dev
```
``log
service/ui configured
```

Make Ingress Controller work like a classic web.
`kubernetes/reddit/ui-ingress.yml`
``Yaml
---
apiVersion: extensions/v1beta1
kind: Ingress
metadata:
  name: ui
spec:
  rules:
    - http:
        paths:
          - path: /*
            backend:
              serviceName: ui
              servicePort: 9292
```
``shell
kubectl apply -f ui-ingress.yml -n dev
```
``log
ingress.extensions/ui configured
```
``shell
kubectl get ingress -n dev
```
``log
NAME HOSTS ADDRESS PORTS AGE
ui * 34.95.116.107 80 14m
```

When trying to open http://34.95.116.107:80, error 502
``log
Error: Server Error
The server encountered a temporary error and could not complete your request.
Please try in 30 seconds.
```

Wait... Checked it out in 10 minutes. It's working.

#### Secret

Now let us protect our service with TLS. First let's remember Ingress IP
``shell
kubectl get ingress -n dev 
```
``log
NAME HOSTS ADDRESS PORTS AGE
ui * 34.95.116.107 80 31m
```

Then we prepare the certificate using IP as CN
``shell
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout tls.key -out tls.crt -subj "/CN=34.95.116.107"
```
``log
Can't load /home/myusername/.rnd into RNG
139682105135552:error:2406F079:random number generator:RAND_load_file:Cannot open file:../crypto/rand/randfile.c:88:Filename=/home/myusername/.rnd
Generating an RSA private key
.......................................+++++
........+++++
writing new private key to 'tls.key'.
-----
```
Errors some ^_^ but the key is created))).

Googling the error resulted in [the following solution] (https://github.com/openssl/openssl/issues/7754#issuecomment-541307674), namely
> I had the same issue as you on Ubuntu 18.04.x. Removing (or commenting out) `RANDFILE = $ENV::HOME/.rnd` from `/etc/ssl/openssl.cnf` worked for me.

Let's try to recreate the certificate.
``shell
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout tls.key -out tls.crt -subj "/CN=34.95.116.107"
```
``log
Generating an RSA private key
.........................................................................+++++
.................................................................................................................................. ..............................................................................................................................+++++
writing new private key to 'tls.key'.
-----
```
No mistakes this time. Continued .

And upload the certificate to the kubernetes cluster.
``shell
kubectl create secret tls ui-ingress --key tls.key --cert tls.crt -n dev
```
``log
secret/ui-ingress created
```

You can check it with a team
``shell
kubectl describe secret ui-ingress -n dev
```
``log
Name: ui-ingress
Namespace: dev
Labels: <none>
Annotations: <none>

Type: kubernetes.io/tls

Data
====
tls.crt: 1123 bytes
tls.key: 1704 bytes
```

#### TLS Termination

Now configure Ingress to receive only HTTPS traffic
`kubernetes/reddit/ui-ingress.yml`
``Yaml
---
apiVersion: extensions/v1beta1
kind: Ingress
metadata:
  name: ui
  annotations:
    kubernetes.io/ingress.allow-http: "false"
spec:
  tls:
    - secretName: ui-ingress
  backend:
    serviceName: ui
    servicePort: 9292
```
``shell
kubectl apply -f ui-ingress.yml -n dev
```
``log
ingress.extensions/ui configured
```

Go to [web console] (https://console.cloud.google.com/net-services/loadbalancing/loadBalancers/list) and see only one HTTPS protocol (not yet) in the description of our balancer.

Sometimes the HTTP protocol may not be removed from an existing Ingress rule, then it must be manually removed and recreated.
``shell
kubectl delete ingress ui -n dev
```
``log
ingress.extensions "ui" deleted
```
``shell
kubectl apply -f ui-ingress.yml -n dev
```
``log
ingress.extensions/ui created
```
The web console now contains only https

``shell
kubectl get ingress -n dev 
```
``log
NAME HOSTS ADDRESS PORTS AGE
ui * 35.244.235.133 80, 443 4m3s
```

Go to our application page by https, confirm the security exception (we have a self-signed certificate) and see that everything works.

https://35.244.235.133
![screenshot-reddit-https.png](kubernetes/img/screenshot-reddit-https.png)

The Ingress rules can be applied for a long time if you can't get in on your first try - wait and try again.

#### Task from \* Secret as a Kubernetes manifesto

Describe the Secret object being created as a Kubernetes manifest.

##### Analysis

https://kubernetes.io/docs/concepts/configuration/secret/

Types of secrets https://github.com/kubernetes/kubernetes/blob/release-1.15/pkg/apis/core/types.go#L4458

Type `SecretTypeTLS SecretType = "kubernetes.io/tls"` https://github.com/kubernetes/kubernetes/blob/release-1.15/pkg/apis/core/types.go#L4530.
``go
	// Required fields:
	// - Secret.Data["tls.key"] - TLS private key.
	// Secret.Data["tls.crt"] - TLS certificate.
	// TODO: Consider supporting different formats, specifying CA/destinationCA.
	SecretTypeTLS SecretType = "kubernetes.io/tls".

	// TLSCertKey is the key for tls in a TLS secret.
	TLSCertKey = "tls.crt".
	// TLSPrivateKeyKey is the key for the private key field in a TLS secret.
	TLSPrivateKeyKey = "tls.key".
```

An example of a secret that we should apply
``Yaml
apiVersion: v1
kind: Secret
metadata:
  name: ui-ingress
type: kubernetes.io/tls
data:
  tls.crt: base64-encoded-content-of_tls.crt
  tls.key: base64-encoded-content-of_tls.key
```

More in theme: on the basis of already created files the secret can be created with the generator https://kubernetes.io/docs/concepts/configuration/secret/#creating-a-secret-from-generator.

##### Implementation

Files `tls.crt` and `tld.key` have been moved to `kubernetes/reddit/secrets`.

**IMPORTANT!** the files `kubernetes/reddit/secrets/tls.crt` and `kubernetes/reddit/secrets/tls.key` have not been added to the repository at this stage because the cluster is still functioning.

The `kubernetes/reddit/secrets/kustomization.yaml` file was created with the following content
``Yaml
---
secretGenerator:
  - name: ui-ingress-yaml
    type: kubernetes.io/tls
    Files:
      - tls.crt
      - tls.key
generatorOptions:
  disableNameSuffixHash: true
```

The existing secret of the ``i-ingress`` has been removed.
``shell
kubectl delete secrets ui-ingress -n dev
```
``log
secret "ui-ingress" deleted
```

In `kubernetes/reddit/ui-ingress.yml` the secret name has been changed to `secretName: ui-ingress-yaml`.

> **Note**: flag `-k` allows you to work with `<kustomization_directory>`.
> 
> For example, to see what happens after you apply
> ``shell
> kubectl kustomize <kustomization_directory>
> ```
> 
> And to apply
> ``shell
> kubectl apply -k <kustomization_directory>
> ```

The secret from `./kubernetes/reddit/secrets/` was created.
``shell
kubectl apply -k ./secrets -n dev       
```
``log
secret/ui-ingress-yaml created
```

We apply .
``shell
kubectl apply -f ./n dev            
```
``log
deployment.apps/comment unchanged
service/comment-db
service/comment unchanged
namespace/dev unchanged
deployment.apps/mongo unchanged
service/mongodb unchanged
deployment.apps/post
service/post-db
service/post
deployment.apps/ui unchanged
ingress.extensions/ui configured
service/ui unchanged
```

Checking: 
``shell
kubectl get secrets -n dev
```
``log
NAME TYPE DATA AGE
default-token-s7bj4 kubernetes.io/service-account-token 3 18h
ui-ingress-yaml kubernetes.io/tls 2 100s
```
``shell
kubectl describe secrets ui-ingress-yaml -n dev
```
``log
Name: ui-ingress-yaml
Namespace: dev
Labels: <none>
Annotations:  
Type: kubernetes.io/tls

Data
====
tls.crt: 1123 bytes
tls.key: 1704 bytes
```
The website https://35.244.235.133/ is opening.


#### Network Policy

https://cloud.google.com/kubernetes-engine/docs/how-to/network-policy

In past projects, we agreed that we would like to spread the database services and the frontend service over different networks, making them unavailable to each other. And we adopted the following scheme of services.

In Kubernetes we can't do that with the help of separate networks, because all PODs can reach each other by default.

We will use **NetworkPolicy** - a tool for declarative description of traffic flows. It should be noted that not all network plugins support network policies.
In particular, GKE has this feature so far in the Beta test and will separately enable **Calico** network plugin (instead of **Kubenet**).

Let's test it.

Our task is to limit traffic coming to _mongodb_ from everywhere except _post_ and _comment_ services.

Find the cluster name.
``shell
gcloud beta container clusters list
```
``log
NAME LOCATION MASTER_VERSION MASTER_IP MACHINE_TYPE NODE_VERSION NUM_NODES STATUS
reddit-public us-central1-a 1.15.4-gke.22 35.226.129.186 n1-standard-1 1.15.4-gke.22 2 RUNNING
```

Enable network-policy for GKE.
``shell
gcloud beta container clusters update reddit-public --zone=us-central1-a --update-addons=NetworkPolicy=ENABLED
```
``log
Updating reddit-public... done.                                                                                                                                      
Updated [https://container.googleapis.com/v1beta1/projects/<project_id>/zones/us-central1-a/clusters/reddit-public].
To inspect the contents of your cluster, go to: https://console.cloud.google.com/kubernetes/workload_/gcloud/us-central1-a/reddit-public?project=<project_id>.
```
``shell
gcloud beta container clusters update reddit-public --zone=us-central1-a --enable-network-policy
```
``log
Enabling/Disabling Network Policy a rolling update of all 
cluster nodes, similar to performing a cluster upgrade.  This . 
This is long-running and will block other operations on the 
(including delete) until it has run to completion.

Do you want to continue (Y/n)?  y

Updating reddit-public... done.                                                                                                                                      
Updated [https://container.googleapis.com/v1beta1/projects/<project_id>/zones/us-central1-a/clusters/reddit-public].
To inspect the contents of your cluster, go to: https://console.cloud.google.com/kubernetes/workload_/gcloud/us-central1-a/reddit-public?project=<project_id>.
```

Wait until the cluster is updated you may be asked to add beta functionality to gcloud - press yes.

Create `kubernetes/reddit/mongo-network-policy.yml` manifesto.
``Yaml
---
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: deny-db-traffic
  The labels:
    app: reddit
spec:
  podSelector: # Choose objects
    matchLabels:
      app: reddit
      mongo
  policyTypes: # Block of forbidden directions
    - Ingress
  ingress: # The block of permissive rules
    - from:
        - podSelector:
            matchLabels:
              app: reddit
              component: comment
```

Select policy objects (pods with mongodb)
``Yaml
podSelector:
  matchLabels:
    app: reddit
    mongo
```

All incoming connections are forbidden. Outgoing connections allowed.
``Yaml
policyTypes:
  - Ingress
```

Allow all incoming connections from PODs with label comment.
```Yaml
ingress:
  - from:
      - podSelector:
          matchLabels:
            app: reddit
            comment.
```

Let's apply the policy
``shell
kubectl apply -f mongo-network-policy.yml -n dev
```
``log
networkpolicy.networking.k8s.io/deny-db-traffic created
```

See .
``shell
kubectl get networkpolicies -n dev
```
``log
NAME POD-SELECTOR AGE
deny-db-traffic app=reddit,component=mongo 2m43s
```
``shell
kubectl describe networkpolicies deny-db-traffic -n dev
```
``log
Name: deny-db-traffic
Namespace: dev
Created on: 2020-01-04 19:08:37 +0300 MSK
Labels: app=reddit
Annotations: kubectl.kubernetes.io/last-applied-configuration:
                {"apiVersion": "networking.k8s.io/v1", "kind": "NetworkPolicy", "metadata":{"annotations":}, "labels":{"app": "reddit"}, "name": "deny-db-traffic...
Spec:
  PodSelector: app=reddit,component=mongo
  Allowing ingress traffic:
    To Port: <any> (traffic allowed to all ports)
    From:
      PodSelector: app=reddit,component=comment
  Not affecting egress traffic
  Policy Types: Ingress
```

Post service can't reach the base, they said. And I've got everything working. Oh... I mean, it works when you open the site. Assumed reason: the substitutions weren't re-created, as they said when we turned on network-policy.

I re-created everything, including the certificate... The site really ** stopped working** ^_^ TODO: figured out how to re-create just what you need and what to re-create >_<. Reread the docks: i guess i just couldn't wait for https://cloud.google.com/kubernetes-engine/docs/how-to/network-policy#enabling_network_policy_enforcement.
> Then, run the gcloud container clusters update command with the --enable-network-policy flag. This command your cluster's node pools to be recreated with network policy enabled

#### Assignment

Update `mongo-network-policy.yml` so that the post service reaches the database.
``Yaml''.
---
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: deny-db-traffic
  The labels:
    app: reddit
spec:
  podSelector:
    matchLabels:
      app: reddit
      mongo
  policyTypes:
    - Ingress
  ingress:
    - from:
        - podSelector:
            matchLabels:
              app: reddit
              component: comment
    - from:
        - podSelector:
            matchLabels:
              app: reddit
              post
```

We apply .
``shell
kubectl apply -f mongo-network-policy.yml -n dev
```
``log
networkpolicy.networking.k8s.io/deny-db-traffic configured
```

The site is back online at https://34.95.116.107/.


### Base Storage

Let's look at data storage issues. The main _Stateful_ service in our application is the MongoDB database.

At the moment it is launched as _Deployment_ and stores data in the herd Docker Volume. This has several problems:
- if you delete a POD, Volume is also deleted.
- Nod's mongo loss threatens data loss
- running the database on a different node starts a new data instance

`mongo-deployment.yml`
``Yaml
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: mongo
  The labels:
    app: reddit
    mongo
    post-db: "true"
    comment-db: "true"
spec:
  replicas: 1
  selector:
    matchLabels:
      app: reddit
      mongo
  Oh..:
    metadata:
      name: mongo
      The labels:
        app: reddit
        mongo
        post-db: "true"
        comment-db: "true"
    spec:
      containers:
      - image: mongo:3.2
        name: mongo
        volumeMounts: # Connect Volume
        - name: mongo-persistent-storage
          mountPath: /data/db
      Oh..:
      - name: mongo-persistent-storage # Declare Volume
        emptyDir: {}
```

 #### Volume

Now the Volume emptyDir type is used. When creating a feed with this type, it simply creates an empty docker volume.

When the POD stops, the content of emtpyDir will be removed forever. Although, in general, the POD's drop does not cause the Volume's deletion.

Task:
1) create a post in the application
   - Created by .
2) remove deployment for mongo
   ``shell
   kubectl delete -f mongo-deployment.yml -n dev
   ```
   ``log
   deployment.apps "mongo" deleted
   ```
3) Create it all over again
   ``shell
   kubectl apply -f mongo-deployment.yml -n dev 
   ```
   ``log
   deployment.apps/mongo created
   ```
4) The post is missing

Instead of storing data locally on the node, it makes sense to connect the remote storage. In our case we can use Volume _gcePersistentDisk_ which will store data in GCE storage.

Let's create a disk in Google Cloud
``shell
gcloud compute disks create --size=25GB --zone=us-central1-a reddit-mongo-disk
```
``log
WARNING: You have selected a disk size of under [200GB]. This may result in poor I/O performance. For more information, see: https://developers.google.com/compute/docs/disks#performance.
Created [https://www.googleapis.com/compute/v1/projects/docker-257914/zones/us-central1-a/disks/reddit-mongo-disk].
NAME ZONE SIZE_GB TYPE STATUS
reddit-mongo-disk us-central1-a 25 pd-standard READY

New disks are unformatted. You must format and mount a disk before it
can be used. You can find instructions on how to do this at:

https://cloud.google.com/compute/docs/disks/add-persistent-disk#formatting.
```

Let's add a new Volume POD to the base.

``Yaml
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: mongo
  The labels:
    app: reddit
    mongo
    post-db: "true"
    comment-db: "true"
spec:
  replicas: 1
  selector:
    matchLabels:
      app: reddit
      mongo
  Oh..:
    metadata:
      name: mongo
      The labels:
        app: reddit
        mongo
        post-db: "true"
        comment-db: "true"
    spec:
      containers:
      - image: mongo:3.2
        name: mongo
        volumeMounts:
        - name: mongo-gce-pd-storage
          mountPath: /data/db
      Oh..:
      - name: mongo-persistent-storage
        emptyDir: {}
        Oh..:
      - name: mongo-gce-pd-storage
        gcePersistentDisk:
          pdName: reddit-mongo-disk
          fsType: ext4
```

Mount the dedicated drive to POD mongo.
![](kubernetes/img/scheme-volume.png)

``shell
kubectl apply -f mongo-deployment.yml -n dev
```
``log
deployment.apps/mongo configured
```

Wait, recreate the Pod (takes up to 10 minutes). Let's go to the application and add a post - done.

Delete
``shell
kubectl delete deploy mongo -n dev
```
``log
deployment.extensions "mongo" deleted
```

We'll create a depression mongo again. 
" hell
kubectl apply -f mongo-deployment.yml -n dev
```
``log
deployment.apps/mongo created
```

Our post is still in place. [Here](https://console.cloud.google.com/compute/disks?supportedpurview=project&project=<project_id>&angularJsUrl=%2Fprojectselector%2Fcompute%2Fdisks%3Fsupportedpurview%3Dproject%26project%3D%26folder%3D%26organizationId%3D&authuser=1) you can look at the disk you created and see which machine uses it.

#### PersistentVolume

The Volume mechanism used can be made more convenient. We can use not an entire dedicated disk for each feed, but an entire storage resource shared by the entire cluster.

Then when running Stateful tasks in the cluster, we can request the storage as the same resource as the CPU or RAM.

For this purpose, we will use the mechanism **PersistentVolume**.

Let's create the description of PersistentVolume.
`mongo-volume.yml`
``Yaml
---
apiVersion: v1
kind: PersistentVolume
metadata:
  name: reddit-mongo-disk
spec:
  capacity:
    storage: 25Gi
  accessModes:
    - ReadWriteOnce
  persistentVolumeReclaimPolicy: Retain
  gcePersistentDisk:
    fsType: "ext4" 
    pdName: "reddit-mongo-disk"
```

Let's add PersistentVolume to the cluster.
``shell
kubectl apply -f mongo-volume.yml -n dev
```
``log
persistentvolume/reddit-mongo-disk created
```
We created PersistentVolume as a drive in GCP.
![](kubernetes/img/scheme-persistentvolume.png)


#### PersistentVolumeClaim

We have created a disk storage resource that has been extended to the entire cluster as PersistentVolume.

To allocate a part of this resource to the application - we need to create a request for the output - **PersistentVolumeClaim**. _Claim_ is the request, not the storage itself.

Using the query you can allocate space both from a specific **PersistentVolume** (then parameters _accessModes_ and _StorageClass_ must match, and there must be enough space), and simply create a separate **PersistentVolume** for a specific query.

Let's create the description **PersistentVolumeClaim** (PVC).
`mongo-claim.yml`
``Yaml
---
kind: PersistentVolumeClaim
apiVersion: v1
metadata:
  name: mongo-pvc
spec:
  accessModes:
    - ReadWriteOnce
  Resources:
    requests:
      storage: 15Gi
```

Add **PersistentVolumeClaim** to the cluster.
``shell
kubectl apply -f mongo-claim.yml -n dev
```
``log
persistentvolumeclaim/mongo-pvc created
```


#### PersistentVolume

We have allocated a space in PV on request for our base. You can only use one PV at a time by **one** Claim.
![](kubernetes/img/scheme-persistentvolume-one.png)


#### PersistentVolumeClaim

If Claim can't find the PV inside the cluster by the specified parameters, or if it is occupied by another Claim, it will create the necessary PV using the standard StorageClass.

``shell
kubectl describe storageclass standard -n dev
```
``log
Name: standard
IsDefaultClass: Yes
Annotations: storageclass.kubernetes.io/is-default-class=true
Provisioner: kubernetes.io/gce-pd
Parameters: type=pd-standard
AllowVolumeExpansion: True
MountOptions: <none>
ReclaimPolicy: Delete
VolumeBindingMode: Immediate
Events: <none>
```

In our case it's a regular slow Google Cloud Persistent Drive.
![](kubernetes/img/scheme-persistentvolumeclaim.png)


#### Let's connect PVC to our Pods.

`mongo-deployment.yml`
``Yaml
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: mongo
  The labels:
    app: reddit
    mongo
    post-db: "true"
    comment-db: "true"
spec:
  replicas: 1
  selector:
    matchLabels:
      app: reddit
      mongo
  Oh..:
    metadata:
      name: mongo
      The labels:
        app: reddit
        mongo
        post-db: "true"
        comment-db: "true"
    spec:
      containers:
        - image: mongo:3.2
          name: mongo
          volumeMounts:
            - name: mongo-gce-pd-storage
              mountPath: /data/db
      Oh..:
        - name: mongo-gce-pd-storage
          The VolumeClaim:
            claimName: mongo-pvc
```

Update the description of our Deployment
``shell
kubectl apply -f mongo-deployment.yml -n dev
```
``log
deployment.apps/mongo configured
```

Mount the PVC dedicated storage to POD mongo
![](kubernetes/img/scheme-persistentvolume-mount.png)

#### Dynamic Volume Selection

By creating PersistentVolume we separated the object of "storage" from our Services and Pods. Now we can reuse it if necessary.

But it is much more interesting for us to create storages when necessary and in automatic mode. **StorageClass**'s will help us to do it. They describe where (which provider) and which repositories are created.

In our case we will create StorageClass **Fast** in such a way that SSDs are mounted for our storage to work.

#### StorageClass

Let's create a description of StorageClass.
`storage-fast.yml`
``Yaml
---
kind: StorageClass
apiVersion: storage.k8s.io/v1beta1
metadata:
  name: fast # StorageClass name
Kubernetes.io/gce-pd # Storage Provider
I'm sorry:
  type: pd-ssd # Type of storage provided
```

Let's add StorageClass to the cluster.
``shell
kubectl apply -f storage-fast.yml -n dev
```
``log
storageclass.storage.k8s.io/fast created
```
``shell
kubectl get storageclasses
```
``log
NAME PROVISIONER AGE
fast kubernetes.io/gce-pd 57s
standard (default) kubernetes.io/gce-pd 26h
```
When you specify a nymspaces, the result is the same. This confirms that StoregeClass will not nymspaces.

``shell.
kubectl describe storageclasses fast
```
``log
Name: fast
IsDefaultClass: No
Annotations: kubectl.kubernetes.io/last-applied-configuration={"apiVersion": "storage.k8s. io/v1beta1", "kind": "StorageClass", "metadata":{"annotations":{}, "name": "fast"}, "parameters":{"type": "pd-ssd"}, "provisioner": "kubernetes.io/gce-pd"}.

Provisioner: kubernetes.io/gce-pd
Parameters: type=pd-ssd
AllowVolumeExpansion: <unset>
MountOptions: <none>
ReclaimPolicy: Delete
VolumeBindingMode: Immediate
Events: <none>
```

#### PVC + StorageClass

Let's create a description of PersistentVolumeClaim. 
`mongo-claim-dynamic.yml`
``Yaml
---
kind: PersistentVolumeClaim
apiVersion: v1
metadata:
  name: mongo-pvc-dynamic
spec:
  accessModes:
    - ReadWriteOnce
  storageClassName: fast # Instead of referring to the created disk, now we refer to StorageClass
  Resources:
    requests:
      storage: 10Gi
```

Let's add StorageClass to the cluster.
``shell
kubectl apply -f mongo-claim-dynamic.yml -n dev
```
``log
persistentvolumeclaim/mongo-pvc-dynamic created
```
``shell
kubectl get persistentvolumeclaims -n dev
```
Neimscape matters.
``log
NAME STATUS VOLUME CAPACITY ACCESS MODES STORAGECLASS AGE
mongo-pvc Bound pvc-f6e26f0c-37bb-4885-9f12-eaa4b85e14a1 15Gi RWO standard 37m
mongo-pvc-dynamic Bound pvc-97eaaa5c-fbce-40ee-ae6f-d6cf0a38ded4 10Gi RWO fast 27s
```

``shell
kubectl describe persistentvolumeclaims mongo-pvc-dynamic -n dev
```
``log
Name: mongo-pvc-dynamic
Namespace: dev
StorageClass: fast
Status: Bound
Volume: pvc-97eaaa5c-fbce-40ee-ae6f-d6cf0a38ded4
Labels: <none>
Annotations: kubectl.kubernetes.io/last-applied-configuration:
                 {"apiVersion": "v1", "kind": "PersistentVolumeClaim", "metadata":{"annotations":}, "name": "mongo-pvc-dynamic", "namespace": "dev"}, "spec":{"acce...
               pv.kubernetes.io/bind-completed: yes
               pv.kubernetes.io/bound-by-controller: yes
               volume.beta.kubernetes.io/storage-provisioner: kubernetes.io/gce-pd
Finalizers: [kubernetes.io/pvc-protection]
Capacity: 10Gi
Access Modes: RWO
VolumeMode: Filesystem
Mounted By: <none>
Events:
  Type Reason Age From Message
  ---- ------ ---- ---- -------
  Normal ProvisioningSucceeded 86s persistentvolume-controller Successfully provisioned volume pvc-97eaaa5c-fbce-40ee-ae6f-d6cf0a38ded4 using kubernetes.io/gce-pd
```

#### Connecting a dynamic PVC

Let's connect the PVC to our Pods.
`mongo-deployment.yml`
``Yaml
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: mongo
  The labels:
    app: reddit
    mongo
    post-db: "true"
    comment-db: "true"
spec:
  replicas: 1
  selector:
    matchLabels:
      app: reddit
      mongo
  Oh..:
    metadata:
      name: mongo
      The labels:
        app: reddit
        mongo
        post-db: "true"
        comment-db: "true"
    spec:
      containers:
        - image: mongo:3.2
          name: mongo
          volumeMounts:
            - name: mongo-gce-pd-storage
              mountPath: /data/db
      Oh..:
        - name: mongo-gce-pd-storage
          The VolumeClaim:
            claimName: mongo-pvc-dynamic
```

Update the description of our Deployment
``shell
kubectl apply -f mongo-deployment.yml -n dev
```
``log
deployment.apps/mongo configured
```
``shell
kubectl describe deployment mongo -n dev
```
``log
Name: mongo
Namespace: dev
CreationTimestamp: Sat, 04 Jan 2020 23:33:44 +0300
Labels: app=reddit
                        comment-db=true
                        component=mongo
                        post-db=true
Annotations: deployment.kubernetes.io/revision: 3
                        kubectl.kubernetes.io/last-applied-configuration:
                          {"apiVersion": "apps/v1", "kind": "Deployment", "metadata":{"annotations":}, "labels":{"app": "reddit", "comment-db": "true", "component": "mongo",...
Selector: app=reddit,component=mongo...
Replicas: 1 desired | 1 updated | 1 total | 1 available | 0 unavailable
StrategyType: RollingUpdate
MinReadySeconds: 0
RollingUpdateStrategy: 25% max unavailable, 25% max surge
Pod Template:
  Labels: app=reddit
           comment-db=true
           component=mongo
           post-db=true
  Containers:
   mongo:
    Image: mongo:3.2
    Port: <none>
    Host Port: <none>
    Environment: <none>
    Mounts:
      /data/db from mongo-gce-pd-storage (rw)
  Volumes:
   mongo-gce-pd-storage:
    Type: PersistentVolumeClaim (a reference to a PersistentVolumeClaim in the same namespace)
    ClaimName: mongo-pvc-dynamic
    ReadOnly: false
Conditions:
  Type Status Reason
  ---- ------ ------
  Available True MinimumReplicasAvailable
  Progressing True NewReplicaSetAvailable
OldReplicaSets: <none>
NewReplicaSet: mongo-7fd95647d9 (1/1 replicas created)
Events:
  Type Reason Age From Message
  ---- ------ ---- ---- -------
  Normal ScalingReplicaSet 57m deployment-controller Scaled up replica set mongo-7644fd57 to 1
  Normal ScalingReplicaSet 42m deployment-controller Scaled up replica set mongo-675d5df69 to 1
  Normal ScalingReplicaSet 42m deployment-controller Scaled down replica set mongo-7644fd57 to 0
  Normal ScalingReplicaSet 3m9s deployment-controller Scaled up replica set mongo-7fd95647d9 to 1
  Normal ScalingReplicaSet 2m49s deployment-controller Scaled down replica set mongo-675d5df69 to 0
```

Let's see how we ended up with PersistentVolumes.
``shell
kubectl get persistentvolume -n dev
```
``log
NAME CAPACITY ACCESS MODES RECLAIM POLICY STATUS CLAIM STORAGECLASS REASON AGE
pvc-97eaaa5c-fbce-40ee-ae6f-d6cf0a38ded4 10Gi RWO Delete Bound dev/mongo-pvc-dynamic fast 15m
pvc-f6e26f0c-37bb-4885-9f12-eaa4b85e14a1 15Gi RWO Delete Bound dev/mongo-pvc standard 52m
reddit-mongo-disk 25Gi RWO Retain Available 55m
```

The disks created by Kubernetes can be viewed at [web console] (https://console.cloud.google.com/projectselector/compute/disks?supportedpurview=project&project=&folder=&organizationId=).
![](kubernetes/img/scheme-dynamic-pvc.png)

The cluster is remote.
``shell
cd ./kubernetes/terraform
make destroy
```

But it may be necessary to remove the disk as well. You need to check and delete it through the console.

Add the created certificates `kubernetes/reddit/secrets/tls.*`.

### How to start

#### Hands

``shell
# Let's create a cluster
cd ./kubernetes/terraform
make apply
cd -
# Access and customize the kubectl context
gcloud container clusters get-credentials reddit-public --zone us-central1-a --project docker-257914
# We create resources
cd ./kubernetes/reddit
kubectl apply -f dev-namespace.yml
kubectl apply -f ./
# Generating a certificate for https
cd ./secrets
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout tls.key -out tls.crt -subj "/CN=reddit"
# Downloading the certificate
kubectl apply -k ./n dev
# We get ip ingress
INGRESS_IP=$(kubectl get ingresses ui -n dev -o json | jq '.status.loadBalancer.ingress[0].ip' | xargs)
echo https://${INGRESS_IP}
```


#### ./kubernetes/Makefile

#### Variables

| variable | default | description |
| ------------ | ------------- | -------------------------- |
| PROJECT_ID | docker-257914 gcp project_id |
| ZONE | us-central1-a | gcp zone |
| CLUSTER_NAME | reddit-public | gke cluster name |.
| NS | dev |pace to deploy app to |

##### Targets

| target | description |
| ----------------- | --------------------------------------------------------------------- |
| create_cluster | create GKE cluster via terraform |
| configure_kubectl | get credentials and configure `kubectl` to manage created GKE cluster |.
| apply_namespaces | create all namespaces |
| apply_reddit | deploy app to `$(NS)` |
| get_https_link | get `https://${INGRESS_IP}` |.
| gen_cert | Generate certificate for https |
| upload_cert | download the certificate to GKE |.
| infra | create_cluster configure_kubectl |
| deploy | apply_namespaces apply_reddit |
| cert | gen_cert upload_cert |
| all | infra deploy cert |


## HomeWork 22: CI/CD at Kubernetes

### Plan

- Working with Helm
- Deployment of Gitlab in Kubernetes
- Launching a CI/CD conveyor at Kubernetes


### Helm

Helm is a package manager for Kubernetes.

With his help, we will:
1. Standardize the application delivery to Kubernetes
2. Declare infrastructure
3. Deploy new versions of the application


#### Helm - installation

Helm - client-server application. Let's install its client part - console Helm client.

Helm reads the kubectl configuration (`~/.kube/config `) and defines the current context (cluster, user, landscape).

If you want to change the cluster, either change the context with `kubectl config set-context` or load helm's own config file with the flag `--kube-context`.

Let's install Helm's server part - _Tiller_.

_Tiller_ is a Kubernetes addon, i.e. a Pod that communicates with the Kubernetes API.

> For this purpose, it will need to issue _ServiceAccount_ and assign the _RBAC_ roles necessary for the work.

Create a `tiller.yml` file and place it in the
``Yaml
---
apiVersion: v1
kind: ServiceAccount
metadata:
  name: tiller
  namespace: kube-system
---
apiVersion: rbac.authorization.k8s.io/v1beta1
Type: ClusterRoleBinding
metadata:
  name: tiller
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: cluster-admin
subjects:
  - kind: ServiceAccount
    name: tiller
    namespace: kube-system
```
``shell
kubectl apply -f tiller.yml
```
Now let's run the tiller server
``shell
helm init --service-account tiller
```
``log
Creating /home/vscoder/.helm 
Creating /home/vscoder/.helm/repository 
Creating /home/vscoder/.helm/repository/cache 
Creating /home/vscoder/.helm/repository/local 
Creating /home/vscoder/.helm/plugins 
Creating /home/vscoder/.helm/starters 
Creating /home/vscoder/.helm/cache/archive 
Creating /home/vscoder/.helm/repository/repositories.yaml 
Adding stable repo with URL: https://kubernetes-charts.storage.googleapis.com. 
Adding local repo with URL: http://127.0.0.1:8879/charts. 
$HELM_HOME has been configured at /home/vscoder/.helm.

Tiller (the Helm server-side component) has been installed into your Kubernetes Cluster.

Please note: by default, Tiller is deployed with an insecure 'allow unauthenticated users' policy.
To prevent this, run `helm init` with the --tiller-tls-verify flag.
For more information on securing your installation see: https://docs.helm.sh/using_helm/#securing-your-helm-installation.
```

Check out .
``shell
kubectl get pods -n kube-system --selector app=helm
```
``log
NAME READY STATUS RESTARTS AGE
tiller-deploy-54f7455d59-sntsc 1/1 Running 0 4m58s
```


#### Charts

Chart is a package in Helm.

Create a Charts directory in the kubernetes folder with the following directory structure:
``shell
mkdir -p ./Charts/{comment,post,reddit,ui}
tree Charts
```
``log
Charts
├── comment
├─ post
├─ reddit
└─ ui

4 directories, 0 files
```

Let's start developing Chart for the ui component of the application. Create a description file for the chart.
``shell
touch ui/Chart.yaml
```

> Helm prefers ''yaml''.

``Yaml
---
name: ui
version: 1.0.0
description: OTUS reddit application UI
I'm not:
  - name: Someone
    email: my@mail.com
appVersion: 1.0
```

The name and version fields are really important. Helm's work with Chart depends on them. The rest is descriptions.


#### Templates

The main contents of Chart are Kubernetes manifesto templates.

1. Create a directory of `ui/templates`.
   ``shell
   mkdir ui/templates
   ```
2. Transfer to it all manifestos developed earlier for the ui service (`ui-service`, `ui-deployment`, `ui-ingress`).
3. Rename them (remove the prefix "ui-") and change the extension to `.yaml') - stylistic corrections

``shell
tree ui
```
``log
ui
├── Chart.yaml
└── templates
    ├─ deployment.yaml
    ├── ingress.yaml
    └── service.yaml

1 directory, 4 files
```

In fact, it's a ready-made package for installation at Kubernetes.

1. Make sure that you do not have application components deployed in kubernetes. If they are, remove them.
2. Let's install Chart.
   ``shell
   helm install --name test-ui-1 ui/
   ```
   ``log
   NAME: test-ui-1
   LAST DEPLOYED: Tue Jan 7 00:47:13 2020
   NAMESPACE: default
   STATUS: DEPLOYED

   RESOURCES:
   ==> v1/Deployment
   NAME AGE
   ui 0s

   ==> v1/Pod(related)
   NAME AGE
   ui-595f89d499-f5b5v 0s
   ui-595f89d499-xwwxx 0s
   ui-595f89d499-z4fxg 0s

   ==> v1/Service
   NAME AGE
   ui 0s

   ==> v1beta1/Ingress
   NAME AGE
   ui 0s
   ```

> Pass the name and path to Chart respectively 3) 
> Let's see what happens.

``shell
helm ls
```
``log
NAME REVISION UPDATED STATUS CHART APP VERSION NAMESPACE
test-ui-1 1 Tue Jan 7 00:47:13 2020 DEPLOYED ui-1.0.0 1 default
```

Now let's make sure that we can use 1 Chart to run multiple instances (releases). Template it.
`ui/templates/service.yaml`.
``Yaml
---
apiVersion: v1
kind: Service
metadata:
  name: {{{ .Release.Name }}-{{ .Chart.Name }} # We need a unique name for the running resource
  The labels:
    app: reddit
    component: ui
    release: {{ .Release.Name }} # Note that the service from a particular release
spec:
  type: NodePort
  ports:
  - port: 9292
    protocol: TCP
    targetPort: 9292
  Selector:
    app: reddit
    component: ui
    release: {{{ .Release.Name }} # We only choose the substitutions from this release
```

`Name: {{{ .Release.Name }}-{{ .Chart.Name }}.

Here we use the built-in variables
- `.Release' is a group of variables with release information (a specific Chart launch in k8s).
- `.Chart` - a group of variables with information about Chart (content of the file `Chart.yaml`).

There are also groups of variables:
- `.Template' - information about the current template ( `.Name' and `.BasePath').
- `.Capabilities` - information about Kubernetes (version, API versions)
- `.Files.Get` - get the contents of the file

Template the other entities in the same way.

`ui/templates/deployment.yaml`
``Yaml
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: {{{ .Release.Name }}-{{ .Chart.Name }}.
  The labels:
    app: reddit
    component: ui
    release: {{{ .Release.Name }}.
spec:
  replicas: 3
  strategy:
    type: Recreate
  Selector:
    matchLabels:
      app: reddit
      component: ui
      release: {{ .Release.Name }}
  Oh..:
    metadata:
      name: ui
      The labels:
        app: reddit
        component: ui
        release: {{ .Release.Name }}
    spec:
      containers:
      - image: vscoder/ui
        name: ui
        ports:
        - containerPort: 9292
          name: ui
          protocol: TCP
        I'm sorry:
        - name: ENV
          valueFrom:
            fieldRef:
              fieldPath: metadata.space
```
**It's important** that the Deployant Selector only finds the right pods.

Don't forget to put your images

Template the other entities in the same way.
`ui/templates/ingress.yaml``
``Yaml
---
apiVersion: extensions/v1beta1
kind: Ingress
metadata:
  name: {{{ .Release.Name }}-{{ .Chart.Name }}.
  annotations:
    kubernetes.io/ingress.class: "gce"
spec:
  rules:
  - http:
      paths:
      - path: /*
        backend:
          serviceName: {{{ .Release.Name }}-{{ .Chart.Name }}.
          servicePort: 9292
```

We'll install a few releases of ui
``shell
helm install --name test-ui-2 ui/
```
``log
NAME: test-ui-2
LAST DEPLOYED: Tue Jan 7 12:08:29 2020
NAMESPACE: default
STATUS: DEPLOYED

RESOURCES:
==> v1/Deployment
NAME AGE
test-ui-2-ui 0s

==> v1/Pod(related)
NAME AGE
test-ui-2-ui-b6cb9c46c-cf2ks 0s
test-ui-2-ui-b6cb9c46c-mksp7 0s
test-ui-2-ui-b6cb9c46c-xz8ll 0s

==> v1/Service
NAME AGE
test-ui-2-ui 0s

==> v1beta1/Ingress
NAME AGE
test-ui-2-ui 0s
```

``shell
helm install --name test-ui-3 ui/
```
``log
NAME: test-ui-3
LAST DEPLOYED: Tue Jan 7 12:08:58 2020
NAMESPACE: default
STATUS: DEPLOYED

RESOURCES:
==> v1/Deployment
NAME AGE
test-ui-3-ui 1s

==> v1/Pod(related)
NAME AGE
test-ui-3-ui-669675d44b-dg4xb 1s
test-ui-3-ui-669675d44b-q5rnp 1s
test-ui-3-ui-669675d44b-tl6m5 1s

==> v1/Service
NAME AGE
test-ui-3-ui 1s

==> v1beta1/Ingress
NAME AGE
test-ui-3-ui 1s
```

> Where ui-(1/2/3) - release names

There should be 3 ingress.
``shell
kubectl get ingress
```
``log
NAME HOSTS ADDRESS PORTS AGE
test-ui-2-ui * 34.95.116.107 80 70s
test-ui-3-ui * 80 41s
ui * 80, 443 11h
```
The conclusion is a little different than expected... Apparently, something went wrong during the first setup)).

By IP addresses you can get to different releases of ui applications.

P.S. Wait a couple of minutes until ingresses are available.

We have already made it possible to launch several versions of applications from a single manifest package using only built-in variables. We customize the installation with our variables (image and port).

`ui/templates/deployment.yaml`.
``Yaml
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: {{{ .Release.Name }}-{{ .Chart.Name }}.
  The labels:
    app: reddit
    component: ui
    release: {{{ .Release.Name }}.
spec:
  replicas: 3
  strategy:
    type: Recreate
  Selector:
    matchLabels:
      app: reddit
      component: ui
      release: {{ .Release.Name }}
  Oh..:
    metadata:
      name: ui
      The labels:
        app: reddit
        component: ui
        release: {{ .Release.Name }}
    spec:
      containers:
      - image: "{{{ .Values.image.repository }}:{{{ .Values.image.tag }}".
        name: ui
        ports:
        - containerPort: {{ .Values.service.internalPort }}.
          name: ui
          protocol: TCP
        I'm sorry:
        - name: ENV
          valueFrom:
            fieldRef:
              fieldPath: metadata.space
...
```

`ui/templates/service.yaml`
``Yaml
---
apiVersion: v1
kind: Service
metadata:
  name: {{{ .Release.Name }}-{{ .Chart.Name }}.
  The labels:
    app: reddit
    component: ui
    release: {{{ .Release.Name }}.
spec:
  type: NodePort
  ports:
  - port: {{{ .Values.service.externalPort }}.
    protocol: TCP
    targetPort: {{{ .Values.service.internalPort }}.
  Selector:
    app: reddit
    component: ui
    release: {{{ .Release.Name }}.
...
```

`ui/templates/ingress.yaml``
``Yaml
---
apiVersion: extensions/v1beta1
kind: Ingress
metadata:
  name: {{{ .Release.Name }}-{{ .Chart.Name }}.
  annotations:
    kubernetes.io/ingress.class: "gce"
spec:
  rules:
  - http:
      paths:
      - path: /
        backend:
          serviceName: {{{ .Release.Name }}-{{ .Chart.Name }}.
          service port: {{{ .Values.service.externalPort}}.
...
```

Let's define the values of our own variables `ui/values.yaml`.
``Yaml
---
service:
  internalPort: 9292
  externalPort: 9292

image:
  repository: vscoder/ui
  tag: latest
```

``shell
helm upgrade test-ui-1 ui/
```
``log
Release "test-ui-1" has been upgraded.
LAST DEPLOYED: Tue Jan 7 12:22:58 2020
NAMESPACE: default
STATUS: DEPLOYED

RESOURCES:
==> v1/Deployment
NAME AGE
test-ui-1-ui 0s

==> v1/Pod(related)
NAME AGE
test-ui-1-ui-56cbd9b9ff-776hc 0s
test-ui-1-ui-56cbd9b9ff-gnldq 0s
test-ui-1-ui-56cbd9b9ff-wrtp5 0s

==> v1/Service
NAME AGE
test-ui-1-ui 0s

==> v1beta1/Ingress
NAME AGE
test-ui-1-ui 0s
```
The release was created because it didn't exist before.

``shell
helm upgrade test-ui-2 ui/
```
``log
Release "test-ui-2" has been upgraded.
LAST DEPLOYED: Tue Jan 7 12:23:32 2020
NAMESPACE: default
STATUS: DEPLOYED

RESOURCES:
==> v1/Deployment
NAME AGE
test-ui-2-ui 15m

==> v1/Pod(related)
NAME AGE
test-ui-2-ui-b6cb9c46c-cf2ks 15m
test-ui-2-ui-b6cb9c46c-mksp7 15m
test-ui-2-ui-b6cb9c46c-xzz8ll 15m

==> v1/Service
NAME AGE
test-ui-2-ui 15m

==> v1beta1/Ingress
NAME AGE
test-ui-2-ui 15m
```
And this release has been updated

``shell
helm upgrade test-ui-3 ui/
```
``log
Release "test-ui-3" has been upgraded.
LAST DEPLOYED: Tue Jan 7 12:24:35 2020
NAMESPACE: default
STATUS: DEPLOYED

RESOURCES:
==> v1/Deployment
NAME AGE
test-ui-3-ui 15m

==> v1/Pod(related)
NAME AGE
test-ui-3-ui-669675d44b-dg4xb 15m
test-ui-3-ui-669675d44b-q5rnp 15m
test-ui-3-ui-669675d44b-tl6m5 15m

==> v1/Service
NAME AGE
test-ui-3-ui 15m

==> v1beta1/Ingress
NAME AGE
test-ui-3-ui 15m
```
And this one has been updated

We built Chart to deploy the application's ui components. It should have the following structure
``shell
tree ui
```
``log
ui
├── Chart.yaml
├── templates
│ ├─ deployment.yaml
│ ├── ingress.yaml
│ └── service.yaml
└── values.yaml

1 directory, 5 files
```

All that remains is to build the packages for the other components

#### Post

`post/templates/service.yaml`
``Yaml
---
apiVersion: v1
kind: Service
metadata:
  name: {{{ .Release.Name }}-{{ .Chart.Name }}.
  The labels:
    app: reddit
    post
    release: {{ .Release.Name }}
spec:
  type: ClusterIP
  ports:
  - port: {{{ .Values.service.externalPort }}.
    protocol: TCP
    targetPort: {{{ .Values.service.internalPort }}.
  Selector:
    app: reddit
    post
    release: {{ .Release.Name }}
...
```

`post/templates/deployment.yaml`
``Yaml
---
apiVersion: apps/v1beta2
kind: Deployment
metadata:
  name: {{{ .Release.Name }}-{{ .Chart.Name }}.
  The labels:
    app: reddit
    post
    release: {{ .Release.Name }}
spec:
  replicas: 1
  selector:
    matchLabels:
      app: reddit
      post
      release: {{ .Release.Name }}
  Oh..:
    metadata:
      name: post
      The labels:
        app: reddit
        post
        release: {{ .Release.Name }}
    spec:
      containers:
      - image: "{{{ .Values.image.repository }}:{{{ .Values.image.tag }}".
        name: post
        ports:
        - containerPort: {{ .Values.service.internalPort }}.
          name: post
          protocol: TCP
        I'm sorry:
        - name: POST_DATABASE_HOST
          value: {{ .Values.databaseHost }}
```

Please note the database address
``Yaml
I'm sorry:
  - name: POST_DATABASE_HOST
    value: postdb
```

Since the database address may change depending on the launch conditions:
- DB is separate from the cluster
- HD is available as a separate release
- ... ...then we'll create a convenient template for setting the database address.

``Yaml
I'm sorry:
  - name: POST_DATABASE_HOST
    value: {{ .Values.databaseHost }}
```

We'll specify dd via the variable `databaseHost`. Sometimes it is better to use such a variable format instead of `database.host` structures, because then you will have to define the database structure, otherwise helm will generate an error.

Let's use the `default()` function. If `databaseHost` is not defined or its value is empty, the output of `printf()` function is used (which simply forms the string `<release name>-mongodb>).
``Yaml
value: {{{ .Values.databaseHost | default (printf "%s-mongodb" .Release.Name) }}.
```
> release-name-mongodb

It should end up as follows.
``Yaml
       I'm sorry:
        - name: POST_DATABASE_HOST
          value: {{{ .Values.databaseHost | default (printf "%s-mongodb" .Release.Name) }}.
```
Now, if databaseHost is not specified, the address of the base raised inside the release will be used.

We end up with the following.
`post/templates/deployment.yaml`
``Yaml
---
apiVersion: apps/v1beta2
kind: Deployment
metadata:
  name: {{{ .Release.Name }}-{{ .Chart.Name }}.
  The labels:
    app: reddit
    post
    release: {{ .Release.Name }}
spec:
  replicas: 1
  selector:
    matchLabels:
      app: reddit
      post
      release: {{ .Release.Name }}
  Oh..:
    metadata:
      name: post
      The labels:
        app: reddit
        post
        release: {{ .Release.Name }}
    spec:
      containers:
      - image: "{{{ .Values.image.repository }}:{{{ .Values.image.tag }}".
        name: post
        ports:
        - containerPort: {{ .Values.service.internalPort }}.
          name: post
          protocol: TCP
        I'm sorry:
            - name: POST_DATABASE_HOST
            value: {{{ .Values.databaseHost | default (printf "%s-mongodb" .Release.Name) }}.
```

More detailed [documentation] (https://helm.sh/docs/chart_template_guide/#the-chart-template-developer-s-guide) on templating and functions

`post/values.yaml`
``Yaml
---
service:
  internalPort: 5000
  externalPort: 5000

image:
  repository: vscoder/post
  tag: latest

databaseHost:
```

`post/Chart.yaml`
``Yaml
---
name: post
version: 1.0.0
description: OTUS reddit application Post
I'm not:
  - name: Someone
    email: my@mail.com
appVersion: 1.0
```


#### Comment

Template service comment:

Here everything is very similar to post service:

`comment/templates/deployment.yaml'.
``Yaml
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: {{{ .Release.Name }}-{{ .Chart.Name }}.
  The labels:
    app: reddit
    component: comment
    release: {{{ .Release.Name }}.
spec:
  replicas: 1
  selector:
    matchLabels:
      app: reddit
      component: comment
      release: {{ .Release.Name }}
  Oh..:
    metadata:
      name: comment
      The labels:
        app: reddit
        component: comment
        release: {{ .Release.Name }}
    spec:
      containers:
      - image: "{{{ .Values.image.repository }}:{{{ .Values.image.tag }}".
        name: comment
        ports:
        - containerPort: {{ .Values.service.internalPort }}.
          name: comment
          protocol: TCP
        I'm sorry:
        - name: COMMENT_DATABASE_HOST
          value: {{{ .Values.databaseHost | default (printf "%s-mongodb" .Release.Name) }}.
```

`comment/templates/service.yaml`
``Yaml
---
apiVersion: v1
kind: Service
metadata:
  name: {{{ .Release.Name }}-{{ .Chart.Name }}.
  The labels:
    app: reddit
    component: comment
    release: {{{ .Release.Name }}.
spec:
  type: ClusterIP
  ports:
  - port: {{{ .Values.service.externalPort }}.
    protocol: TCP
    targetPort: {{{ .Values.service.internalPort }}.
  Selector:
    app: reddit
    component: comment
    release: {{{ .Release.Name }}.
```

`comment/values.yaml`
``Yaml
---
service:
  internalPort: 9292
  externalPort: 9292

image:
  repository: vscoder/comment
  tag: latest

databaseHost:
```

don't forget to add `Chart.yaml'.
``Yaml
---
name: comment
version: 1.0.0
description: OTUS reddit application Comment
I'm not:
  - name: Someone
    email: my@mail.com
appVersion: 1.0
```

The final structure looks like this:
``shell
tree ./
```
``log
./
├── comment
│ ├── Chart.yaml
│ ├── templates
│ │ ├── deployment.yaml
│ │ └── service.yaml
│ └── values.yaml
├─ post
│ ├── Chart.yaml
│ ├── templates
│ │ ├── deployment.yaml
│ │ └── service.yaml
│ └── values.yaml
├─ reddit
└─ ui
    ├── Chart.yaml
    ├── templates
    │ ├─ deployment.yaml
    │ ├── ingress.yaml
    │ └── service.yaml
    └── values.yaml

7 directories, 13 files
```


#### Helpers

It is also worth noting the helm functionality for using helpers and templates. 

**Helper** is a function written by us. The function describes, as a rule, complex logic. Templates of these functions are arranged in the file `_helpers.tpl`.

An example of the function `comment.fullname`:

`Charts/comment/templates/_helpers.tpl`.
```
{- define "comment.fullname" }}
{{-printf "%s-%s" .Release.Name .Chart.Name }}.
{- end -}
```

which will result in the same output as: `{{ .Release.Name }}-{{ .Chart.Name }}}.

And replace it with the appropriate lines in the file to use the helper.

`comment/templates/service.yaml`
``Yaml
---
apiVersion: v1
kind: Service
metadata:
  name: {{{ template "comment.fullname"}. }}
  The labels:
    app: reddit
    component: comment
    release: {{ .Release.Name }}
spec:
  type: ClusterIP
  ports:
  - port: {{{ .Values.service.externalPort }}.
    protocol: TCP
    targetPort: {{{ .Values.service.internalPort }}.
  Selector:
    app: reddit
    component: comment
    release: {{{ .Release.Name }}.
```

Structure of the transport function
```t
{{ 
  template # The template function
  "comment.fullname" # Name of the function to import
  .                   # Scope of visibility for import
}}
```

**". "** - all scope of all variables (you can pass `.Chart`, then `.Values` will not be available inside the function).


#### Assignment

1. Create files `_helpers.tpl` in the templates folders of _ui_, _post_ and _comment_ services.
   1. File `_helpers.tpl` is copied into `post/templates/` and `ui/templates/`.
2. Insert the ".fullname" function into each `_helpers.tpl` file. Replace with the chart name of the corresponding service.
   The function name has been changed to `post.fullname' and `ui.fullname' respectively.
3. In each of the manifest templates, insert the following function where required (most fields are name: `{{ template "comment.fullname" . }}}.
   1. `{{ .Release.Name }}-{{ .Chart.Name }}` for all manifest templates are replaced by the corresponding template call


#### Addiction management

The structure is as follows:
``shell
tree.
```
``log
.
├── comment
│ ├── Chart.yaml
│ ├── templates
│ │ ├── deployment.yaml
│ │ ├─ _helpers.tpl
│ │ └── service.yaml
│ └── values.yaml
├─ post
│ ├── Chart.yaml
│ ├── templates
│ │ ├── deployment.yaml
│ │ ├─ _helpers.tpl
│ │ └── service.yaml
│ └── values.yaml
├─ reddit
└─ ui
    ├── Chart.yaml
    ├── templates
    │ ├─ deployment.yaml
    │ ├─ _helpers.tpl
    │ ├── ingress.yaml
    │ └── service.yaml
    └── values.yaml
```

We have created Chart's for every component of our application. Each of them can be run separately with a command
``shell
helm install <chart-path> --name <release-name>
```

But they will run in different releases, and will not see each other. With the help of the dependency management mechanism, let's create...
a single Chart `reddit` that will combine our components.
![](kubernetes/img/helm-scheme-reddit.png)

1. Create `reddit/Chart.yaml`.
``Yaml
---
name: reddit
version: 0.1.0
description: OTUS sample reddit application
I'm not:
  - name: Aleksey Koloskov
    email: vsyscoder@gmail.com
```
> Fill in the name and email options with your data (OK)
2. Create an empty `reddit/values.yaml'.

In Chart's reddit directory let's create the file `reddit/requirements.yaml`.
``Yaml
---
I'm sorry:
  - name: ui
    version: "1.0.0"
    repository: "file://.../ui"

  - name: post
    version: "1.0.0"
    repository: "file://.../post"

  - name: comment
    version: "1.0.0"
    repository: "file://.../comment"
...
```

> Name and version must match the content of `ui/Chart.yml`.
> The path is indicated relative to the location of the `requirements.yaml` itself.

Need to download dependencies (when Chart' is not packed in tgz archive).
``shell
helm dep dep update
```
``log
Hang tight while we grab the latest from your chart repositories.
...Unable to get an update from the "local" chart repository (http://127.0.0.1:8879/charts):
        Get http://127.0.0.1:8879/charts/index.yaml: dial tcp 127.0.0.1:8879: connect: connection refused
...Successfully got an update from the "stable" chart repository...
Update Complete.
Saving 3 charts
Deleting outdated charts
```

You will see the file `requirements.lock` with dependency commits. A directory of charts with dependencies will be created as archives.

The structure is as follows:
``shell
tree reddit 
```
``log
reddit
├─ charts
│ ├── comment-1.0.0.tgz
│ ├── post-1.0.0.tgz
│ └─ ui-1.0.0.tgz
├── Chart.yaml
├─ requirements.lock
├── requirements.yaml
└── values.yaml

1 directory, 7 files
```

We will not create Chart for the database manually. We'll take the ready one.

We'll find the Chart in a public repository.
``shell
helm search mongo
```
``log
NAME CHART VERSION APP VERSION DESCRIPTION                                                 
stable/mongodb 7.6.3 4.0.14 NoSQL document-oriented database that stores JSON-like do...
stable/mongodb-replicaset 3.11.2 3.6 NoSQL document-oriented database that stores JSON-like do...
stable/prometheus-mongodb-exporter 2.4.0 v0.10.0 A Prometheus exporter for MongoDB metrics                   
stable/unifi 0.5.2 5.11.50 Ubiquiti Network's Unifi Controller
```

Let's add it to `reddit/requirements.yml`.
``Yaml
---
I'm sorry:
  - name: ui
    version: 1.0.0
    repository: "file://.../ui"

  - name: post
    version: 1.0.0
    repository: "file://.../post"

  - name: comment
    version: 1.0.0
    repository: "file://.../comment"

  - name: mongodb
    version: 7.2.8
    repository: https://kubernetes-charts.storage.googleapis.com
...
```

Let's offload dependencies
``shell
helm dep dep update
```
``log
Hang tight while we grab the latest from your chart repositories.
...Unable to get an update from the "local" chart repository (http://127.0.0.1:8879/charts):
        Get http://127.0.0.1:8879/charts/index.yaml: dial tcp 127.0.0.1:8879: connect: connection refused
...Successfully got an update from the "stable" chart repository...
Update Complete.
Saving 4 charts
Downloading mongodb from repo https://kubernetes-charts.storage.googleapis.com
Deleting outdated charts
```
``shell
tree reddit
```
``log
reddit
├─ charts
│ ├── comment-1.0.0.tgz
│ ├── mongodb-7.2.8.tgz
│ ├── post-1.0.0.tgz
│ └─ ui-1.0.0.tgz
├── Chart.yaml
├─ requirements.lock
├── requirements.yaml
└── values.yaml

1 directory, 8 files
```

Let's install our application:
``shell
helm install reddit --name reddit-test
```
``log
Error: YAML parse error on reddit/charts/post/templates/deployment.yaml: error converting YAML to JSON: yaml: line 32: did not find expected '-' indicator
```
Fix `post/templates/deployment.yaml'.
``Yaml
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: {{{ template "post.fullname"}. }}
  The labels:
    app: reddit
    post
    release: {{{ .Release.Name }}
spec:
  replicas: 1
  Selector:
    matchLabels:
      app: reddit
      post
      release: {{{ .Release.Name }}
  Oh..:
    metadata:
      name: post
      The labels:
        app: reddit
        post
        release: {{{ .Release.Name }}
    spec:
      containers:
      - image: "{{{ .Values.image.repository }}:{{{ .Values.image.tag }}".
        name: post
        ports:
        - containerPort: {{{ .Values.service.internalPort }}.
          name: post
          Protocol: TCP
        I'm sorry:
        - name: POST_DATABASE_HOST
          value: {{{ .Values.databaseHost | default (printf "%s-mongodb" .Release.Name) }}.
```
``shell
helm dep dep update
```
``log
Hang tight while we grab the latest from your chart repositories.
...Unable to get an update from the "local" chart repository (http://127.0.0.1:8879/charts):
        Get http://127.0.0.1:8879/charts/index.yaml: dial tcp 127.0.0.1:8879: connect: connection refused
...Successfully got an update from the "stable" chart repository...
Update Complete.
Saving 4 charts
Downloading mongodb from repo https://kubernetes-charts.storage.googleapis.com
Deleting outdated charts
```
``shell
helm install reddit --name reddit-test
```
``log
NAME: reddit-test
LAST DEPLOYED: Wed Jan 8 15:47:48 2020
NAMESPACE: default
STATUS: DEPLOYED

RESOURCES:
==> v1/Deployment
NAME AGE
reddit-test-comment 1s
reddit-test-post 1s
reddit-test-ui 1s

==> v1/PersistentVolumeClaim
NAME AGE
reddit-test-mongodb 1s

==> v1/Pod(related)
NAME AGE
reddit-test-comment-5cf7784c46-mhrm5 1s
reddit-test-mongodb-bd574dbb8-ltkdh 1s
reddit-test-post-66b4846455-csb59 1s
reddit-test-ui-9d7d5c8c-cfdtm 1s
reddit-test-ui-9d7d5c8c-ls6x5 1s
reddit-test-ui-9d7d5c8c-qgz97 1s

==> v1/Secret
NAME AGE
reddit-test-mongodb 1s

==> v1/Service
NAME AGE
reddit-test-comment 1s
reddit-test-mongodb 1s
reddit-test-post 1s
reddit-test-ui 1s

==> v1beta1/Deployment
NAME AGE
reddit-test-mongodb 1s

==> v1beta1/Ingress
NAME AGE
reddit-test-ui 1s
```


Find the ingress address with kubectl.
``shell
kubectl get ingress
```
``log
NAME HOSTS ADDRESS PORTS AGE
reddit-test-ui * 34.107.198.236 80 38s
test-ui-1-ui * 34.107.213.1 80 27h
test-ui-2-ui * 34.95.116.107 80 27h
test-ui-3-ui * 35.244.235.133 80 27h
```
``shell
kubectl describe ingresses reddit-test-ui
```
``log
Name: reddit-test-ui
Namespace: default
Address:          34.107.198.236
Default backend: default-http-backend:80 (10.4.0.2:8080)
Rules:
  Host Path Backends
  ---- ---- --------
  *     
        / reddit-test-ui:9292 (<none>)
Annotations:
  ingress.kubernetes.io/backends:         {"k8s-be-30484--bb36bed10e2d33ef": "Unknown", "k8s-be-31427--bb36bed10e2d33ef": "HEALTHY" }
  ingress.kubernetes.io/forwarding-rule: k8s-fw-default-reddit-test-ui--bb36bed10e2d33ef
  ingress.kubernetes.io/target-proxy: k8s-tp-default-reddit-test-ui--bb36bed10e2d33ef
  ingress.kubernetes.io/url-map: k8s-um-default-reddit-test-ui--bb36bed10e2d33ef
  kubernetes.io/ingress.class: gce
Events:
  Type Reason Age From Message
  ---- ------ ---- ---- -------
  Normal ADD 90s loadbalancer-controller default/reddit-test-ui
  Normal CREATE 52s loadbalancer-controller ip: 34.107.198.236
```

Wait until ingress is processed and... opened)
> Can't show blog posts, some problems with the post service. Refresh?

There is a problem that the UI service does not know how to properly go to the post and comment services. After all, their names are now dynamic and depend on the names of the charts.

In `Dockerfile` UI services, the environment variables are already set. We need them to point to the right backends.
``dockerfile
ENV POST_SERVICE_HOST post
ENV POST_SERVICE_PORT 5000
ENV COMMENT_SERVICE_HOST comment
ENV COMMENT_SERVICE_PORT 9292
```

Let's add it to `ui/deployments.yaml`.
``Yaml
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: {{{ template "ui.fullname"}. }}
  The labels:
    app: reddit
    component: ui
    release: {{{ .Release.Name }}
spec:
  replicas: 3
  strategy:
    type: Recreate
  Selector:
    matchLabels:
      app: reddit
      component: ui
      release: {{{ .Release.Name }}
  Oh..:
    metadata:
      name: ui
      The labels:
        app: reddit
        component: ui
        release: {{{ .Release.Name }}
    spec:
      containers:
      - image: {{{ .Values.image.repository }}:{{{ .Values.image.tag }}.
        name: ui
        ports:
        - containerPort: {{{ .Values.service.internalPort }}.
          name: ui
        I'm sorry:
        - name: POST_SERVICE_HOST
          value: {{{ .Values.postHost | default (printf "%s-post" .Release.Name) }}.
        - name: POST_SERVICE_PORT
          value: {{{ .Values.postPort |} default "5000." | quote }}
        - name: COMMENT_SERVICE_HOST
          value: {{{ .Values.commentHost | default (printf "%s-comment" .Release.Name) }}.
        - name: COMMENT_SERVICE_PORT
          value: {{{ .Values.commentPort} | default "9292." | quote }}
        - name: ENV
          valueFrom:
            fieldRef:
              fieldPath: metadata.space
...
```

> `{{ .Values.commentPort | default "9292"] | quote }} ` ❗ note the function to add quotes. This is important for numbers and Boolean values!

Let's add it to `ui/values.yaml`.
``Yaml
---
service:
  internalPort: 9292
  externalPort: 9292

image:
  repository: vscoder/ui
  tag: latest

ingress:
  class: nginx

postHost:
postPort:
commentHost:
commentPort:
```

You can even recommend these parameters or leave them blank. The important thing is that they're in Chart's configuration ** as documentation**.

You can now specify variables for dependencies directly in `values.yaml` of Chart's own reddit. They overwrite the values of the variables in the dependent charts.

"reddit/values.yaml
``Yaml
---
comment:
  image:
    repository: vscoder/comment
    tag: latest
  service:
    externalPort: 9292

Post:
  image:
    repository: vscoder/post
    tag: latest
  service:
    externalPort: 5000

ui:
  image:
    repository: vscoder/ui
    tag: latest
  service:
    externalPort: 9292
```
> We refer to chart variables from dependencies

After updating the UI - you need to update the reddit card dependencies.
``shell
helm dep update ./reddit
```
``log
Hang tight while we grab the latest from your chart repositories.
...Unable to get an update from the "local" chart repository (http://127.0.0.1:8879/charts):
        Get http://127.0.0.1:8879/charts/index.yaml: dial tcp 127.0.0.1:8879: connect: connection refused
...Successfully got an update from the "stable" chart repository...
Update Complete.
Saving 4 charts
Downloading mongodb from repo https://kubernetes-charts.storage.googleapis.com
Deleting outdated charts
```

Update the release installed in k8s
``shell
helm upgrade <release-name> ./reddit
```
``log
Release "reddit-test" has been upgraded.
LAST DEPLOYED: Wed Jan 8 17:10:55 2020
NAMESPACE: default
STATUS: DEPLOYED

RESOURCES:
==> v1/Deployment
NAME AGE
reddit-test-comment 83m
reddit-test-post 83m
reddit-test-ui 83m

==> v1/PersistentVolumeClaim
NAME AGE
reddit-test-mongodb 83m

==> v1/Pod(related)
NAME AGE
reddit-test-comment-5cf7784c46-mhrm5 83m
reddit-test-mongodb-bd574dbb8-ltkdh 83m
reddit-test-post-66b4846455-csb59 83m
reddit-test-ui-9d7d5c8c-cfdtm 83m
reddit-test-ui-9d7d5c8c-ls6x5 83m
reddit-test-ui-9d7d5c8c-qgz97 83m

==> v1/Secret
NAME AGE
reddit-test-mongodb 83m

==> v1/Service
NAME AGE
reddit-test-comment 83m
reddit-test-mongodb 83m
reddit-test-post 83m
reddit-test-ui 83m

==> v1beta1/Deployment
NAME AGE
reddit-test-mongodb 83m

==> v1beta1/Ingress
NAME AGE
reddit-test-ui 83m
```


#### helm2 tiller plugin

Prior to that, we deploded with a cluster-admin, which is not safe**. There is a concept of creating a tiller in every namepace and giving it only the necessary rights. To avoid creating namespace and tiller in it with your hands every time, use [tiller plugin](https://github.com/rimusz/helm-tiller)([description](https://rimusz.net/tillerless-helm)).

1. Let us remove the already existing tiller from the cluster ([article](https://stackoverflow.com/questions/47583821/how-to-delete-tiller-from-kubernetes-cluster/47583918));
``shell
helm reset
```
``log
Error: there are still 4 deployed releases. Releases will not be deleted.
```
``shell
helm reset --force
```
``log
Tiller (the Helm server-side component) has been uninstalled from your Kubernetes Cluster.
```

2. Let's perform the installation of the plugin and the depression itself in the new namespace `reddit-ns`:
``shell
helm init --client-only
```
``log
$HELM_HOME has been configured at /home/vscoder/.helm.
Not installing Tiller due to 'client-only' flag having been set
```
``shell
helm plugin install https://github.com/rimusz/helm-tiller
```
``log
Installed plugin: tiller
```
``shell
cd kubernetes/Charts
helm tiller run -- helm upgrade --install --wait --namespace=reddit-ns reddit reddit/
```
``log
Installed Helm version v2.16.1
Installed Tiller version v2.16.1
Helm and Tiller are the same version!
Starting Tiller...
Tiller namespace: kube-system
Running: helm upgrade --install --wait --namespace=reddit-ns reddit reddit/

Release "reddit" does not exist. Installing it now.
NAME: reddit
LAST DEPLOYED: Wed Jan 8 19:48:26 2020
NAMESPACE: reddit-ns
STATUS: DEPLOYED

RESOURCES:
==> v1/Deployment
NAME AGE
reddit-comment 20s
reddit-post 20s
reddit-ui 20s

==> v1/PersistentVolumeClaim
NAME AGE
reddit-mongodb 21s

==> v1/Pod(related)
NAME AGE
reddit-comment-5c9999f4d4-8nn5t 20s
reddit-mongodb-6fd8c46f6b-ztrfw 20s
reddit-post-5df6798d67-h7ntz 20s
reddit-ui-9b5b66dc4-btq6b 20s
reddit-ui-9b5b66dc4-mtzsr 20s
reddit-ui-9b5b66dc4-z4slk 20s

==> v1/Secret
NAME AGE
reddit-mongodb 21s

==> v1/Service
NAME AGE
reddit-comment 21s
reddit-mongodb 20s
reddit-post 21s
reddit-ui 21s

==> v1beta1/Deployment
NAME AGE
reddit-mongodb 20s

==> v1beta1/Ingress
NAME AGE
reddit-ui 20s


Stopping Tiller...
```

3. Let's check that everything is successful, having received an ipe from `kubectl get ingress -n reddit-ns` and having passed on it. No O_o address.

Reason: `Kubectl get ingress -n reddit-ns`
``log
Warning Sync 7m1s (x23 over 43m) loadbalancer-controller Error during sync: error running backend syncing routine: googleapi: Error 403: QUOTA_EXCEEDED - Quota 'BACKEND_SERVICES' exceeded.  Limit: 5.0 globally.
```

Looks like we should have removed the releases from the old Helm before we removed the Tyler... Now I'm gonna need some pens.
``hell.
kubectl delete ingress test-ui-3-ui
kubectl delete ingress test-ui-2-ui
kubectl delete ingress test-ui-1-ui
```

TODO: remember to clean up the rest of the creatures.

We're watching ip again.
``shell
kubectl get ingress -n reddit-ns
```
``log
NAME HOSTS ADDRESS PORTS AGE
reddit-ui * 34.107.225.231 80 83m
```
``log
Can't show blog posts, some problems with the post service. Refresh?
```

Well, it should work... Diagnosis
``shell
kubectl -n reddit-ns logs reddit-ui-9b5b66dc4-d45sd
```
``log
E, [2020-01-08T18:59:33.443574 #1] ERROR -- : service=ui | event=show_all_posts | request_id=554047ae-f986-4d0a-a63f-abf5d81f8e09 | message='Failed to read from Post service. Reason: getaddrinfo: Try again' | params: "{}"
```
``shell
kubectl -n reddit-ns describe deployments reddit-ui
```
``log
Name: reddit-ui
Namespace: reddit-ns
CreationTimestamp:  Wed, 08 Jan 2020 19:48:29 +0300
Labels: app=reddit
                    component=ui
                    release=reddit
Annotations: deployment.kubernetes.io/revision: 1
Selector: app=reddit,component=ui,release=reddit
Replicas:           3 desired | 3 updated | 3 total | 3 available | 0 unavailable
StrategyType:       Recreate
MinReadySeconds:    0
Pod Template:
  Labels: app=reddit
           component=ui
           release=reddit
  Containers:
   ui:
    Image: vscoder/ui:latest
    Port: 9292/TCP
    Host Port: 0/TCP
    Environment:
      POST_SERVICE_HOST: reddit-post
      POST_SERVICE_PORT: 5000
      COMMENT_SERVICE_HOST: reddit-comment
      COMMENT_SERVICE_PORT: 9292
      ENV: (v1:metadata.namespace)
    Mounts:                  <none>
  Volumes:                   <none>
Conditions:
  Type Status Reason
  ---- ------ ------
  Progressing True NewReplicaSetAvailable
  Available True MinimumReplicasAvailable
OldReplicaSets:  <none>
NewReplicaSet: reddit-ui-9b5b66dc4 (3/3 replicas created)
Events:          <none>
```

After about 20 minutes, the list of posts (more precisely, no posts) is displayed correctly. But when trying to create a post http://34.107.225.231/new, the error
``log
default backend - 404
```

TODO: Fix it tomorrow

in the meantime, the drop in infra
``shell
cd ./kubernetes/terraform
make destroy
```

Infra's up again. Going in.
``hell.
cd ./kubernetes/terraform
make apply
gcloud container clusters get-credentials reddit-public --zone us-central1-a --project docker-257914
cd -
make install_helm HELM_VERSION=2.16.1
helm init --client-only
helm plugin install https://github.com/rimusz/helm-tiller
cd kubernetes/Charts
helm tiller run -- helm upgrade --install --wait --namespace=reddit-ns reddit reddit/
```

``shell
kubectl get ingresses -n reddit-ns 
```
``log
NAME HOSTS ADDRESS PORTS AGE
reddit-ui * 34.107.213.1 80 6m56s
```
Same error when you go to http://34.107.213.1. And when trying to create the post http://34.107.213.1/new, too.

In `./ui/templates/ingress.yaml' fixed `path:`.
``yaml``
---
apiVersion: extensions/v1beta1
kind: Ingress
metadata:
  name: {{{ template "ui.fullname"}. }}
  annotations:
    kubernetes.io/ingress.class: "gce"
spec:
  rules:
  - http:
      paths:
      - path: /* # previously was just /
        backend:
          serviceName: {"pos(template "ui.fullname"}. }}
          servicePort: {{{ .Values.service.externalPort }}.
...
```

Now it is possible to create a post, but the list of posts is still not displayed.
> Can't show blog posts, some problems with the post service. Refresh?

Maybe Ingress lag at the google, or the addresses of `post` and `comment` services are transmitted incorrectly to the `ui` service. Wait a minute.

Wait. Didn't help))

Let's see the logs
``shell
kubectl logs reddit-ui-9b5b66dc4-6jc8j -n reddit-ns
```
``log
E, [2020-01-09T16:52:57.764164 #1] ERROR -- : service=ui | event=show_all_posts | request_id=afdd1428-8294-4e7c-a076-03c5d2118bf5 | message='Failed to read from Post service. Reason: 776: unexpected token at 'Internal Server Error'' | params: "{}"
I, [2020-01-09T16:52:57.783509 #1] INFO -- : service=ui | event=request | path=/ | request_id=afdd1428-8294-4e7c-a076-03c5d2118bf5 | remote_addr=10.3.0.3 | method= GET | response_status=200.
E, [2020-01-09T16:53:31.584705 #1] ERROR -- : service=ui | event=show_all_posts | request_id=9254f99d-8044-4d2e-bb96-be1f120d6633 | message='Failed to read from Post service. Reason: 776: unexpected token at 'Internal Server Error'' | params: "{}"
I, [2020-01-09T16:53:31.684601 #1] INFO -- : service=ui | event=request | path=/ | request_id=9254f99d-8044-4d2e-bb96-be1f120d6633 | remote_addr=10.3.0.4 | method= GET | response_status=200.
E, [2020-01-09T16:53:33.100635 #1] ERROR -- : service=ui | event=show_all_posts | request_id=3ee616b9-f35f-4dcb-bf72-1f9ff996d765 | message='Failed to read from Post service. Reason: 776: unexpected token at 'Internal Server Error'' | params: "{}"
I, [2020-01-09T16:53:33.150194 #1] INFO -- : service=ui | event=request | path=/ | request_id=3ee616b9-f35f-4dcb-bf72-1f9ff996d765 | remote_addr=10.3.0.4 | method= GET | response_status=200.
```

And here's a mistake in the `post` service.
``shell
kubectl logs reddit-post-5df6798d67-mwz95 -n reddit-ns
```
``log
{"addr."] "10.4.0.15," "event." "request", "level": "info", "method": "GET", "path": "/posts?", "request_id." "e9b4b8e1-d1dc-4210-a56f-708b9ff4718b", "response_status": 500, "service." "post", "timestamp": "2020-01-09 17:00:58"}
{"event."] "find_all_posts," "level." "info", "message": "Successfully retrieved all posts from the database", "params": {}, "request_id." "c9af9652-cf53-486a-937d-94e1e3532dea", "service": "post", "timestamp": "2020-01-09 17:00:58"}
{"event."] "internal_error," "level." "error", "method": {"event": "GET", "path": "/posts?", "remote_addr." "10.4.1.5", "request_id": "c9af9652-cf53-486a-937d-94e1e3532dea", "service": "post", "timestamp": "2020-01-09 17:00:58", "traceback": "Traceback (most recent call last):\n File \"/usr/local/lib/python3.6/site-packages/flask/app.py\", line 1612, in full_dispatch_request\n rv = self.dispatch_request()\n File \"/usr/local/lib/python3.6/site-packages/flask/app. py\", line 1598, in dispatch_request\n return self.view_functions[rule.endpoint](**req.view_args)\n File \"/app/post_app.py\", line 133, in posts\n posts = find_posts()\n File \"/usr/local/lib/python3. 6/site-packages/py_zipkin.py\", line 246, in decorated\n return f(*args, **kwargs)\n File \"/app/post_app.py\", line 120, in findposts\n return dumps(posts)\n File \"/usr/local/lib/python3. 6/site-packages/bson/json_util.py\", line 403, in dumps\n return json.dumps(_json_convert(obj, json_options), *args, **kwargs)\n File \"/usr/local/lib/python3.6/site-packages/bson/json_util. py\", line 444, in _json_convert\n return list((_json_convert(v, json_options) for v in obj))\n File \"/usr/local/lib/python3. 6/site-packages/bson/json_util.py\", line 444, in <genexpr>\n return list((_json_convert(v, json_options) for v in obj))\n File \"/usr/local/lib/python3. 6/site-packages/pymongo/cursor.py\", line 1132, in next\n if len(self.__data) or self._refresh():\n File \"/usr/local/lib/python3.6/site-packages/pymongo/cursor. py\", line 1055, in _refresh\n self.__collation))\n File \"/usr/local/lib/python3.6/site-packages/pymongo/cursor.py\", line 947, in __send_message\n helpers._check_command_response(doc['data'][0])\n File \"/usr/local/lib/python3. 6/site-packages/pymongo/helpers.py\", line 210, in _check_command_response\n raise OperationFailure(msg % errmsg, code, response)\npymongo.OperationFailure: command find requires authentication\n"}.
```
In short, the point is.
``log
pymongo.OperationFailure command find requires authentication
```

Googling suggests the same idea as trying to think: https://stackoverflow.com/questions/57443291/pymongo-errors-operationfailure-command-insert-requires-authentication.

Specifically:
> MongoDB instance you are using is set up with authentication

Let's see what the monga has to tell us.
``shell
kubectl describe pod reddit-mongodb-6fd8c46f6b-w4gdr -n reddit-ns
```
``log
Name: reddit-mongodb-6fd8c46f6b-w4gdr
Namespace: reddit-ns
Priority: 0
Node: gke-reddit-public-main-pool-43115a71-cksq/10.3.0.3
Start Time: Thu, 09 Jan 2020 18:44:45 +0300
Labels: app=mongodb
                chart=mongodb-7.2.8
                pod-template-hash=6fd8c46f6b
                release=reddit
Annotations: cni.projectcalico.org/podIP: 10.4.0.16/32
Status:         Running
IP: 10.4.0.16
IPs:            <none>
Controlled By:  ReplicaSet/reddit-mongodb-6fd8c46f6b
Containers:
  reddit-mongodb:
    Container ID: docker://7433071b84dae22bb5d2d5c3e7d88940f5fef65e8ae8b798a85cb0286462f817
    Image: docker.io/bitnami/mongodb:4.0.12-debian-9-r22
    Image ID: docker-pullable://bitnami/mongodb@sha256:fca68e8a78207d8195e004ac09f34d7c23d406a609d2fbb0d4cc9c7855c6b5ec
    Port: 27017/TCP
    Host Port: 0/TCP
    State:          Running
      Started:      Thu, 09 Jan 2020 18:45:16 +0300
    Ready:          True
    Restart Count:  0
    Liveness: exec [mongo --eval db.adminCommand('ping')] delay=30s timeout=5s period=10s #success=1 #failure=6.
    Readiness: exec [mongo --eval db.adminCommand('ping')] delay=5s timeout=5s period=10s #success=1 #failure=6.
    Environment:
      MONGODB_ROOT_PASSWORD: <set to the key 'mongodb-root-password' in secret 'reddit-mongodb'> Optional: false
      MONGODB_SYSTEM_LOG_VERBOSITY: 0
      MONGODB_DISABLE_SYSTEM_LOG: no
      MONGODB_ENABLE_IPV6: no
      MONGODB_ENABLE_DIRECTORY_PER_DB: no
    Mounts:
      /bitnami/mongodb from data (rw)
      /var/run/secrets/kubernetes.io/serviceaccount from default-token-vqclp (ro)
Conditions:
  Type Status
  Initialized True 
  Ready True 
  ContainersReady True 
  PodScheduled True 
Volumes:
  data:
    Type:       PersistentVolumeClaim (a reference to a PersistentVolumeClaim in the same namespace)
    ClaimName: reddit-mongodb
    ReadOnly: false
  default-token-vqclp:
    Type:        Secret (a volume populated by a Secret)
    SecretName: default-token-vqclp
    Optional: false
QoS Class:       BestEffort
Node-Selectors:  <none>
Tolerations: node.kubernetes.io/not-ready:NoExecute for 300s
                 node.kubernetes.io/unreachable:NoExecute for 300s
Events:          <none>
```
Password asks to be set.

Description of the chart https://github.com/helm/charts/tree/master/stable/mongodb.

For the purposes of this installation, let's try to disable authorization first.

`kubernetes/Charts/reddit/values.yaml`.
``Yaml
---
comment:
  image:
    repository: vscoder/comment
    tag: latest
  service:
    externalPort: 9292

Post:
  image:
    repository: vscoder/post
    tag: latest
  service:
    externalPort: 5000

ui:
  image:
    repository: vscoder/ui
    tag: latest
  service:
    externalPort: 9292

mongodb:
  usePassword: false # This parameter was added by us
```

``shell
helm dependency build reddit/
```
``log
Hang tight while we grab the latest from your chart repositories.
...Unable to get an update from the "local" chart repository (http://127.0.0.1:8879/charts):
        Get http://127.0.0.1:8879/charts/index.yaml: dial tcp 127.0.0.1:8879: connect: connection refused
...Successfully got an update from the "stable" chart repository...
Update Complete.
Saving 4 charts
Downloading mongodb from repo https://kubernetes-charts.storage.googleapis.com
Deleting outdated charts
```
``shell
helm tiller run -- helm upgrade --install --wait --namespace=reddit-ns reddit reddit/
```
``log
Installed Helm version v2.16.1
Installed Tiller version v2.16.1
Helm and Tiller are the same version!
Starting Tiller...
Tiller namespace: kube-system
Running: helm upgrade --install --wait --namespace=reddit-ns reddit reddit/

Release "reddit" has been upgraded.
LAST DEPLOYED: Thu Jan 9 22:15:12 2020
NAMESPACE: reddit-ns
STATUS: DEPLOYED

RESOURCES:
==> v1/Deployment
NAME AGE
3h30m
3h30m reddit-post
reddit-ui 3h30m

==> v1/PersistentVolumeClaim
NAME AGE
reddit-mongodb 3h30m

==> v1/Pod(related)
NAME AGE
reddit-comment-5c9999f4d4-vfq9m 3h30m
reddit-mongodb-68fd4989f7-r58lm 8s
reddit-post-5df6798d67-mwz95 3h30m
reddit-ui-9b5b66dc4-6jc8j 3h30m
reddit-ui-9b5b66dc4-6mqbn 3h30m
reddit-ui-9b5b66dc4-slv8p 3h30m

==> v1/Service
NAME AGE
3h30m
reddit-mongodb 3h30m
3h30m reddit-post
reddit-ui 3h30m

==> v1beta1/Deployment
NAME AGE
reddit-mongodb 3h30m

==> v1beta1/Ingress
NAME AGE
reddit-ui 3h30m


Stopping Tiller...
```
Restarted our mongodb. Let's take a look at him.
``shell
kubectl describe pod reddit-mongodb-68fd4989f7-r58lm -n reddit-ns
```
``log
Name: reddit-mongodb-68fd4989f7-r58lm
Namespace: reddit-ns
Priority: 0
Node: gke-reddit-public-main-pool-43115a71-xgm5/10.3.0.4
Start Time: Thu, 09 Jan 2020 22:15:16 +0300
Labels: app=mongodb
                chart=mongodb-7.2.8
                pod-template-hash=68fd4989f7
                release=reddit
Annotations: cni.projectcalico.org/podIP: 10.4.1.7/32
Status:         Running
IP: 10.4.1.7
IPs:            <none>
Controlled By:  ReplicaSet/reddit-mongodb-68fd4989f7
Containers:
  reddit-mongodb:
    Container ID: docker://e4ebe7055d7715b129229dd43359f0565fff8314b913171c0dadb1ef59983a07
    Image: docker.io/bitnami/mongodb:4.0.12-debian-9-r22
    Image ID: docker-pullable://bitnami/mongodb@sha256:fca68e8a78207d8195e004ac09f34d7c23d406a609d2fbb0d4cc9c7855c6b5ec
    Port: 27017/TCP
    Host Port: 0/TCP
    State:          Running
      Started:      Thu, 09 Jan 2020 22:16:15 +0300
    Ready:          True
    Restart Count:  0
    Liveness: exec [mongo --eval db.adminCommand('ping')] delay=30s timeout=5s period=10s #success=1 #failure=6.
    Readiness: exec [mongo --eval db.adminCommand('ping')] delay=5s timeout=5s period=10s #success=1 #failure=6.
    Environment:
      MONGODB_SYSTEM_LOG_VERBOSITY: 0
      MONGODB_DISABLE_SYSTEM_LOG: no
      MONGODB_ENABLE_IPV6: no
      MONGODB_ENABLE_DIRECTORY_PER_DB: no
    Mounts:
      /bitnami/mongodb from data (rw)
      /var/run/secrets/kubernetes.io/serviceaccount from default-token-vqclp (ro)
Conditions:
  Type Status
  Initialized True 
  Ready False 
  ContainersReady True 
  PodScheduled True 
Volumes:
  data:
    Type:       PersistentVolumeClaim (a reference to a PersistentVolumeClaim in the same namespace)
    ClaimName: reddit-mongodb
    ReadOnly: false
  default-token-vqclp:
    Type:        Secret (a volume populated by a Secret)
    SecretName: default-token-vqclp
    Optional: false
QoS Class:       BestEffort
Node-Selectors:  <none>
Tolerations: node.kubernetes.io/not-ready:NoExecute for 300s
                 node.kubernetes.io/unreachable:NoExecute for 300s
Events:
  Type Reason Age From Message
  ---- ------ ---- ---- -------
  Normal Scheduled 4m43s default-scheduler Successfully assigned reddit-ns/reddit-mongodb-68fd4989f7-r58lm to gke-reddit-public-main-pool-43115a71-xgm5
  Warning FailedAttachVolume 4m43s attachdetach-controller Multi-Attach error for volume "pvc-2d9d568d-1a82-4a65-b179-253570318b19" Volume is already used by pod(s) reddit-mongodb-6fd8c46f6b-w4gdr
  Normal SuccessfulAttachVolume 4m22s attachdetach-controller AttachVolume.Attach succeeded for volume "pvc-2d9d568d-1a82-4a65-b179-253570318b19".
  Normal Pulling 4m7s kubelet, gke-reddit-public-main-pool-43115a71-xgm5 Pulling image "docker.io/bitnami/mongodb:4.0.12-debian-9-r22".
  Normal Pulled 3m45s kubelet, gke-reddit-public-main-pool-43115a71-xgm5 Successfully pulled image "docker.io/bitnami/mongodb:4.0.12-debian-9-r22".
  Normal Created 3m45s kubelet, gke-reddit-public-main-pool-43115a71-xgm5 Created container reddit-mongodb
  Normal Started 3m44s kubelet, gke-reddit-public-main-pool-43115a71-xgm5 Started container reddit-mongodb
  Warning Unhealthy 3m35s kubelet, gke-reddit-public-main-pool-43115a71-xgm5 Readiness probe failed: MongoDB shell version v4.0.12
connecting to: mongodb://127.0.0.1:27017/?gssapiServiceName=mongodb
2020-01-09T19:16:24.149+0000 E QUERY [js] Error: couldn't connect to server 127.0.0.1:27017, connection attempt failed: SocketException: Error connection to server 127.0.0.1:27017 :: caused by :: Connection refused :
connect@src/mongo/shell/mongo.js:344:17
@(connect):2:6
exception: connect failed
```
The environment variable `MONGODB_ROOT_PASSWORD` will remain, from which we can conclude that the configuration changes have successfully worked. But you can see the error in the events... Supposedly it is related to the fact that the content of the monga will was created when using a password.

Let's remove the will in order to recreate
``shell
kubectl delete persistentvolumes pvc-2d9d568d-1a82-4a65-b179-253570318b19
```
``log
"pvc-2d9d568d-1a82-4a65-b179-253570318b19" deleted
# And then everything hung on...
```

For the purity of the experiment, I'll re-create the release

First we remove the old one.
``shell
helm tiller run -- helm delete --purge reddit
```
``log
Installed Helm version v2.16.1
Installed Tiller version v2.16.1
Helm and Tiller are the same version!
Starting Tiller...
Tiller namespace: kube-system
Running: helm delete reddit

release "reddit" deleted
Stopping Tiller...
```

Let's try to create anew
``shell
helm tiller run -- helm upgrade --install --wait --namespace=reddit-ns reddit reddit/
```
``log
Installed Helm version v2.16.1
Installed Tiller version v2.16.1
Helm and Tiller are the same version!
Starting Tiller...
Tiller namespace: kube-system
Running: helm upgrade --install --wait --namespace=reddit-ns reddit reddit/

UPGRADE FAILED
Error: "reddit" has no deployed releases
Error: UPGRADE FAILED: "reddit" has no deployed releases
Stopping Tiller...
Error: plugin "tiller" exited with error
```

Googleogle, find https://github.com/helm/helm/issues/3208#issuecomment-348238689.
``shell
helm tiller run -- helm list --all                                                   
```
``log
Installed Helm version v2.16.1
Installed Tiller version v2.16.1
Helm and Tiller are the same version!
Starting Tiller...
Tiller namespace: kube-system
Running: helm list --all

NAME REVISION UPDATED STATUS CHART APP VERSION NAMESPACE
reddit 5 Thu Jan 9 22:15:12 2020 DELETED reddit-0.1.0 reddit-ns
Stopping Tiller...
```
Turns out we haven't quite removed the release.

Delete release at all https://github.com/helm/helm/issues/3208#issuecomment-352241117.
``shell
helm tiller run -- helm delete --purge reddit
```
``log
Installed Helm version v2.16.1
Installed Tiller version v2.16.1
Helm and Tiller are the same version!
Starting Tiller...
Tiller namespace: kube-system
Running: helm delete --purge reddit

release "reddit" deleted
Stopping Tiller...
```

And let's create anew.
``shell
helm tiller run -- helm upgrade --install --wait --namespace=reddit-ns reddit reddit/
```
``log
Installed Helm version v2.16.1
Installed Tiller version v2.16.1
Helm and Tiller are the same version!
Starting Tiller...
Tiller namespace: kube-system
Running: helm upgrade --install --wait --namespace=reddit-ns reddit reddit/

Release "reddit" does not exist. Installing it now.
NAME: reddit
LAST DEPLOYED: Thu Jan 9 22:41:36 2020
NAMESPACE: reddit-ns
STATUS: DEPLOYED

RESOURCES:
==> v1/Deployment
NAME AGE
reddit-comment 23s
reddit-post 23s
reddit-ui 23s

==> v1/PersistentVolumeClaim
NAME AGE
reddit-mongodb 24s

==> v1/Pod(related)
NAME AGE
reddit-comment-5c9999f4d4-x2ctx 23s
reddit-mongodb-68fd4989f7-qcsxj 23s
reddit-post-5df6798d67-sxf2s 23s
reddit-ui-9b5b66dc4-dhlms 23s
reddit-ui-9b5b66dc4-lq5mt 23s
reddit-ui-9b5b66dc4-rz9hk 23s

==> v1/Service
NAME AGE
reddit-comment 24s
reddit-mongodb 23s
reddit-post 24s
reddit-ui 23s

==> v1beta1/Deployment
NAME AGE
reddit-mongodb 23s

==> v1beta1/Ingress
NAME AGE
reddit-ui 23s


Stopping Tiller...
```
It's a success now.

Let's wait for ingress configuration and check the result http://35.244.235.133/.

Yes! Now it's fucking working!!!

**TODO**: Implement authorization in MongoDB ** using secret**.


#### Helm3

Let's try the new major version of helm in battle:

1. Let's try the new major version of helm in battle:
2. Put the downloaded helm binary in the binary directory (`~/bin`) under the name helm3.
   ``shell
   make install_helm 
   wget https://get.helm.sh/helm-v3.0.2-linux-amd64.tar.gz -O /tmp/helm-3.0.2.tar.gz
   --2020-01-10 23:42:48-- https://get.helm.sh/helm-v3.0.2-linux-amd64.tar.gz.
   Recognized by get.helm.sh (get.helm.sh)... 152.199.21.175, 2606:2800:233:1cb7:261b:1f9c:2074:3c
   Connecting to get.helm.sh (get.helm.sh) |152.199.21.175|:443... connection established.
   The HTTP request has been sent. Waiting for reply... 200 OK
   Length: 12101232 (12M) [application/x-tar]
   Keeping in: "/tmp/helm-3.0.2.tar.gz"

   /tmp/helm-3.0.2.tar. 100%[===============>] 11,54M 9,23MB/s for 1,3s    

   2020-01-10 23:42:51 (9.23 MB/s) - "/tmp/helm-3.0.2.tar.gz" saved [12101232/12101232].

   cd /tmp/ && tar vxzf /tmp/helm-3.0.2.tar.gz
   linux-amd64/
   linux-amd64/README.md
   linux-amd64/LICENSE
   linux-amd64/helm
   mv /tmp/linux-amd64/helm ~/bin/helm-3.0.2
   chmod +x ~/bin/helm-3.0.2
   ln -sf helm-3.0.2 ~/bin/helm
   ~/bin/helm version && rm -rf /tmp/helm-3.0.2.tar.gz /tmp/linux-amd64
   version.BuildInfo{Version: "v3.0.2", GitCommit: "19e47ee3283ae98139d98460de796c1be1e3975f", GitTreeState: "clean", GoVersion: "go1.13.5" }. 
   ```
3. Let's create a new namespace `new-helm`:
   ``hell``
   cd ./kubernetes && make configure_kubectl
   kubectl create ns new-helm
   ```
   ``log
   namespace/new-helm created
   ```
4. Let's warm up:
   ``shell
   ./kubernetes/Charts
   helm3 dep update ./reddit
   helm3 upgrade --install --namespace=new-helm --wait reddit-release reddit/
   ```
   ``log
   Release "reddit-release" does not exist. Installing it now.
   NAME: reddit-release
   LAST DEPLOYED: Fri Jan 10 23:56:01 2020
   NAMESPACE: new-helm
   STATUS: deployed
   REVISION: 1
   TEST SUITE: None
   ```
5. Check: `kubectl get ingress -not new-helm`.
   http://34.107.225.231

** Everything works! **

> In order to continue the execution of the RS it is necessary to return _clusterAdmin tiller_ entity to our cluster. On the other hand, further use of `helm3` / `helm2 tiller plugin is not prohibited :)

We will use `helm3` ^_^... But this is not accurate))))


### GitLab + Kubernetes

#### Let's install GitLab

Let's add a new node-pool for gitlab.

`Kubernetes/terraform/main.tf`
``conf
# ---------------------------------------------------------------------------------------------------------------------
# CREATE A NODE POOL FOR GITLAB
# ---------------------------------------------------------------------------------------------------------------------

resource "google_container_node_pool" "gitlab_node_pool" {
  provider = google-beta

  name = "gitlab-pool"
  project = var.project
  location = var.location
  cluster = module.gke_cluster.name

  initial_node_count = "1"

  // autoscaling {
  // min_node_count = "1"
  // max_node_count = "1"
  // }

  management {
    auto_repair = "true"
    auto_upgrade = "true"
  }

  node_config {
    image_type = "COS"
    machine_type = "n1-standard-2"

    labels = {
      app = "gitlab"
    }

    # Add a public tag to the instances. See the network access tier table for full details:
    # https://github.com/gruntwork-io/terraform-google-network/tree/master/modules/vpc-network#access-tier
    tags = [
      module.vpc_network.public,
      "public-pool-example."
    ]

    disk_size_gb = "30"
    disk_type = "pd-standard"
    preemptible = false

    service_account = module.gke_service_account.email

    oauth_scopes = [
      "https://www.googleapis.com/auth/cloud-platform."
    ]
  }

  lifecycle {
    ignore_changes = [initial_node_count]
  }

  timeouts {
    create = "30m"
    update = "30m"
    delete = "30m"
  }
}
```

With the help of node pools, new machines of different capacities and configurations can be added to the cluster.

P.S. Wait until the cluster is ready for operation

The RS says to disable RBAC and enable obsolete access rights. 

But when creating the cluster, we have already found out that in the current version we could not find an option to enable obsolete access rights.

Let's try not to disable RBAC in the same way. ^_^

We will also install Gitlab using Helm Chart from Omnibus package. Just in case, the official instruction is https://source.isimplelab.com/help/install/kubernetes/gitlab_omnibus.md.

1. Let's add Gitlab repository.
``shell
helm repo add gitlab https://charts.gitlab.io
```
``log
"gitlab" has been added to your repositories
```

2. We will change the Gitlab configuration, so we will download the Chart (the latest version, not the one specified in the RS).
``shell
helm fetch gitlab/gitlab-omnibus --untar
cd gitlab-omnibus
```

3. Fix `gitlab-omnibus/values.yaml'.
``Yaml
baseDomain: your-domain.com
legoEmail: you@example.com
```

4. Add to `gitlab-omnibus/templates/gitlab/gitlab-svc.yaml`.
``Yaml
...
    - name: web
      port: 80
      targetPort: workhorse
...
```
Get .
``Yaml
apiVersion: v1
kind: Service
metadata:
  name: {{{ template "fullname"}. }}
  The labels:
    app: {{{"pos(192,210)}the template "fullname. }}
    chart: "{{{ .Chart.Name }}-{{ .Chart.Version }}."
    release: "{{{ .Release.Name }}"
    "{{{ .Release.Service }}."
spec:
  selector:
    name: {{{ template "fullname"} . }}
  ports:
    - name: ssh
      port: 22
      targetPort: ssh
    - name: mattermost
      port: 8065
      targetPort: mattermost
    - name: registry
      port: 8105
      targetPort: registry
    - name: workhorse
      port: 8005
      targetPort: workhorse
    - name: prometheus
      port: 9090
      targetPort: prometheus
    - name: web
      port: 80
      targetPort: workhorse
    {{- if and .Values.pagesExternalScheme .Values.pagesExternalDomain}}
    - name: pages
      port: 8090
      targetPort: pages
    {- end }
```

5. Fix in `gitlab-omnibus/templates/gitlab-config.yaml'.
``Yaml
...
data:
  external_scheme: http
  external_hostname: {{{ template "fullname"} . }}
...
```

6. Fix in `gitlab-omnibus/templates/ingress/gitlab-ingress.yaml'.
``Yaml
...
  rules:
  - host: {{{ template "fullname"} . }}
...
---
```
Get .
``Yaml
apiVersion: extensions/v1beta1
kind: Ingress
metadata:
  name: {{{ template "fullname"}. }}
  The labels:
    app: {{{"pos(192,210)}the template "fullname. }}
    chart: "{{{ .Chart.Name }}-{{ .Chart.Version }}."
    release: "{{{ .Release.Name }}"
    "{{{ .Release.Service }}."
  annotations:
    kubernetes.io/tls-acme: "true"
    kubernetes.io/ingress.class: "nginx"
spec:
  tls:
  - hosts:
    - gitlab.{{ .Values.baseDomain }}.
    - registry.{{ .Values.baseDomain }}
    - mattermost. {{{ .Values.baseDomain }}
    - prometheus.{{{ .Values.baseDomain }}
    secretName: gitlab-tls
  Rules:
  - host: {{{ template "full name"}. }}
    http:
      Http:
      - path: /
        backend:
          serviceName: {{{"pos(192,210)}the template "fullname". }}
          servicePort: 8005
  - host: registry.{{{ .Values.baseDomain }}.
    http:
      Http:
      - path: /
        backend:
          serviceName: {{{"pos(192,210)}the template "fullname". }}
          servicePort: 8105
  - host: mattermost. {{{ .Values.baseDomain }}
    http:
      Http:
      - path: /
        backend:
          serviceName: {{{"pos(192,210)}the template "fullname". }}
          servicePort: 8065
  - host: prometheus.{{ .Values.baseDomain }}.
    http:
      Http:
      - path: /
        backend:
          serviceName: {{{"pos(192,210)}the template "fullname". }}
          servicePort: 9090
---
```

Let's run a depression (remind me, we have helm3)
``shell
helm install -f values.yaml gitlab.
```
``log
WARNING: This chart is deprecated
Error: unable to build kubernet objects from release manifest: error validating "": error validating data: [unknown object type "nil" in ConfigMap.data.pages_external_domain, unknown object type "nil" in ConfigMap.data.pages_external_scheme].
```

Let's add it to `gitlab-omnibus/values.yaml'.
``Yaml
...
pagesExternalScheme: http
pagesExternalDomain: your-pages-domain.com
...
```
``log
WARNING: This chart is deprecated
NAME: gitlab
LAST DEPLOYED: Sat Jan 11 18:12:13 2020
NAMESPACE: default
STATUS: deployed
REVISION: 1
TEST SUITE: None
NOTES:
It may take several minutes for GitLab to reconfigure.
    You can watch the status by running `kubectl get deployment -w gitlab-gitlab --namespace default
  You did not specify a baseIP so one will be assigned for you.
  It may take a few minutes for the LoadBalancer IP to be available.
  Watch the status with: 'kubectl get svc -w --namespace nginx-ingress nginx', then:

  export SERVICE_IP=$(kubectl get svc --namespace nginx-ingress nginx -o jsonpath='{.status.loadBalancer.ingress[0].ip}').

  Then make sure to configure DNS with something like:
    *.your-domain.com 300 IN A $SERVICE_IP
```
Deploy started

It's a problem:
``shell
kubectl get pods
```
``log
NAME READY STATUS RESTARTS AGE
gitlab-gitlab-766445f7d7-m4flm 0/1 Running 0 4m40s
gitlab-gitlab-postgresql-66d5b899b8-tzggp 0/1 Pending 0 4m40s
gitlab-gitlab-redis-6c675dd568-cp4xn 1/1 Running 0 4m40s
gitlab-gitlab-runner-875586966-lbc6h 0/1 CrashLoopBackOff 4 4m39s
```
``shell
kubectl describe pod gitlab-gitlab-postgresql-66d5b899b8-tzggp
```
``log
Name: gitlab-gitlab-postgresql-66d5b899b8-tzggp
Namespace: default
Priority: 0
Node:           <none>
Labels: app=gitlab-gitlab
                name=gitlab-gitlab-postgresql
                pod-template-hash=66d5b899b8
Annotations: kubernetes.io/limit-ranger: LimitRanger plugin set: cpu request for container postgresql
Status:         Pending
IP:             
IPs:            <none>
Controlled By:  ReplicaSet/gitlab-gitlab-postgresql-66d5b899b8
Containers:
  postgresql:
    Image: postgres:9.6.5
    Port: 5432/TCP
    Host Port: 0/TCP
    Requests:
      cpu: 100m
    Liveness: exec [pg_isready -h localhost -U postgres] delay=30s timeout=5s period=10s #success=1 #failure=3.
    Readiness: exec [pg_isready -h localhost -U postgres] delay=5s timeout=1s period=10s #success=1 #failure=3.
    Environment:
      POSTGRES_USER: <set to the key 'postgres_user' of config map 'gitlab-gitlab-config'> Optional: false
      POSTGRES_PASSWORD: <set to the key 'postgres_password' in secret 'gitlab-gitlab-secrets'> Optional: false
      POSTGRES_DB: <set to the key 'postgres_db' of config map 'gitlab-gitlab-config'> Optional: false
      DB_EXTENSION: pg_trgm
      PGDATA:             /var/lib/postgresql/data/pgdata
    Mounts:
      /docker-entrypoint-initdb.d from initdb (ro)
      /var/lib/postgresql/data from data (rw,path="postgres")
      /var/run/secrets/kubernetes.io/serviceaccount from default-token-5lcj8 (ro)
Conditions:
  Type Status
  PodScheduled False 
Volumes:
  data:
    Type:       PersistentVolumeClaim (a reference to a PersistentVolumeClaim in the same namespace)
    ClaimName: gitlab-gitlab-postgresql-storage
    ReadOnly: false
  initdb:
    Type:      ConfigMap (a volume populated by a ConfigMap)
    Name: gitlab-gitlab-postgresql-initdb
    Optional: false
  default-token-5lcj8:
    Type:        Secret (a volume populated by a Secret)
    SecretName: default-token-5lcj8
    Optional: false
QoS Class:       Burstable
Node-Selectors:  <none>
Tolerations: node.kubernetes.io/not-ready:NoExecute for 300s
                 node.kubernetes.io/unreachable:NoExecute for 300s
Events:
  Type Reason Age From Message
  ---- ------ ---- ---- -------
  Warning FailedScheduling 22s (x9 over 5m23s) Default-scheduler pod has unbound immediate PersistentVolumeClaims (repeated 3 times)
```

Let's move on, see `PersistentVolumeClaims`.
``shell
kubectl get persistentvolumeclaims 
```
``log
NAME STATUS VOLUME CAPACITY ACCESS MODES STORAGECLASS AGE
gitlab-gitlab-config-storage Bound pvc-e3284073-2016-4095-b79c-5b2585dd990a 1Gi RWO gitlab-gitlab-fast 20m
gitlab-gitlab-postgresql-storage Pending gitlab-gitlab-fast 20m
gitlab-gitlab-redis-storage Bound pvc-dbb0d126-ce15-42d5-9331-520a4301d54e 5Gi RWO gitlab-gitlab-fast 20m
gitlab-gitlab-registry-storage Bound pvc-2bec254a-e45b-4d3e-9ed1-cdf5b4b45c12 30Gi RWO gitlab-gitlab-fast 20m
gitlab-gitlab-storage Bound pvc-3b8b3abd-442b-4d8f-aed4-0caac0445de1 30Gi RWO gitlab-gitlab-fast 20m
```
``log
kubectl describe persistentvolumeclaims gitlab-gitlab-postgresql-storage
Name: gitlab-gitlab-postgresql-storage
Namespace: default
StorageClass: gitlab-gitlab-fast
Status:        Pending
Volume:        
Labels: app=gitlab-gitlab
               chart=gitlab-omnibus-0.1.37
               heritage=Helm
               release=gitlab
Annotations: volume.beta.kubernetes.io/storage-class: gitlab-gitlab-fast
               volume.beta.kubernetes.io/storage-provisioner: kubernetes.io/gce-pd
Finalizers:    [kubernetes.io/pvc-protection]
Capacity:      
Access Modes:  
VolumeMode:    Filesystem
Mounted By: gitlab-gitlab-postgresql-66d5b899b8-tzggp
Events:
  Type Reason Age From Message
  ---- ------ ---- ---- -------
  Warning ProvisioningFailed 21s (x17 over 21m) persistentvolume controller Failed to provision volume with StorageClass "gitlab-gitlab-fast": googleapi: Error 403: QUOTA_EXCEEDED - Quota 'SSD_TOTAL_GB' exceeded.  Limit: 100.0 in region us-central1.
```

All right, `Failed to provide volume with StorageClass 'gitlab-gitlab-fast': googleapi: Error 403: QUOTA_EXCEEDED - Quota 'SSD_TOTAL_GB' exceeded.  Limit: 100.0 in region us-central1.`.

Let's see the available classes
``shell
kubectl get storageclasses
```
``log
NAME PROVISIONER AGE
gitlab-gitlab-fast kubernetes.io/gce-pd 24m
standard (default) kubernetes.io/gce-pd 19h
```

There are two solutions:
1. use _storageclas_ `standard`.
2. Reduce the space requirement to fit in 100GB

Let's choose the 2nd way: we don't need much space for our task)).

`gitlab-omnibus/values.yaml`
``Yaml
...
redisStorageSize: 5Gi # default 5Gb
postgresStorageSize: 10Gi # default 30Gb
gitlabDataStorageSize: 10Gi # default 30Gb
gitlabRegistryStorageSize: 10Gi # default 30Gb
gitlabConfigStorageSize: 1Gi # default 1Gb
...
```

Let's try to apply
``shell
helm upgrade -f values.yaml gitlab.
```
``log
WARNING: This chart is deprecated
Error: UPGRADE FAILED: cannot patch "gitlab-gitlab-storage" with kind PersistentVolumeClaim: PersistentVolumeClaim "gitlab-gitlab-storage" is invalid: spec.resources.requests.storage: Forbidden: field can not be less than previous value && cannot patch "gitlab-gitlab-registry-storage" with kind PersistentVolumeClaim: PersistentVolumeClaim "gitlab-gitlab-registry-storage" is invalid: spec.resources.requests.storage: Forbidden: field can not be less than previous value && cannot patch "gitlab-gitlab-postgresql-storage" with kind PersistentVolumeClaim: PersistentVolumeClaim "gitlab-gitlab-postgresql-storage" is invalid: [spec: Forbidden: is immutable after creation except resources.requests for bound claims, spec.resources.requests.storage: Forbidden: field can not be less than previous value]
```

Logically, you can't reduce the space already requested.

Then we'll be completely reassigned.
``shell
helm uninstall gitlab
```
``log
release "gitlab" uninstalled
```
``shell
helm list --all       
```
``log
NAME NAMESPACE REVISION UPDATED STATUS CHART APP VERSION
```
``shell
helm install -f values.yaml gitlab.
```
``log
WARNING: This chart is deprecated
NAME: gitlab
LAST DEPLOYED: Sat Jan 11 18:50:28 2020
NAMESPACE: default
STATUS: deployed
REVISION: 1
TEST SUITE: None
NOTES:
It may take several minutes for GitLab to reconfigure.
    You can watch the status by running `kubectl get deployment -w gitlab-gitlab --namespace default
  You did not specify a baseIP so one will be assigned for you.
  It may take a few minutes for the LoadBalancer IP to be available.
  Watch the status with: 'kubectl get svc -w --namespace nginx-ingress nginx', then:

  export SERVICE_IP=$(kubectl get svc --namespace nginx-ingress nginx -o jsonpath='{.status.loadBalancer.ingress[0].ip}').

  Then make sure to configure DNS with something like:
    *.your-domain.com 300 IN A $SERVICE_IP
```

Check out .
``shell
kubectl get pods
```
``log
NAME READY STATUS RESTARTS AGE
gitlab-gitlab-766445f7d7-nfts2 1/1 Running 0 23m
gitlab-gitlab-postgresql-66d5b899b8-95kph 1/1 Running 0 23m
gitlab-gitlab-redis-6c675dd568-9xbpw 1/1 Running 0 23m
gitlab-gitlab-runner-875586966-q8frz 1/1 Running 4 23m
```

It should be a few minutes. Find the issued ingress IP address of the nginx controller.

``shell
kubectl get service -n nginx-ingress nginx
```
``log
NAME TYPE CLUSTER-IP EXTERNAL-IP PORT(S) AGE
nginx LoadBalancer 10.4.15.19 35.223.233.250 80:31807/TCP,443:30526/TCP,22:32686/TCP 28m
```

Put the record in the local file `/etc/hosts` (put your IP address)
``shell
echo "35.223.233.250 gitlab-gitlab staging production" | sudo tee /etc/hosts
```

We try to enter: `Failed to connect to gitlab-gitlab port 80: In connection it is refused ` Firewall?

``shell
kubectl get pods -n nginx-ingress
```
``log
NAME READY STATUS RESTARTS AGE
default-http-backend-65b964d8cc-npbcq 1/1 Running 0 89m
nginx-lvkst 0/1 CrashLoopBackOff 22 89m
```
``shell
kubectl logs nginx-lvkst -n nginx-ingress
```
``log
[dumb-init] Unable to detach from controlling tty (errno=25 Inappropriate ioctl for device).
[dumb-init] Child spawned with PID 6.
[dumb-init] Unable to attach to controlling tty (errno=25 Inappropriate ioctl for device).
[dumb-init] setsid complete.
I0111 17:18:11.723933 6 launch.go:105] &{NGINX 0.9.0-beta.11 git-a3131c5 https://github.com/kubernetes/ingress}.
I0111 17:18:11.723968 6 launch. go:108] Watching for ingress class: nginx
I0111 17:18:11.724233 6 launch. go:262] Creating API server client for https://10.4.0.1:443.
I0111 17:18:11.729500 6 nginx.go:182] starting NGINX process...
F0111 17:18:11.775095 6 launch.go:122] no service with name nginx-ingress/default-http-backend found: services "default-http-backend" is forbidden: User "system:serviceaccount:nginx-ingress:default" cannot get resource "services" in API group "" in the namespace "nginx-ingress".
[dumb-init] Received signal 17.
[dumb-init] A child with PID 6 exited with exit status 255.
[dumb-init] Forwarded signal 15 to children.
[dumb-init] A child with PID 6 exited with exit status 255. Goodbye. [dumb-init]
```

That's a mistake.
``log
no service with name nginx-ingress/default-http-backend found: services "default-http-backend" is forbidden: User "system:serviceaccount:nginx-ingress:default" cannot get resource "services" in API group "" in the namespace "nginx-ingress".
```

Let's try to lock into a separate neurospace.

``shell
kubectl create namespace gitlab
```
``log
namespace/gitlab created
```
``shell
helm install --namespace gitlab -f values.yaml gitlab .
```
``log
WARNING: This chart is deprecated
NAME: gitlab
LAST DEPLOYED: Sat Jan 11 20:37:37 2020
NAMESPACE: gitlab
STATUS: deployed
REVISION: 1
TEST SUITE: None
NOTES:
It may take several minutes for GitLab to reconfigure.
    You can watch the status by running `kubectl get deployment -w gitlab-gitlab --namespace gitlab
  You did not specify a baseIP so one will be assigned for you.
  It may take a few minutes for the LoadBalancer IP to be available.
  Watch the status with: 'kubectl get svc -w --namespace nginx-ingress nginx', then:

  export SERVICE_IP=$(kubectl get svc --namespace nginx-ingress nginx -o jsonpath='{.status.loadBalancer.ingress[0].ip}').

  Then make sure to configure DNS with something like:
    *.your-domain.com 300 IN A $SERVICE_IP
```

Same mistake
``shell
kubectl logs nginx-p4m8s -n nginx-ingress
```
``log
[dumb-init] Unable to detach from controlling tty (errno=25 Inappropriate ioctl for device).
[dumb-init] Child spawned with PID 6.
[dumb-init] Unable to attach to controlling tty (errno=25 Inappropriate ioctl for device).
[dumb-init] setsid complete.
I0111 17:48:38.912239 6 launch.go:105] &{NGINX 0.9.0-beta.11 git-a3131c5 https://github.com/kubernetes/ingress}.
I0111 17:48:38.912274 6 launch. go:108] Watching for ingress class: nginx
I0111 17:48:38.912938 6 launch. go:262] Creating API server client for https://10.4.0.1:443.
I0111 17:48:38.916966 6 nginx.go:182] starting NGINX process...
F0111 17:48:38.970325 6 launch.go:122] no service with name nginx-ingress/default-http-backend found: services "default-http-backend" is kubectl logs nginx-p4m8s -n nginx-ing
ress
[dumb-init] Unable to detach from controlling tty (errno=25 Inappropriate ioctl for device).
[dumb-init] Child spawned with PID 6.
[dumb-init] Unable to attach to controlling tty (errno=25 Inappropriate ioctl for device).
[dumb-init] setsid complete.
I0111 17:48:38.912239 6 launch.go:105] &{NGINX 0.9.0-beta.11 git-a3131c5 https://github.com/kubernetes/ingress}.
I0111 17:48:38.912274 6 launch. go:108] Watching for ingress class: nginx
I0111 17:48:38.912938 6 launch. go:262] Creating API server client for https://10.4.0.1:443.
I0111 17:48:38.916966 6 nginx.go:182] starting NGINX process...
F0111 17:48:38.970325 6 launch.go:122] no service with name nginx-ingress/default-http-backend found: services "default-http-backend" is forbidden: User "system:serviceaccount:nginx-ingress:default" cannot get resource "services" in API group "" in the namespace "nginx-ingress".
[dumb-init] Received signal 17.
[dumb-init] A child with PID 6 exited with exit status 255.
[dumb-init] Forwarded signal 15 to children.
[dumb-init] A child with PID 6 exited with exit status 255. Goodbye. In API group "" in the namespace "nginx-ingress".
[dumb-init] Received signal 17.
[dumb-init] A child with PID 6 exited with exit status 255.
[dumb-init] Forwarded signal 15 to children.
[dumb-init] A child with PID 6 exited with exit status 255. Goodbye. [dumb-init]
```

Google says: https://stackoverflow.com/questions/50613717/deploy-gitlab-with-helm-nginx-ingress-pods-cant-start

One more thing: let's try to enable `Legacy Authorization`.

`Kubernetes/terraform/main.tf`
``conf
...
module "gke_cluster" {y:i}...
  ...
  enable_legacy_abac = "true"
}
...
```

A bug was found in the module `kubernetes/terraform/modules/gke-cluster`. In `kubernetes/terraform/modules/gke-cluster/variables.tf` there is a variable `enable_legacy_abac`, but it is not applied anywhere. Although its value should set `enable_legacy_abac` to `resource "google_container_cluster" "cluster" {` in `kubernetes/terraform/modules/gke-cluster/main.tf`.

Compiled by https://github.com/gruntwork-io/terraform-google-gke/issues/79.

Created by PR https://github.com/gruntwork-io/terraform-google-gke/pull/80.

Locally this bug has been fixed

`kubernetes/terraform/modules/gke-cluster/main.tf`
``conf
...
resource "google_container_cluster" "cluster" {
  ...
  enable_legacy_abac = var.enable_legacy_abac
}
```

Waiting for the Gitlab to come up.
``shell
kubectl get pods -n gitlab
```
``log
NAME READY STATUS RESTARTS AGE
gitlab-gitlab-766445f7d7-9ptqb 1/1 Running 0 11h
gitlab-gitlab-postgresql-66d5b899b8-67qbm 1/1 Running 0 11h
gitlab-gitlab-redis-6c675dd568-pb6xw 1/1 Running 0 11h
gitlab-gitlab-runner-644c574f56-48kvd 1/1 Running 4 11h
```

Receiving external ip
``shell
kubectl get service -n nginx-ingress nginx
```
``log
NAME TYPE CLUSTER-IP EXTERNAL-IP PORT(S) AGE
nginx LoadBalancer 10.4.8.171 35.223.5.28 80:32197/TCP,443:32626/TCP,22:31543/TCP 10h
```

Add `35.223.5.28 gitlab-gitlab staging production` to `/etc/hosts`.

Open http://gitlab-gitlab/.

We set our own password. Login under user root and the new password otusgitlab (actually there is no ^_^).


#### Let's start the project

Let's create a group `vscoder` http://gitlab-gitlab/vscoder.

In group settings, select CI/CD http://gitlab-gitlab/groups/vscoder/-/settings/ci_cd.

Add 2 variables:
- `CI_REGISTRY_USER` - login to dockerhub
- `CI_REGISTRY_PASSWORD` - password from Docker Hub

> These credentials will be used to build and release docker images using Gitlab CI

In the group we will create a new project `reddit-deploy` http://gitlab-gitlab/vscoder/reddit-deploy.

**Task:** Create 3 more projects: _post_, _ui_, _comment_ (make them public as well).

Public projects have been created
- `post` http://gitlab-gitlab/vscoder/post
- `comment` http://gitlab-gitlab/vscoder/comment
- `ui` http://gitlab-gitlab/vscoder/ui

Locally (outside the main repository) the `Gitlab_ci` directory was created with the following structure
``log
Gitlab_ci
├── comment
├─ post
├─ ─ reddit-deploy
└─ ui

4 directories, 0 files
```

##### ui

Transfer the source codes of the service `ui` to `Gitlab_ci/ui`.

The structure of the directory was
``log
Gitlab_ci/ui
├── build_info.txt
├─ config.ru
├── docker_build.sh
├── Dockerfile
├─ Gemfile
├── Gemfile.lock
├── helpers.rb
├── middleware.rb
├── ui_app.rb
├── VERSION
└─ views
    ├── create.haml
    ├── index.haml
    ├── layout.haml
    └── show.haml

1 directory, 14 files
```

Pour the service code `ui` into the corresponding project, the instructions are on the page of an empty project `ui` in `gitlab`.
In the directory `Gitlab_ci/`:
``shell
cd ./ui
git init
git remote add origin git@gitlab-gitlab:vscoder/ui.git
git add .
git commit -m "Initial commit"
git push -u origin master
```
``log
Initialised empty Git repository in /home/vscoder/projects/otus/devops-2019-08/Gitlab_ci/ui/.git/
[master (root commit) 049d01f] Initial commit
 14 files changed, 587 insertions(+)
 create mode 100644 Dockerfile
 create mode 100644 Gemfile
 create mode 100644 Gemfile.lock
 create mode 100644 VERSION
 create mode 100644 build_info.txt
 create mode 100644 config.ru
 create mode 100644 docker_build.sh
 create mode 100644 helpers.rb
 create mode 100644 middleware.rb
 create mode 100644 ui_app.rb
 create mode 100644 views/create.haml
 create mode 100644 views/index.haml
 create mode 100644 views/layout.haml
 create mode 100644 views/show.haml
Counting objects: 17, it's done.
Delta compression using up to 12 threads.
Compressing objects: 100% (15/15), done.
Recording objects: 100% (17/17), 7.28 KiB | 1.04 MiB/s, ready.
Total 17 (delta 1), reused 0 (delta 0).
To gitlab-gitlab:vscoder/ui.git
 * [new branch] master -> master
The "master" branch tracks the external "master" branch from "origin".
```

**Task:** For post and comment, do the same. Remember to specify the appropriate repository and group names.


##### comment

In the directory `Gitlab_ci/`:
``shell
cd ./comment
git init
git remote add origin git@gitlab-gitlab:vscoder/comment.git
git add .
git commit -m "Initial commit"
git push -u origin master
```
``log
Initialised empty Git repository in /home/vscoder/projects/otus/devops-2019-08/Gitlab_ci/comment/.git/
[master (root commit) 1fa7a7f] Initial commit
 9 files changed, 290 insertions(+)
 create mode 100644 Dockerfile
 create mode 100644 Gemfile
 create mode 100644 Gemfile.lock
 create mode 100644 VERSION
 create mode 100644 build_info.txt
 create mode 100644 comment_app.rb
 create mode 100644 config.ru
 create mode 100644 docker_build.sh
 create mode 100644 helpers.rb
Counting of objects: 11, done.
Delta compression using up to 12 threads.
Compressing objects: 100% (9/9), done.
Recording objects: 100% (11/11), 3.53 KiB | 1.18 MiB/s, ready.
Total 11 (delta 0), reused 0 (delta 0).
To gitlab-gitlab:vscoder/comment.git
 * [new branch] master -> master
The "master" branch tracks the external "master" branch from "origin".
```


#### post

In the directory `Gitlab_ci/`:
``shell
cd ./post
git init
git remote add origin git@gitlab-gitlab:vscoder/post.git
git add .
git commit -m "Initial commit"
git push -u origin master
```
``log
Initialised empty Git repository in /home/vscoder/projects/otus/devops-2019-08/Gitlab_ci/post/.git/
[master (root commit) 9be6e80] Initial commit
 7 files changed, 351 insertions(+)
 create mode 100644 Dockerfile
 create mode 100644 VERSION
 create mode 100644 build_info.txt
 create mode 100644 docker_build.sh
 create mode 100644 helpers.py
 create mode 100644 post_app.py
 create mode 100644 requirements.txt
Object count: 9, ready.
Delta compression using up to 12 threads.
Compressing objects: 100% (7/7), done.
Recording objects: 100% (9/9), 3.96 KiB | 1013.00 KiB/s, ready.
Total 9 (delta 0), reused 0 (delta 0).
To gitlab-gitlab:vscoder/post.git
 * [new branch] master -> master
The "master" branch tracks the external "master" branch from "origin".
```


##### reddit-deploy

1. Move the contents of `Charts` directory (folders ui, post, comment, reddit) to `Gitlab_ci/reddit-deploy`.
2. Run `reddit-deploy` to the gitlab project _reddit-deploy_.
``shell
cd reddit-deploy
git init
git remote add origin git@gitlab-gitlab:vscoder/reddit-deploy.git
git add .
git commit -m "Initial commit"
git push -u origin master
```
``log
Initialised empty Git repository in /home/vscoder/projects/otus/devops-2019-08/Gitlab_ci/reddit-deploy/.git/
[master (root commit) cbe8d36] Initial commit
 21 files changed, 323 insertions(+)
 create mode 100644 comment/Chart.yaml
 create mode 100644 comment/templates/_helpers.tpl
 create mode 100644 comment/templates/deployment.yaml
 create mode 100644 comment/templates/service.yaml
 create mode 100644 comment/values.yaml
 create mode 100644 post/Chart.yaml
 create mode 100644 post/templates/_helpers.tpl
 create mode 100644 post/templates/deployment.yaml
 create mode 100644 post/templates/service.yaml
 create mode 100644 post/values.yaml
 create mode 100644 reddit/.gitignore
 create mode 100644 reddit/Chart.yaml
 create mode 100644 reddit/requirements.lock
 create mode 100644 reddit/requirements.yaml
 create mode 100644 reddit/values.yaml
 create mode 100644 ui/Chart.yaml
 create mode 100644 ui/templates/_helpers.tpl
 create mode 100644 ui/templates/deployment.yaml
 create mode 100644 ui/templates/ingress.yaml
 create mode 100644 ui/templates/service.yaml
 create mode 100644 ui/values.yaml
Counting objects: 30, it's done.
Delta compression using up to 12 threads.
Compressing objects: 100% (29/29), done.
Recording objects: 100% (30/30), 3.83 KiB | 490.00 KiB/s, ready.
Total 30 (delta 6), reused 0 (delta 0).
To gitlab-gitlab:vscoder/reddit-deploy.git.
 * [new branch] master -> master
The "master" branch tracks the external "master" branch from "origin".
```
3. The structure should look like this (yes, it looks like this, I will not add it).


#### Let's set up the CI


##### ui

1. Create a file `gitlab_ci/ui/.gitlab-ci.yml` with the content
``Yaml
image: alpine:latest

Oh:
  - build
  - test
  - release
  - cleanup

build:
  stage: build
  image: docker:git
  Services:
    - docker:18.09.7-dind
  script:
    - setup_docker
    - build
  It's not:
    DOCKER_DRIVER: overlay2
  Only:
    -

Test:
  stage: test
  script:
    - exit 0
  Only:
    -

release:
  stage: release
  image: docker
  Services:
    - docker:dind
  script:
    - setup_docker
    - release
  Oh:
    DOCKER_TLS_CERTDIR: ""
  Only:
    - master

.auto_devops: &auto_devops |
  ["$TRACE" ] && set -x.
  export CI_REGISTRY="index.docker.io"
  export CI_APPLICATION_REPOSITORY=$CI_REGISTRY/$CI_PROJECT_PATH
  export CI_APPLICATION_TAG=$CI_COMMIT_REF_SLUG
  export CI_CONTAINER_NAME=ci_job_build_${CI_JOB_ID}
  export TILLER_NAMESPACE="kube-system"

  function setup_docker() {
    if ! docker info &>/dev/null; then
      if [ -z "$DOCKER_HOST" -a "$KUBERNETES_PORT" ]; then
        export DOCKER_HOST='tcp://localhost:2375'.
      fi
    fi
  }

  function release() {

    "Updating docker images..."

    if [[ -n "$CI_REGISTRY_USER" ]]; then
      "Logging to GitLab Container Registry with CI credentials..."
      docker login -u "$CI_REGISTRY_USER" -p "$CI_REGISTRY_PASSWORD"
      echo ""
    fi

    docker pull "$CI_APPLICATION_REPOSITORY:$CI_APPLICATION_TAG"
    docker tag "$CI_APPLICATION_REPOSITORY:$CI_APPLICATION_TAG" "$CI_APPLICATION_REPOSITORY:$(cat VERSION)".
    docker push "$CI_APPLICATION_REPOSITORY:$(cat VERSION)"
    echo ""
  }

  function build() {

    "Building Dockerfile-based application..."
    echo `git show --format="%h" HEAD | head -1` > build_info.txt
    echo `git rev-parse --abbrev-ref HEAD` >> build_info.txt.
    docker build -t "$CI_APPLICATION_REPOSITORY:$CI_APPLICATION_TAG" .

    if [[ -n "$CI_REGISTRY_USER" ]]; then
      "Logging to GitLab Container Registry with CI credentials..."
      docker login -u "$CI_REGISTRY_USER" -p "$CI_REGISTRY_PASSWORD"
      echo ""
    fi

    "Pushing to GitLab Container Registry..."
    docker push "$CI_APPLICATION_REPOSITORY:$CI_APPLICATION_TAG"
    echo ""
  }

before_script:
  - *auto_devops
```

2. Finish and run in gitlab
``shell
cd ./ui
git add .
git ci -m "Add .gitlab-ci.yml"
git push
```
``log
[master e270943] Add .gitlab-ci.yml
 1 file changed, 94 insertions(+)
 create mode 100644 .gitlab-ci.yml
Counting objects: 3, done.
Delta compression using up to 12 threads.
Compressing objects: 100% (3/3), done.
Recording objects: 100% (3/3), 1.07 KiB | 1.07 MiB/s, ready.
Total 3 (delta 1), reused 0 (delta 0).
To gitlab-gitlab:vscoder/ui.git
   049d01f...e270943 master -> master
```

3. Make sure that Pipeline is working
   After entering the correct password for `CI_REGISTRY_PASSWORD` the Pipeline was successfully :)

In the current configuration, CI performs
1. Build a docker-image assembly with the master tag
2. Test: Functional testing
3. Release: Changing tag from master to tag from VERSION file and fluffy docker-image with new tag

Job for each task runs in a separate Kubernetes POD.

The required operations are called in script blocks:
```yaml
script:
  - setup_docker
  - build
```

Description of the operations themselves is made in the form of bash-functions in the block `.auto_devops`.
``shell
.auto_devops: &auto_devops |
function setup_docker() {
  ...
}
function release() {
  ...
}
function build() {
  ...
}
```

For `Post` and `Comment` also add `.gitlab-ci.yml` to the repository and see that the image builds were successful.


#### comment

Copy the same ''gitlab-ci.yml'', then...
``shell
git add .
git ci -m "Add .gitlab-ci.yml"
git push
```
``log
[master 9961b94] Add .gitlab-ci.yml
 1 file changed, 94 insertions(+)
 create mode 100644 .gitlab-ci.yml
Counting objects: 3, done.
Delta compression using up to 12 threads.
Compressing objects: 100% (3/3), done.
Recording objects: 100% (3/3), 1.07 KiB | 1.07 MiB/s, ready.
Total 3 (delta 1), reused 0 (delta 0).
To gitlab-gitlab:vscoder/comment.git
   1fa7a7f...9961b94 master -> master
```

Pipeline is fully operational.


#### post

Copy the same ''gitlab-ci.yml'', then...
``shell
git add .
git ci -m "Add .gitlab-ci.yml"
git push
```
``log
[master e0c8f14] Add .gitlab-ci.yml
 1 file changed, 94 insertions(+)
 create mode 100644 .gitlab-ci.yml
Counting objects: 3, done.
Delta compression using up to 12 threads.
Compressing objects: 100% (3/3), done.
Recording objects: 100% (3/3), 1.08 KiB | 1.08 MiB/s, ready.
Total 3 (delta 1), reused 0 (delta 0).
To gitlab-gitlab:vscoder/post.git
   9be6e80...e0c8f14 master -> master
```

All stages of the Pipeline were successful.

#### character-branch

Let the developer run a separate environment in Kubernetes via commit in a feature-brunch.

Let's update the Ingress config for the UI service a little bit:
`reddit-deploy/ui/templates/ingress.yml`.
``Yaml
---
apiVersion: extensions/v1beta1
kind: Ingress
metadata:
  name: {{{ template "ui.fullname"}. }}
  annotations:
    kubernetes.io/ingress.class: {{ .Values.ingress.class }}
spec:
  rules:
  - host: {{{ .Values.ingress.host | default .Release.Name }}.
    http:
      Http:
      - path: /
        backend:
          serviceName: {{{ template "ui.fullname" . }}
          service port: {{{ .Values.service.externalPort}}.
...
```
> As the controller is nginx, so the rule is different

Update the Ingress config for the UI service:
`reddit-deploy/ui/templates/values.yml'.  
``Yaml
---
service:
  internalPort: 9292
  externalPort: 9292

image:
  repository: vscoder/ui
  tag: latest

# We'll use nginx-ingress, 
# that was put together with the gitlab # 
# (it's faster and the rules are more flexible than GCP)
ingress:
  class: nginx

postHost:
postPort:
commentHost:
commentPort:
...
```
**Note:** it's possible that the path to the file in RS is not correct, and there should be `reddit-deploy/ui/values.yml`, since such a file exists in this path, unlike the variant from RS. That's why we use it, because it looks more logical.

Let the developer run a separate environment in Kubernetes via commit in a feature-brunch.

1. Create a new brunch in the ui repository.
``shell
git checkout -b feature/3
```
``log
Switched to the new "feature/3" branch.
```
2. update the `ui/.gitlab-ci.yml` file:
``yaml`
---
image: alpine:latest

(Sighs)
  - build
  - test
  - review
  - release

build:
  stage: build
  image: docker:git
  Services:
    - docker:18.09.7-dind
  script:
    - setup_docker
    - build
  It's not:
    DOCKER_DRIVER: overlay2
  Only:
    -

Test:
  stage: test
  script:
    - exit 0
  Only:
    -

release:
  stage: release
  image: docker
  Services:
    - docker:18.09.7-dind
  script:
    - setup_docker
    - release
  Only:
    - master

review:
  stage: review
  script:
    - install_dependencies
    - ensure_namespace
    - install_tiller
    -
  Oh:
    KUBE_NAMESPACE: review
    host: $CI_PROJECT_PATH_SLUG-$CI_COMMIT_REF_SLUG
  Environment:
    name: review/$CI_PROJECT_PATH/$CI_COMMIT_REF_NAME
    url: http://$CI_PROJECT_PATH_SLUG-$CI_COMMIT_REF_SLUG
    on_stop: stop_review
  Only:
    refs:
      - branches
    kubernetes: active
  except:
    - master

.auto_devops: &auto_devops |
  ["$TRACE" ] && set -x.
  export CI_REGISTRY="index.docker.io"
  export CI_APPLICATION_REPOSITORY=$CI_REGISTRY/$CI_PROJECT_PATH
  export CI_APPLICATION_TAG=$CI_COMMIT_REF_SLUG
  export CI_CONTAINER_NAME=ci_job_build_${CI_JOB_ID}
  export TILLER_NAMESPACE="kube-system"

  function deploy() {
    track="${1-stable}"
    name="$CI_ENVIRONMENT_SLUG".

    if [["$track" != "stable" ]]; then.
      name="$name-$track"
    fi

    "Clone deploy repository..."
    git clone http://gitlab-gitlab/$CI_PROJECT_NAMESPACE/reddit-deploy.git

    "Download helm dependencies..."
    helm dep update reddit-deploy/reddit

    echo "Deploy helm release $name to $KUBE_NAMESPACE"
    helm upgrade --install \
      --wait \
      -set ui.ingress.host="$host" \
      -set $CI_PROJECT_NAME.image.tag=$CI_APPLICATION_TAG \.
      --namespace="$KUBE_NAMESPACE." \
      --version="$CI_PIPELINE_ID-$CI_JOB_ID". \
      "$name" \
      reddit-deploy/reddit/
  }

  function install_dependencies() {

    apk add -U openssl curl tar gzip bash ca-certificates git
    wget -q -O /etc/apk/keys/sgerrand.rsa.pub https://alpine-pkgs.sgerrand.com/sgerrand.rsa.pub.
    wget https://github.com/sgerrand/alpine-pkg-glibc/releases/download/2.23-r3/glibc-2.23-r3.apk
    apk add glibc-2.23-r3.apk
    rm glibc-2.23-r3.apk

    curl https://storage.googleapis.com/pub/gsutil.tar.gz | tar -xz -C $HOME
    export PATH=${PATH}:$HOME/gsutil

    curl https://kubernetes-helm.storage.googleapis.com/helm-v2.13.1-linux-amd64.tar.gz | tar zx

    mv linux-amd64/helm /usr/bin/
    helm version --client

    curl -o /usr/bin/sync-repo.sh https://raw.githubusercontent.com/kubernetes/helm/master/scripts/sync-repo.sh.
    chmod a+x /usr/bin/sync-repo.sh

    curl -L -o /usr/bin/kubectl https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl
    chmod +x /usr/bin/kubectl
    kubectl version --client
  }

  function setup_docker() {
    if ! docker info &>/dev/null; then
      if [ -z "$DOCKER_HOST" -a "$KUBERNETES_PORT" ]; then
        export DOCKER_HOST='tcp://localhost:2375'.
      fi
    fi
  }

  function ensure_namespace() {
    kubectl describe namespace "$KUBE_NAMESPACE" || kubectl create namespace "$KUBE_NAMESPACE"
  }

  function release() {

    "Updating docker images..."

    if [[ -n "$CI_REGISTRY_USER" ]]; then
      "Logging to GitLab Container Registry with CI credentials..."
      docker login -u "$CI_REGISTRY_USER" -p "$CI_REGISTRY_PASSWORD"
      echo ""
    fi

    docker pull "$CI_APPLICATION_REPOSITORY:$CI_APPLICATION_TAG"
    docker tag "$CI_APPLICATION_REPOSITORY:$CI_APPLICATION_TAG" "$CI_APPLICATION_REPOSITORY:$(cat VERSION)".
    docker push "$CI_APPLICATION_REPOSITORY:$(cat VERSION)"
    echo ""
  }

  function build() {

    "Building Dockerfile-based application..."
    echo `git show --format="%h" HEAD | head -1` > build_info.txt
    echo `git rev-parse --abbrev-ref HEAD` >> build_info.txt.
    docker build -t "$CI_APPLICATION_REPOSITORY:$CI_APPLICATION_TAG" .

    if [[ -n "$CI_REGISTRY_USER" ]]; then
      "Logging to GitLab Container Registry with CI credentials..."
      docker login -u "$CI_REGISTRY_USER" -p "$CI_REGISTRY_PASSWORD"
      echo ""
    fi

    "Pushing to GitLab Container Registry..."
    docker push "$CI_APPLICATION_REPOSITORY:$CI_APPLICATION_TAG"
    echo ""
  }

  function install_tiller() {
    "Checking Tiller..."
    helm init --upgrade
    kubectl rollout status -n "$TILLER_NAMESPACE" -w "deployment/tiller-deploy"
    if ! helm version --debug; then
      "Failed to init Tiller."
      return one.
    fi
    echo ""
  }

before_script:
  - *auto_devops
...
```

3. Comment and run the changes.
``shell
git push
```
``log
Counting objects: 3, done.
Delta compression using up to 12 threads.
Compressing objects: 100% (3/3), done.
Recording objects: 100% (3/3), 1.91 KiB | 1.91 MiB/s, ready.
Total 3 (delta 1), reused 0 (delta 0).
remote: 
remote: To create a merge request for feature/3, visit:
remote: http://gitlab-gitlab/vscoder/ui/merge_requests/new?merge_request%5Bsource_branch%5D=feature%2F3
remote: 
To gitlab-gitlab:vscoder/ui.git
 * [new branch] feature/3 -> feature/3
```

But the error, however, `yaml invalid` says Hitlab. Check it out: http://gitlab-gitlab/ci/lint.
``log
Error: review job: on_stop job stop_review is not defined
```
Job `stop_review` will be added further to the RS.

In the commits of the `feature/3` branch you can find the changes made.

Note that we have added a `review` stage that runs the application in k8s commit to **feature-brunches** (not master).
```yaml
review:
  stage: review
  script:
    - install_dependencies
    - ensure_namespace
    - install_tiller
    -
  Oh:
    KUBE_NAMESPACE: review
    host: $CI_PROJECT_PATH_SLUG-$CI_COMMIT_REF_SLUG
  Environment:
    name: review/$CI_PROJECT_PATH/$CI_COMMIT_REF_NAME
    url: http://$CI_PROJECT_PATH_SLUG-$CI_COMMIT_REF_SLUG
    on_stop: stop_review
  Only:
    refs:
      - branches
    kubernetes: active
  except:
    - master
```

We added the `deploy` function which loads _Chart_ from the `reddit-deploy` repository and makes a release in the `review` with the application image built in the `build` stage.
``shell``.
function deploy() {
  track="${1-stable}"
  name="$CI_ENVIRONMENT_SLUG".

  if [["$track" != "stable" ]]; then.
    name="$name-$track"
  fi

  "Clone deploy repository..."
  git clone http://gitlab-gitlab/$CI_PROJECT_NAMESPACE/reddit-deploy.git

  "Download helm dependencies..."
  helm dep update reddit-deploy/reddit

  echo "Deploy helm release $name to $KUBE_NAMESPACE"
  helm upgrade --install \
    --wait \
    -set ui.ingress.host="$host" \
    -set $CI_PROJECT_NAME.image.tag=$CI_APPLICATION_TAG \.
    --namespace="$KUBE_NAMESPACE." \
    --version="$CI_PIPELINE_ID-$CI_JOB_ID". \
    "$name" \
    reddit-deploy/reddit/
}
```

We can see which releases are running (we can't really, because we still don't have a job `review`, so just go ahead for now).

The environments created for such purposes are temporary, they need to be "killed" when they are no longer needed.

Add to `.gitlab-ci.yml'.
``Yaml
Oh:
  - build
  - test
  - review
  - release
  - cleanup # this one

stop_review: # And this
  stage: cleanup
  It's not:
    GIT_STRATEGY: none
  script:
    - install_dependencies
    - delete
  Environment:
    name: review/$CI_PROJECT_PATH/$CI_COMMIT_REF_NAME
    action: stop
  when: manual
  allow_failure: true
  Only:
    refs:
      - branches
    kubernetes: active
  except:
    - master
```

Add environment removal function
``shell
  function delete() {
    track="${1-stable}"
    name="$CI_ENVIRONMENT_SLUG".
    helm delete "$name" --purge || true
  }
```

The final `ui/.gitlab-ci.yml`
``Yaml
---
image: alpine:latest

(Sighs)
  - build
  - test
  - review
  - release
  - cleanup

build:
  stage: build
  image: docker:git
  Services:
    - docker:18.09.7-dind
  script:
    - setup_docker
    - build
  It's not:
    DOCKER_DRIVER: overlay2
  Only:
    -

Test:
  stage: test
  script:
    - exit 0
  Only:
    -

release:
  stage: release
  image: docker
  Services:
    - docker:18.09.7-dind
  script:
    - setup_docker
    - release
  Only:
    - master

review:
  stage: review
  script:
    - install_dependencies
    - ensure_namespace
    - install_tiller
    -
  Oh:
    KUBE_NAMESPACE: review
    host: $CI_PROJECT_PATH_SLUG-$CI_COMMIT_REF_SLUG
  Environment:
    name: review/$CI_PROJECT_PATH/$CI_COMMIT_REF_NAME
    url: http://$CI_PROJECT_PATH_SLUG-$CI_COMMIT_REF_SLUG
    on_stop: stop_review
  Only:
    refs:
      - branches
    kubernetes: active
  except:
    - master

stop_review:
  stage: cleanup
  It's not:
    GIT_STRATEGY: none
  script:
    - install_dependencies
    - delete
  Environment:
    name: review/$CI_PROJECT_PATH/$CI_COMMIT_REF_NAME
    action: stop
  when: manual
  allow_failure: true
  Only:
    refs:
      - branches
    kubernetes: active
  except:
    - master

.auto_devops: &auto_devops |.
  ["$TRACE" ] && set -x.
  export CI_REGISTRY="index.docker.io"
  export CI_APPLICATION_REPOSITORY=$CI_REGISTRY/$CI_PROJECT_PATH
  export CI_APPLICATION_TAG=$CI_COMMIT_REF_SLUG
  export CI_CONTAINER_NAME=ci_job_build_${CI_JOB_ID}
  export TILLER_NAMESPACE="kube-system"

  function deploy() {
    track="${1-stable}"
    name="$CI_ENVIRONMENT_SLUG".

    if [["$track" != "stable" ]]; then.
      name="$name-$track"
    fi

    "Clone deploy repository..."
    git clone http://gitlab-gitlab/$CI_PROJECT_NAMESPACE/reddit-deploy.git

    "Download helm dependencies..."
    helm dep update reddit-deploy/reddit

    echo "Deploy helm release $name to $KUBE_NAMESPACE"
    helm upgrade --install \
      --wait \
      -set ui.ingress.host="$host" \.
      -set $CI_PROJECT_NAME.image.tag=$CI_APPLICATION_TAG \.
      --namespace="$KUBE_NAMESPACE" \.
      --version="$CI_PIPELINE_ID-$CI_JOB_ID" \.
      "$name" \
      reddit-deploy/reddit/
  }

  function install_dependencies() {

    apk add -U openssl curl tar gzip bash ca-certificates git
    wget -q -O /etc/apk/keys/sgerrand.rsa.pub https://alpine-pkgs.sgerrand.com/sgerrand.rsa.pub.
    wget https://github.com/sgerrand/alpine-pkg-glibc/releases/download/2.23-r3/glibc-2.23-r3.apk
    apk add glibc-2.23-r3.apk
    rm glibc-2.23-r3.apk

    curl https://storage.googleapis.com/pub/gsutil.tar.gz | tar -xz -C $HOME
    export PATH=${PATH}:$HOME/gsutil

    curl https://kubernetes-helm.storage.googleapis.com/helm-v2.13.1-linux-amd64.tar.gz | tar zx

    mv linux-amd64/helm /usr/bin/
    helm version --client

    curl -o /usr/bin/sync-repo.sh https://raw.githubusercontent.com/kubernetes/helm/master/scripts/sync-repo.sh.
    chmod a+x /usr/bin/sync-repo.sh

    curl -L -o /usr/bin/kubectl https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl
    chmod +x /usr/bin/kubectl
    kubectl version --client
  }

  function setup_docker() {
    if ! docker info &>/dev/null; then
      if [ -z "$DOCKER_HOST" -a "$KUBERNETES_PORT" ]; then
        export DOCKER_HOST='tcp://localhost:2375'.
      fi
    fi
  }

  function ensure_namespace() {
    kubectl describe namespace "$KUBE_NAMESPACE" || kubectl create namespace "$KUBE_NAMESPACE"
  }

  function release() {

    "Updating docker images..."

    if [[ -n "$CI_REGISTRY_USER" ]]; then
      "Logging to GitLab Container Registry with CI credentials..."
      docker login -u "$CI_REGISTRY_USER" -p "$CI_REGISTRY_PASSWORD"
      echo ""
    fi

    docker pull "$CI_APPLICATION_REPOSITORY:$CI_APPLICATION_TAG"
    docker tag "$CI_APPLICATION_REPOSITORY:$CI_APPLICATION_TAG" "$CI_APPLICATION_REPOSITORY:$(cat VERSION)".
    docker push "$CI_APPLICATION_REPOSITORY:$(cat VERSION)"
    echo ""
  }

  function build() {

    "Building Dockerfile-based application..."
    echo `git show --format="%h" HEAD | head -1` > build_info.txt
    echo `git rev-parse --abbrev-ref HEAD` >> build_info.txt.
    docker build -t "$CI_APPLICATION_REPOSITORY:$CI_APPLICATION_TAG" .

    if [[ -n "$CI_REGISTRY_USER" ]]; then
      "Logging to GitLab Container Registry with CI credentials..."
      docker login -u "$CI_REGISTRY_USER" -p "$CI_REGISTRY_PASSWORD"
      echo ""
    fi

    "Pushing to GitLab Container Registry..."
    docker push "$CI_APPLICATION_REPOSITORY:$CI_APPLICATION_TAG"
    echo ""
  }

  function delete() {
    track="${1-stable}"
    name="$CI_ENVIRONMENT_SLUG".
    helm delete "$name" --purge || true
  }

  function install_tiller() {
    "Checking Tiller..."
    helm init --upgrade
    kubectl rollout status -n "$TILLER_NAMESPACE" -w "deployment/tiller-deploy"
    if ! helm version --debug; then
      "Failed to init Tiller."
      return one.
    fi
    echo ""
  }

before_script:
  - *auto_devops
```

Run changes in Git
``shell
git add .
git ci -m "Update .gitlab-ci.yml"
git push
```
``log
[feature/3 f116405] Update .gitlab-ci.yml
 1 file changed, 25 insertions(+)
Counting objects: 3, done.
Delta compression using up to 12 threads.
Compressing objects: 100% (3/3), done.
Recording objects: 100% (3/3), 467 bytes | 467.00 KiB/s, done.
Total 3 (delta 2), reused 0 (delta 0).
remote: 
remote: To create a merge request for feature/3, visit:
remote: http://gitlab-gitlab/vscoder/ui/merge_requests/new?merge_request%5Bsource_branch%5D=feature%2F3
remote: 
To gitlab-gitlab:vscoder/ui.git
   fc6c6ac...f116405 feature/3 -> feature/3
```

Pipeline worked it out. Let's check the deposit.
``shell
helm-2.13.1 list                     
```
``log
NAME REVISION UPDATED STATUS CHART APP VERSION NAMESPACE
review-vscoder-ui-8kt2zr 1 Mon Jan 13 00:02:38 2020 DEPLOYED reddit-0.1.0 review
```

In Environments http://gitlab-gitlab/vscoder/ui/environments/1 see url http://vscoder-ui-feature-3/.

Let's bring in the host `vscoder-ui-feature-3` in `/etc/hosts`.

Go to http://vscoder-ui-feature-3/.
``log
default backend - 404
```
No okay, let's deal with... Got it, you evil Pinocchio himself))

We're watching our ingress ip
``shell
kubectl get ingress -n review 
```
``log
NAME HOSTS ADDRESS PORTS AGE
review-vscoder-ui-8kt2zr-ui * 34.107.198.236 80 15h
```

And we missed the name for ip hitlab... Diagnosis: we need more sleep)))

Prescribed in `/etc/hosts ` conformity `34.107.198.236 vscoder-ui-feature-3`. Has checked http://vscoder-ui-feature-3/ ** All services work**.


In Pipelines: http://gitlab-gitlab/vscoder/ui/pipelines let's start deleting
``log
release "review-vscoder-ui-8kt2zr" deleted
Job succeeded
```

`helm-2.13.1 ls` did not show anything this time.

**Building:**

Copy the resulting file `.gitlab-ci.yml` for ui to the repository for post and comment.
Check that the dynamic creation and removal of environments works as expected.

###### For `post #

``shell
cd ../post
cp ../ui/.gitlab-ci.yml ./
git co -b feature/4
git add .
git ci -m "Test ci"
git push
```
``log
M .gitlab-ci.yml
Switched to the new "feature/4" branch.
[feature/4 d12d4a8] Test ci
 1 file changed, 111 insertions(+), 2 deletions(-)
Counting objects: 3, done.
Delta compression using up to 12 threads.
Compressing objects: 100% (3/3), done.
Recording objects: 100% (3/3), 2.00 KiB | 2.00 MiB/s, ready.
Total 3 (delta 1), reused 0 (delta 0).
remote: 
remote: To create a merge request for feature/4, visit:
remote: http://gitlab-gitlab/vscoder/post/merge_requests/new?merge_request%5Bsource_branch%5D=feature%2F4
remote: 
To gitlab-gitlab:vscoder/post.git
 * [new branch] feature/4 -> feature/4
```

Created ingress can also be viewed at GCP https://console.cloud.google.com/kubernetes/ingresses.

reddit went up

Remember to delete


##### comment

``shell
cd ../comment
cp ../ui/.gitlab-ci.yml ./
git co -b feature/5
git add .
git ci -m "Test comment ci"
git push
```
``log
M .gitlab-ci.yml
Switched to the new "feature/5" branch.
[feature/5 78c9626] Test comment ci
 1 file changed, 111 insertions(+), 2 deletions(-)
Counting objects: 3, done.
Delta compression using up to 12 threads.
Compressing objects: 100% (3/3), done.
Recording objects: 100% (3/3), 2.00 KiB | 2.00 MiB/s, ready.
Total 3 (delta 1), reused 0 (delta 0).
remote: 
remote: To create a merge request for feature/5, visit:
remote: http://gitlab-gitlab/vscoder/comment/merge_requests/new?merge_request%5Bsource_branch%5D=feature%2F5
remote: 
To gitlab-gitlab:vscoder/comment.git
 * [new branch] feature/5 -> feature/5
```

Let's check: working environment)).

The operation of the 2 environments is tested simultaneously:
``shell
kubectl get ingress -n review
```
``log
NAME HOSTS ADDRESS PORTS AGE
review-vscoder-co-ga6art-ui * 34.107.213.1 80 7m43s
review-vscoder-po-f2yqms-ui * 34.95.116.107 80 20m
```
by http both are available

helm sees both
``shell
helm-2.13.1 ls
```
``log
NAME REVISION UPDATED STATUS CHART APP VERSION NAMESPACE
review-vscoder-co-ga6art 1 Mon Jan 13 16:01:30 2020 DEPLOYED reddit-0.1.0 review   
review-vscoder-po-f2yqms 1 Mon Jan 13 15:48:35 2020 DEPLOYED reddit-0.1.0 review
```

Remove both via gitlab.


#### Deploym

Now let's create a `staging` and `production` environment for the application.

Create a file `reddit-deploy/.gitlab-ci.yml`.
``Yaml
---
image: alpine:latest

(Sighs)
  - test
  - staging
  - production

Test:
  stage: test
  script:
    - exit 0
  Only:
    -
    -

Staging:
  stage: staging
  script:
  - install_dependencies
  - ensure_namespace
  - install_tiller
  -
  It's not:
    KUBE_NAMESPACE: staging
  Environment:
    name: staging
    url: http://staging
  Only:
    refs:
      - master
    kubernetes: active

production:
  stage: production
  script:
    - install_dependencies
    - ensure_namespace
    - install_tiller
    -
  It's not:
    KUBE_NAMESPACE: production
  Environment:
    name: production
    url: http://production
  when: manual
  Only:
    refs:
      - master
    kubernetes: active

.auto_devops: &auto_devops |.
  # Auto DevOps and functions
  ["$TRACE" ] && set -x.
  export CI_REGISTRY="index.docker.io"
  export CI_APPLICATION_REPOSITORY=$CI_REGISTRY/$CI_PROJECT_PATH
  export CI_APPLICATION_TAG=$CI_COMMIT_REF_SLUG
  export CI_CONTAINER_NAME=ci_job_build_${CI_JOB_ID}
  export TILLER_NAMESPACE="kube-system"

  function deploy() {
    echo $KUBE_NAMESPACE
    track="${1-stable}"
    name="$CI_ENVIRONMENT_SLUG".
    helm dep build reddit

    # for microservice in $(helm dep ls | grep "file://" | awk '{print $1}') ; do
    # SET_VERSION="$SET_VERSION \ -set $microservice.image.tag='$(curl http://gitlab-gitlab/$CI_PROJECT_NAMESPACE/ui/raw/master/VERSION)''.

    helm upgrade --install \
      --wait \
      -set ui.ingress.host="$host" \.
      -set ui.image.tag="$(curl http://gitlab-gitlab/$CI_PROJECT_NAMESPACE/ui/raw/master/VERSION)". \
      -set post.image.tag="$(curl http://gitlab-gitlab/$CI_PROJECT_NAMESPACE/post/raw/master/VERSION)". \
      -set comment.image.tag="$(curl http://gitlab-gitlab/$CI_PROJECT_NAMESPACE/comment/raw/master/VERSION)". \
      --namespace="$KUBE_NAMESPACE" \.
      --version="$CI_PIPELINE_ID-$CI_JOB_ID" \.
      "$name" \
      reddit
  }

  function install_dependencies() {

    apk add -U openssl curl tar gzip bash ca-certificates git
    wget -q -O /etc/apk/keys/sgerrand.rsa.pub https://alpine-pkgs.sgerrand.com/sgerrand.rsa.pub.
    wget https://github.com/sgerrand/alpine-pkg-glibc/releases/download/2.23-r3/glibc-2.23-r3.apk
    apk add glibc-2.23-r3.apk
    rm glibc-2.23-r3.apk

    curl https://kubernetes-helm.storage.googleapis.com/helm-v2.13.1-linux-amd64.tar.gz | tar zx

    mv linux-amd64/helm /usr/bin/
    helm version --client

    curl -L -o /usr/bin/kubectl https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl
    chmod +x /usr/bin/kubectl
    kubectl version --client
  }

  function ensure_namespace() {
    kubectl describe namespace "$KUBE_NAMESPACE" || kubectl create namespace "$KUBE_NAMESPACE"
  }

  function install_tiller() {
    "Checking Tiller..."
    helm init --upgrade
    kubectl rollout status -n "$TILLER_NAMESPACE" -w "deployment/tiller-deploy"
    if ! helm version --debug; then
      "Failed to init Tiller."
      return one.
    fi
    echo ""
  }

  function delete() {
    track="${1-stable}"
    name="$CI_ENVIRONMENT_SLUG".
    helm delete "$name" || true
  }

before_script:
  - *auto_devops
```

Run the reddit-deploy branch master
``shell
cd ../reddit-deploy
git add .
git ci -m "Update .gitlab-ci.yml and some others..."
git push
```
``log
[master cfe4726] Update .gitlab-ci.yml and some others...
 3 files changed, 130 insertions(+), 3 deletions(-)
 create mode 100644 .gitlab-ci.yml
Object count: 7, ready.
Delta compression using up to 12 threads.
Compressing objects: 100% (7/7), done.
Recording objects: 100% (7/7), 2.16 KiB | 1.08 MiB/s, ready.
Total 7 (delta 2), reused 0 (delta 0).
To gitlab-gitlab:vscoder/reddit-deploy.git.
   cbe8d36...cfe4726 master -> master
```

This file is different from the previous ones:

1. It doesn't build docker images
2. Deploying on static environments (staging and production)
3. Does not remove the environment

Make sure the staging is successfully completed... Error in job `staging`
``log
$pread
staging
Error: requirements.lock is out of sync with requirements.yaml
...
```

Update dependencies
``shell
cd reddit-deploy/reddit
helm-2.13.1 update
```
``log
Hang tight while we grab the latest from your chart repositories.
...Unable to get an update from the "local" chart repository (http://127.0.0.1:8879/charts):
        Get http://127.0.0.1:8879/charts/index.yaml: dial tcp 127.0.0.1:8879: connect: connection refused
...Successfully got an update from the "stable" chart repository...
Update Complete. ⎈Happy Helming!⎈
Saving 4 charts
Downloading mongodb from repo https://kubernetes-charts.storage.googleapis.com
Deleting outdated charts
```
``shell
reddit-deploy/reddit
git ci -m "Fix Chart reddit requirements"
git push
```
``log
[master 720dc38] Fix Chart reddit requirements
 1 file changed, 2 insertions(+), 2 deletions(-)
Counting objects: Four, done.
Delta compression using up to 12 threads.
Compressing objects: 100% (4/4), done.
Recording objects: 100% (4/4), 466 bytes | 466.00 KiB/s, done.
Total 4 (delta 3), reused 0 (delta 0).
To gitlab-gitlab:vscoder/reddit-deploy.git.
   cfe4726...720dc38 master -> master
```

Deploy at staging was a success. The site is available under the link from http://gitlab-gitlab/vscoder/reddit-deploy/environments.

We roll out to Production: here we launch a manual paipeline on the prod. And we wait for the Pipeline to finish.

In http://gitlab-gitlab/vscoder/reddit-deploy/environments, you can see both environments

You can also see everything in helm
``shell
helm-2.13.1 ls
```
``log
NAME REVISION UPDATED STATUS CHART APP VERSION NAMESPACE 
production 1 Mon Jan 13 17:16:34 2020 DEPLOYED reddit-0.1.0 production
staging 1 Mon Jan 13 17:08:55 2020 DEPLOYED reddit-0.1.0 staging
```

#### Pipeline of a healthy person

Now almost all logic of the Pipeline is enclosed in `Auto_devops` and is difficult to read. Let's redesign the existing Pipeline for `ui` so that it matches the Gitlab syntax.

``Yaml
---
image: alpine:latest

(Sighs)
  - build
  - test
  - review
  - release
  - cleanup

build:
  stage: build
  Only:
    -
  image: docker:git
  Services:
    - docker:18.09.7-dind
  It's not:
    DOCKER_DRIVER: overlay2
    CI_REGISTRY: 'index.docker.io'.
    CI_APPLICATION_REPOSITORY: $CI_REGISTRY/$CI_PROJECT_PATH
    CI_APPLICATION_TAG: $CI_COMMIT_REF_SLUG
    CI_CONTAINER_NAME: ci_job_build_${CI_JOB_ID}
  before_script:
    - >
      if ! docker info &>/dev/null; then
        if [ -z "$DOCKER_HOST" -a "$KUBERNETES_PORT" ]; then
          export DOCKER_HOST='tcp://localhost:2375'.
        fi
      fi
  script:
    # Building
    - "Building Dockerfile-based application..."
    - echo `git show --format="%h" HEAD | head -1` > build_info.txt
    - echo `git rev-parse --abbrev-ref HEAD` >> build_info.txt.
    - docker build -t "$CI_APPLICATION_REPOSITORY:$CI_APPLICATION_TAG" .
    - >
      if [[ -n "$CI_REGISTRY_USER" ]]; then
        "Logging to GitLab Container Registry with CI credentials...for construction"
        docker login -u "$CI_REGISTRY_USER" -p "$CI_REGISTRY_PASSWORD"
      fi
    - "Pushing to GitLab Container Registry..."
    - docker push "$CI_APPLICATION_REPOSITORY:$CI_APPLICATION_TAG"

Test:
  stage: test
  script:
    - exit 0
  Only:
    -

release:
  stage: release
  image: docker
  Services:
    - docker:18.09.7-dind
  It's not:
    CI_REGISTRY: 'index.docker.io'.
    CI_APPLICATION_REPOSITORY: $CI_REGISTRY/$CI_PROJECT_PATH
    CI_APPLICATION_TAG: $CI_COMMIT_REF_SLUG
    CI_CONTAINER_NAME: ci_job_build_${CI_JOB_ID}
  before_script:
    - >
      if ! docker info &>/dev/null; then
        if [ -z "$DOCKER_HOST" -a "$KUBERNETES_PORT" ]; then
          export DOCKER_HOST='tcp://localhost:2375'.
        fi
      fi
  script:
    # Releasing
    - "Updating docker images..."
    - >
      if [[ -n "$CI_REGISTRY_USER" ]]; then
        "Logging to GitLab Container Registry with CI credentials for release..."
        docker login -u "$CI_REGISTRY_USER" -p "$CI_REGISTRY_PASSWORD".
      fi
    - docker pull "$CI_APPLICATION_REPOSITORY:$CI_APPLICATION_TAG".
    - docker tag "$CI_APPLICATION_REPOSITORY:$CI_APPLICATION_TAG" "$CI_APPLICATION_REPOSITORY:$(cat VERSION)".
    - docker push "$CI_APPLICATION_REPOSITORY:$(cat VERSION)"
    # latest is neede for feature flags
    - docker tag "$CI_APPLICATION_REPOSITORY:$CI_APPLICATION_TAG" "$CI_APPLICATION_REPOSITORY:latest".
    - docker push "$CI_APPLICATION_REPOSITORY:latest"
  Only:
    - master

review:
  stage: review
  Oh:
    KUBE_NAMESPACE: review
    host: $CI_PROJECT_PATH_SLUG-$CI_COMMIT_REF_SLUG
    TILLER_NAMESPACE: kube-system
    CI_APPLICATION_TAG: $CI_COMMIT_REF_SLUG
    name: $CI_ENVIRONMENT_SLUG
  Environment:
    name: review/$CI_PROJECT_PATH/$CI_COMMIT_REF_NAME
    url: http://$CI_PROJECT_PATH_SLUG-$CI_COMMIT_REF_SLUG
    on_stop: stop_review
  Only:
    refs:
      - branches
    kubernetes: active
  except:
    - master
  before_script:
    # installing dependencies
    - apk add -U openssl curl tar gzip bash ca-certificates git
    - wget -q -O /etc/apk/keys/sgerrand.rsa.pub https://alpine-pkgs.sgerrand.com/sgerrand.rsa.pub.
    - wget https://github.com/sgerrand/alpine-pkg-glibc/releases/download/2.23-r3/glibc-2.23-r3.apk
    - apk add glibc-2.23-r3.apk
    - curl https://storage.googleapis.com/pub/gsutil.tar.gz | tar -xz -C $HOME
    - export PATH=${PATH}:$HOME/gsutil
    - curl https://kubernetes-helm.storage.googleapis.com/helm-v2.13.1-linux-amd64.tar.gz | tar zx
    - mv linux-amd64/helm /usr/bin/
    - helm version --client
    - curl -o /usr/bin/sync-repo.sh https://raw.githubusercontent.com/kubernetes/helm/master/scripts/sync-repo.sh.
    - chmod a+x /usr/bin/sync-repo.sh
    - curl -L -o /usr/bin/kubectl https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl
    - chmod +x /usr/bin/kubectl
    - kubectl version --client
    # providing namespace
    - kubectl describe namespace "$KUBE_NAMESPACE" || kubectl create namespace "$KUBE_NAMESPACE"
    # Tiller
    - "Checking Tiller..."
    - helm init --upgrade
    - kubectl rollout status -n "$TILLER_NAMESPACE" -w "deployment/tiller-deploy"
    - >
      if ! helm version --debug; then
        "Failed to init Tiller."
        exit 1
      fi
  script:
    - export track="${1-stable}"
    - >
      if [["$track" != "stable" ]]; then.
        name="$name-$track"
      fi
    - "Clone deploy repository..."
    - git clone http://gitlab-gitlab/$CI_PROJECT_NAMESPACE/reddit-deploy.git
    - "Download helm dependencies..."
    - helm dep update reddit-deploy/reddit
    - echo "Deploy helm release $name to $KUBE_NAMESPACE"
    - "Upgrading existing release..."
    - echo "helm upgrade --install --wait --set ui.ingress.host="$host" --set $CI_PROJECT_NAME.image.tag="$CI_APPLICATION_TAG" --namespace="$KUBE_NAMESPACE" --version="$CI_PIPELINE_ID-$CI_JOB_ID" "$name" reddit-deploy/reddit/".
    - >
      helm upgrade \
        --install \
        --wait \
        -set ui.ingress.host="$host" \.
        -set $CI_PROJECT_NAME.image.tag="$CI_APPLICATION_TAG" \.
        --namespace="$KUBE_NAMESPACE" \.
        --version="$CI_PIPELINE_ID-$CI_JOB_ID" \.
        "$name" \
        reddit-deploy/reddit/

stop_review:
  stage: cleanup
  It's not:
    GIT_STRATEGY: none
    name: $CI_ENVIRONMENT_SLUG
  Environment:
    name: review/$CI_PROJECT_PATH/$CI_COMMIT_REF_NAME
    action: stop
  when: manual
  allow_failure: true
  Only:
    refs:
      - branches
    kubernetes: active
  except:
    - master
  before_script:
    # installing dependencies
    - apk add -U openssl curl tar gzip bash ca-certificates git
    - wget -q -O /etc/apk/keys/sgerrand.rsa.pub https://alpine-pkgs.sgerrand.com/sgerrand.rsa.pub.
    - wget https://github.com/sgerrand/alpine-pkg-glibc/releases/download/2.23-r3/glibc-2.23-r3.apk
    - apk add glibc-2.23-r3.apk
    - curl https://storage.googleapis.com/pub/gsutil.tar.gz | tar -xz -C $HOME
    - export PATH=${PATH}:$HOME/gsutil
    - curl https://kubernetes-helm.storage.googleapis.com/helm-v2.13.1-linux-amd64.tar.gz | tar zx
    - mv linux-amd64/helm /usr/bin/
    - helm version --client
    - curl -o /usr/bin/sync-repo.sh https://raw.githubusercontent.com/kubernetes/helm/master/scripts/sync-repo.sh.
    - chmod a+x /usr/bin/sync-repo.sh
    - curl -L -o /usr/bin/kubectl https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl
    - chmod +x /usr/bin/kubectl
    - kubectl version --client
  script:
    - helm delete "$name" --purge
...
```
The subtleties of the syntax:

- The declaration of variables can be moved to variables
- You can write it down like this:
  ``shell
  if [["$track" != "stable" ]]; then.
  name="$name-$track"
  fi
  ```
- And to put a line like this..:
  ``shell
  helm upgrade --install \
  --wait \
  -set ui.ingress.host="$host"
  ```

As you can see, the code readability has greatly increased.


#### Evicted

While I was working here, k8s evicted my gitlab =()
``shell
kubectl get pods -n gitlab
```
``log
NAME READY STATUS RESTARTS AGE
gitlab-gitlab-766445f7d7-2q69s 0/1 Evicted 0 43m
gitlab-gitlab-766445f7d7-4tj6x 0/1 Evicted 0 43m
gitlab-gitlab-766445f7d7-8gmp6 0/1 Evicted 0 43m
gitlab-gitlab-766445f7d7-9brxd 0/1 Evicted 0 43m
gitlab-gitlab-766445f7d7-9ptqb 0/1 Evicted 0 46h
gitlab-gitlab-766445f7d7-9zdkd 0/1 Evicted 0 43m
gitlab-gitlab-766445f7d7-d7mf6 0/1 Evicted 0 43m
gitlab-gitlab-766445f7d7-fnrx4 0/1 Evicted 0 43m
gitlab-gitlab-766445f7d7-jbw4w 0/1 Evicted 0 43m
gitlab-gitlab-766445f7d7-k8spx 0/1 Evicted 0 43m
gitlab-gitlab-766445f7d7-mgv9f 0/1 Evicted 0 43m
gitlab-gitlab-766445f7d7-mkw7l 0/1 Evicted 0 43m
gitlab-gitlab-766445f7d7-r97ht 0/1 Evicted 0 43m
gitlab-gitlab-766445f7d7-rfzl6 0/1 CrashLoopBackOff 8 43m
gitlab-gitlab-766445f7d7-sbd99 0/1 Evicted 0 43m
gitlab-gitlab-766445f7d7-sjt2q 0/1 Evicted 0 43m
gitlab-gitlab-766445f7d7-smwfk 0/1 Evicted 0 43m
gitlab-gitlab-766445f7d7-t6lb7 0/1 Evicted 0 43m
gitlab-gitlab-766445f7d7-tf4vq 0/1 Evicted 0 43m
gitlab-gitlab-postgresql-66d5b899b8-67qbm 1/1 Running 0 46h
gitlab-gitlab-redis-6c675dd568-pb6xw 1/1 Running 0 46h
gitlab-gitlab-runner-644c574f56-48kvd 1/1 Running 4 46h
```

``shell
kubectl logs gitlab-gitlab-766445f7d7-rfzl6 -n gitlab
```
``log
  * service[postgres-exporter] action restart
    - restart service[postgres-exporter]
  * ruby_block[reload postgres-exporter svlogd configuration] action create
    - The ruby block reload postgres-exporter svlogd configuration

Running handlers:
Running handlers complete
Chef Client finished, 318/508 resources updated in 02 minutes 51 seconds
gitlab Reconfigured!
Checking for an omnibus managed postgresql: NOT OK
No currently installed postgresql in the omnibus instance found.
Runnning Post Reconfigure Script...
```

``shell
kubectl describe pod gitlab-gitlab-766445f7d7-rfzl6 -n gitlab
```
``log
Name: gitlab-gitlab-766445f7d7-rfzl6
Namespace: gitlab
Priority: 0
Node: gke-reddit-public-gitlab-pool-05e41e6e-5kqp/10.3.0.3
Start Time: Mon, 13 Jan 2020 23:35:52 +0300
Labels: app=gitlab-gitlab
                name=gitlab-gitlab
                pod-template-hash=766445f7d7
Annotations: cni.projectcalico.org/podIP: 10.4.0.89/32
Status:         Running
IP: 10.4.0.89
IPs:            <none>
Controlled By:  ReplicaSet/gitlab-gitlab-766445f7d7
Containers:
  gitlab:
    Container ID: docker://e6d8fdc48b61ebdcd596798b22892f3f310b1b644fe82ad18562e521f8292973
    Image: gitlab/gitlab-ce:10.6.2-ce.0
    Image ID: docker-pullable://gitlab/gitlab-ce@sha256:573e1cf90a5bf1bd9b964d782dd22394b73d67ccdf7f47e0d3152feb112ac00d
    Ports:         8105/TCP, 8065/TCP, 8005/TCP, 22/TCP, 9090/TCP, 8090/TCP
    Host Ports:    0/TCP, 0/TCP, 0/TCP, 0/TCP, 0/TCP, 0/TCP.
    Command:
      /pin/bash
      -c
      sed -i "s/environment ({'GITLAB_ROOT_PASSWORD' => initial_root_password }) if initial_root_password/environment ({'GITLAB_ROOT_PASSWORD' => initial_root_password, 'GITLAB_SHARED_RUNNERS_REGISTRATION_TOKEN' => node['gitlab']['initial_shared_runners_registration_token'] })/g" /opt/gitlab/embedded/cookbooks/gitlab/recipes/database_migrations. rb && echo 'gitlab-omnibus-helm-chart' > /opt/gitlab/embedded/service/gitlab-rails/INSTALLATION_TYPE && exec /assets/wrapper
    State:          Running
      Started:      Tue, 14 Jan 2020 00:17:18 +0300
    Last State:     Terminated
      Reason:       Error
      Exit Code:    137
      Started:      Tue, 14 Jan 2020 00:08:11 +0300
      Finished:     Tue, 14 Jan 2020 00:12:09 +0300
    Ready:          False
    Restart Count:  9
    Liveness: http-get http://:8005/health_check%3Ftoken=SXBAQichEJasbtDSygrD delay=180s timeout=15s period=10s #success=1 #failure=3.
    Readiness: http-get http://:8005/health_check%3Ftoken=SXBAQichEJasbtDSygrD delay=15s timeout=1s period=10s #success=1 #failure=3.
    Environment:
      GITLAB_EXTERNAL_SCHEME:                            <set to the key 'external_scheme' of config map 'gitlab-gitlab-config'> Optional: false
      GITLAB_EXTERNAL_HOSTNAME:                          <set to the key 'external_hostname' of config map 'gitlab-gitlab-config'> Optional: false
      GITLAB_REGISTRY_EXTERNAL_SCHEME:                   <set to the key 'registry_external_scheme' of config map 'gitlab-gitlab-config'> Optional: false
      GITLAB_REGISTRY_EXTERNAL_HOSTNAME:                 <set to the key 'registry_external_hostname' of config map 'gitlab-gitlab-config'> Optional: false
      GITLAB_MATTERMOST_EXTERNAL_SCHEME:                 <set to the key 'mattermost_external_scheme' of config map 'gitlab-gitlab-config'> Optional: false
      GITLAB_MATTERMOST_EXTERNAL_HOSTNAME:               <set to the key 'mattermost_external_hostname' of config map 'gitlab-gitlab-config'> Optional: false
      POSTGRES_USER: <set to the key 'postgres_user' of config map 'gitlab-gitlab-config'> Optional: false
      POSTGRES_PASSWORD: <set to the key 'postgres_password' in secret 'gitlab-gitlab-secrets'> Optional: false
      POSTGRES_DB: <set to the key 'postgres_db' of config map 'gitlab-gitlab-config'> Optional: false
      GITLAB_INITIAL_SHARED_RUNNERS_REGISTRATION_TOKEN: <set to the key 'initial_shared_runners_registration_token' in secret 'gitlab-gitlab-secrets'> Optional: false
      MATTERMOST_APP_UID: <set to the key 'mattermost_app_uid' of config map 'gitlab-gitlab-config'> Optional: false
      MATTERMOST_APP_SECRET: <set to the key 'mattermost_app_secret' in secret 'gitlab-gitlab-secrets'> Optional: false
      PAGES_EXTERNAL_SCHEME:                             <set to the key 'pages_external_scheme' of config map 'gitlab-gitlab-config'> Optional: false
      PAGES_EXTERNAL_DOMAIN: <set to the key 'pages_external_domain' of config map 'gitlab-gitlab-config' > Optional: false
      GITLAB_OMNIBUS_CONFIG: external_url "#{ENV['GITLAB_EXTERNAL_SCHEME']}://#{ENV['GITLAB_EXTERNAL_HOSTNAME']}".
                                                         registry_external_url "#{ENV['GITLAB_REGISTRY_EXTERNAL_SCHEME']}://#{ENV['GITLAB_REGISTRY_EXTERNAL_HOSTNAME']}".
                                                         "#{ENV['GITLAB_MATTERMOST_EXTERNAL_SCHEME']}://#{ENV['GITLAB_MATTERMOST_EXTERNAL_HOSTNAME']}".
                                                         
                                                         gitlab_rails['initial_shared_runners_registration_token'] = ENV['GITLAB_INITIAL_SHARED_RUNNERS_REGISTRATION_TOKEN'].
                                                         
                                                         nginx['enable'] = false
                                                         registry_nginx['enable'] = false
                                                         mattermost_nginx['enable'] = false
                                                         
                                                         gitlab_workhorse['listen_network'] = 'tcp'.
                                                         gitlab_workhorse['listen_addr'] = '0.0.0.0:8005'.
                                                         
                                                         mattermost['service_address'] = '0.0.0.0'.
                                                         mattermost['service_port'] = '8065'.
                                                         
                                                         registry['registry_http_addr'] = '0.0.0.0:8105'.
                                                         
                                                         postgresql['enable'] = false
                                                         gitlab_rails['db_host'] = 'gitlab-gitlab-postgresql'.
                                                         gitlab_rails['db_password'] = ENV['POSTGRES_PASSWORD'].
                                                         gitlab_rails['db_username'] = ENV['POSTGRES_USER'].
                                                         gitlab_rails['db_database'] = ENV['POSTGRES_DB'].
                                                         
                                                         redis['enable'] = false
                                                         gitlab_rails['redis_host'] = 'gitlab-gitlab-redis'.
                                                         
                                                         mattermost['file_directory'] = '/gitlab-data/mattermost';
                                                         mattermost['sql_driver_name'] = 'postgres';
                                                         mattermost['sql_data_source'] = "user=#{ENV['POSTGRES_USER']} host=gitlab-gitlab-postgresql port=5432 dbname=mattermost_production password=#{ENV['POSTGRES_PASSWORD']} sslmode=disable";
                                                         mattermost['gitlab_enable'] = true;
                                                         mattermost['gitlab_secret'] = ENV['MATTERMOST_APP_SECRET'];
                                                         mattermost['gitlab_id'] = ENV['MATTERMOST_APP_UID'];
                                                         mattermost['gitlab_scope'] = '';
                                                         mattermost['gitlab_auth_endpoint'] = "#{ENV['GITLAB_EXTERNAL_SCHEME']}://#{ENV['GITLAB_EXTERNAL_HOSTNAME']}/oauth/authorize";
                                                         mattermost['gitlab_token_endpoint'] = "#{ENV['GITLAB_EXTERNAL_SCHEME']}://#{ENV['GITLAB_EXTERNAL_HOSTNAME']}/oauth/token";
                                                         mattermost['gitlab_user_api_endpoint'] = "#{ENV['GITLAB_EXTERNAL_SCHEME']}://#{ENV['GITLAB_EXTERNAL_HOSTNAME']}/api/v4/user".
                                                         
                                                         manage_accounts['enable'] = true.
                                                         manage_storage_directories['manage_etc'] = false
                                                         
                                                         if ENV['PAGES_EXTERNAL_SCHEME'] && ENV['PAGES_EXTERNAL_DOMAIN'].
                                                           pages_external_url "#{ENV['PAGES_EXTERNAL_SCHEME']}://#{ENV['PAGES_EXTERNAL_DOMAIN']}/".
                                                           gitlab_pages['enable'] = true
                                                           gitlab_pages['listen_proxy'] = "0.0.0.0:8090".
                                                         end
                                                         
                                                         gitlab_shell['auth_file'] = '/gitlab-data/ssh/authorized_keys'.
                                                         git_data_dirs({ "default" => { "path" => "/gitlab-data/git-data" } }).
                                                         gitlab_rails['shared_path'] = '/gitlab-data/shared'.
                                                         gitlab_rails['uploads_directory'] = '/gitlab-data/uploads'.
                                                         gitlab_ci['builds_directory'] = '/gitlab-data/builds'.
                                                         gitlab_rails['registry_path'] = '/gitlab-registry'.
                                                         gitlab_rails['trusted_proxies'] = ["10.0.0.0/8", "172.16.0.0/12", "192.168.0.0/16"].
                                                         
                                                         prometheus['listen_address'] = '0.0.0.0:9090'.
                                                         postgres_exporter['enable'] = true
                                                         postgres_exporter['env'] = {
                                                           'DATA_SOURCE_NAME' => "user=#{ENV['POSTGRES_USER']} host=gitlab-gitlab-postgresql port=5432 dbname=#{ENV['POSTGRES_DB']} password=#{ENV['POSTGRES_PASSWORD']} sslmode=disable".
                                                         }
                                                         redis_exporter['enable'] = true
                                                         redis_exporter['flags'] = {
                                                           'redis.addr' => "gitlab-gitlab-redis:6379",
                                                         }
                                                         
      GITLAB_POST_RECONFIGURE_CODE: include Gitlab::CurrentSettings
                                                         
                                                         Doorkeeper::Application.where(uid: ENV["MATTERMOST_APP_UID"]).first_or_create(
                                                           name: "GitLab Mattermost."
                                                           secret: ENV["MATTERMOST_APP_SECRET"],
                                                           redirect_uri: "#{ENV["GITLAB_MATTERMOST_EXTERNAL_SCHEME"]}://#{ENV["GITLAB_MATTERMOST_EXTERNAL_HOSTNAME"]}/signup/gitlab/complete\r\n#{ENV["GITLAB_MATTERMOST_EXTERNAL_SCHEME"]}: //#{ENV["GITLAB_MATTERMOST_EXTERNAL_HOSTNAME"]}/login/gitlab/complete").
                                                         
                                                         PrometheusService.where(template: true).first_or_create(
                                                           It's true, api_url: "http://localhost:9090")
                                                         
                                                         KubernetesService.where(template: true).first_or_create(
                                                           It's true,
                                                           api_url: "https://#{ENV["KUBERNETES_SERVICE_HOST"]}:#{ENV["KUBERNETES_SERVICE_PORT"]}",
                                                           Token: File.read("/var/run/secrets/kubernetes.io/serviceaccount/token"),
                                                           ca_pem: File.read("/var/run/secrets/kubernetes.io/serviceaccount/ca.crt").
                                                         
                                                         Gitlab::CurrentSettings.current_application_settings.update_attribute(:health_check_access_token, 'SXBAQichEJasbtDSygrD').
                                                         
      GITLAB_POST_RECONFIGURE_SCRIPT: /opt/gitlab/bin/gitlab-rails runner -e production "$GITLAB_POST_RECONFIGURE_CODE".
                                                         
    Mounts:
      /etc/gitlab from config (rw)
      /gitlab-data from data (rw,path="gitlab-data")
      /gitlab-registry from registry (rw)
      /var/run/secrets/kubernetes.io/serviceaccount from default-token-znmvd (ro)
Conditions:
  Type Status
  Initialized True 
  Ready False 
  ContainersReady False 
  PodScheduled True 
Volumes:
  data:
    Type:       PersistentVolumeClaim (a reference to a PersistentVolumeClaim in the same namespace)
    ClaimName: gitlab-gitlab-storage
    ReadOnly: false
  It's the registry:
    Type:       PersistentVolumeClaim (a reference to a PersistentVolumeClaim in the same namespace)
    ClaimName: gitlab-gitlab-registry-storage
    ReadOnly: false
  I'm sorry:
    Type:       PersistentVolumeClaim (a reference to a PersistentVolumeClaim in the same namespace)
    ClaimName: gitlab-gitlab-config-storage
    ReadOnly: false
  default-token-znmvd:
    Type:        Secret (a volume populated by a Secret)
    SecretName: default-token-znmvd
    Optional: false
QoS Class:       BestEffort
Node-Selectors:  <none>
Tolerations: node.kubernetes.io/not-ready:NoExecute for 300s
                 node.kubernetes.io/unreachable:NoExecute for 300s
Events:
  Type Reason Age From Message
  ---- ------ ---- ---- -------
  Warning FailedScheduling 43m (x6 over 48m) default-scheduler 0/1 nodes are available: 1 node(s) had taints that the pod didn't tolerate.
  Normal Scheduled 43m default-scheduler Successfully assigned gitlab/gitlab-gitlab-766445f7d7-rfzl6 to gke-reddit-public-gitlab-pool-05e41e6e-5kqp.
  Normal SuccessfulAttachVolume 43m attachdetach-controller AttachVolume.Attach succeeded for volume "pvc-89b7b55a-ed38-407a-b541-06c9f59731db".
  Normal SuccessfulAttachVolume 43m attachdetach-controller AttachVolume.Attach succeeded for volume "pvc-95f58849-b3fd-4d77-8754-54fa5a807586".
  Normal SuccessfulAttachVolume 43m attachdetach-controller AttachVolume.Attach succeeded for volume "pvc-61f1ca90-83b1-47f3-969b-2cf61c6dd293".
  Normal Pulled 43m kubelet, gke-reddit-public-gitlab-pool-05e41e6e-5kqp Container image "gitlab/gitlab-ce:10.6.2-ce.0" already present on machine
  Normal Created 43m kubelet, gke-reddit-public-gitlab-pool-05e41e6e-5kqp Created container gitlab
  Normal Started 43m kubelet, gke-reddit-public gitlab-pool-05e41e6e-5kqp Started container gitlab
  Warning Unhealthy 39m (x3 over 40m) kubelet, gke-reddit-public-gitlab-pool-05e41e6e-5kqp Liveness probe failed: HTTP probe failed with statuscode: 502
  Warning Unhealthy 18m (x52 over 42m) kubelet, gke-reddit-public-gitlab-pool-05e41e6e-5kqp Readiness probe failed: Get http://10.4.0.89:8005/health_check?token=SXBAQichEJasbtDSygrD: dial tcp 10.4.0.89:8005: connect: connection refused
  Warning Unhealthy 8m15s (x113 over 40m) kubelet, gke-reddit-public-gitlab-pool-05e41e6e-5kqp Readiness probe failed: HTTP probe failed with statuscode: 502
  Warning BackOff 3m7s (x23 over 7m19s) kubelet, gke-reddit-public-gitlab-pool-05e41e6e-5kqp Back-off restarting failed container
```

After some tambourine dancing, he re-created the cluster and remodeled everything. Now the helmets show all the installations correctly.
``hell
helm-3.0.2 list --all
```
``log
NAME NAMESPACE REVISION UPDATED STATUS CHART APP VERSION
gitlab default 1 2020-01-14 20:19:24.615711767 +0300 MSK
```
``shell
helm-2.13.1 list --all
```
``log
NAME REVISION UPDATED STATUS CHART APP VERSION NAMESPACE 
production 1 Tue Jan 14 21:12:00 2020 DEPLOYED reddit-0.1.0 production
review-vscoder-co-tl8stj 1 Tue Jan 14 21:12:49 2020 DEPLOYED reddit-0.1.0 review    
review-vscoder-po-7fbjm5 1 Tue Jan 14 21:08:58 2020 DEPLOYED reddit-0.1.0 review    
review-vscoder-ui-a347ed 1 Tue Jan 14 21:08:58 2020 DEPLOYED reddit-0.1.0 review    
review-vscoder-ui-szjzwy 1 Tue Jan 14 21:08:22 2020 DEPLOYED reddit-0.1.0 review    
staging 1 Tue Jan 14 21:03:16 2020 DEPLOYED reddit-0.1.0 staging
```


#### Pipeline of the Healthy Man: Mission

1. Modify the Pipeline service _COMMENT_, which uses `helm2` for the deposit, so that the deposit is carried out using `tiller plugin`. Thus, the deposit of each of the three services should be performed differently.
2. Modify the POST_ service's pipeline so that it uses `helm3` for the deposit.

Put the resulting files of the service's `helm3' (4 pieces: `ui`, `post`, `comment`, `reddit`) into the directory `Charts/gitlabci` under the name `gitlab-ci-.yml` and commit.


##### Optimize the pipeline ui.

Created a directory `kubernetes/docker-helm ` with Dockerfile for building the base image with pre-installed `helm ` and `kubectl `.

The corresponding image has been created and uploaded to the docker hub.

Jobs `review` and `stop_review` in the specified pipeline are not optimal, because each time you install `helm` and `kubectl` in the base image `alpine:latest`. For further work, this pipeline will be rebuilt to use the `vscoder/helm:v2.13.1` image of its own assembly.

`Ui/.gitlab-ci.yml`
``Yaml
---
image: vscoder/helm:v2.13.1

stages:
  - build
  - test
  - review
  - release
  - cleanup

build:
  stage: build
  Only:
    -
  image: docker:git
  Services:
    - docker:18.09.7-dind
  It's not:
    DOCKER_DRIVER: overlay2
    CI_REGISTRY: "index.docker.io."
    CI_APPLICATION_REPOSITORY: $CI_REGISTRY/$CI_PROJECT_PATH
    CI_APPLICATION_TAG: $CI_COMMIT_REF_SLUG
    CI_CONTAINER_NAME: ci_job_build_${CI_JOB_ID}
  before_script:
    - >
      if ! docker info &>/dev/null; then
        if [ -z "$DOCKER_HOST" -a "$KUBERNETES_PORT" ]; then
          export DOCKER_HOST='tcp://localhost:2375'.
        fi
      fi
  script:
    # Building
    - "Building Dockerfile-based application..."
    - echo `git show --format="%h" HEAD | head -1` > build_info.txt
    - echo `git rev-parse --abbrev-ref HEAD` >> build_info.txt.
    - docker build -t "$CI_APPLICATION_REPOSITORY:$CI_APPLICATION_TAG" .
    - >
      if [[ -n "$CI_REGISTRY_USER" ]]; then
        "Logging to GitLab Container Registry with CI credentials...for construction"
        docker login -u "$CI_REGISTRY_USER" -p "$CI_REGISTRY_PASSWORD"
      fi
    - "Pushing to GitLab Container Registry..."
    - docker push "$CI_APPLICATION_REPOSITORY:$CI_APPLICATION_TAG"

Test:
  stage: test
  script:
    - exit 0
  Only:
    -

release:
  stage: release
  image: docker
  Services:
    - docker:18.09.7-dind
  It's not:
    CI_REGISTRY: "index.docker.io."
    CI_APPLICATION_REPOSITORY: $CI_REGISTRY/$CI_PROJECT_PATH
    CI_APPLICATION_TAG: $CI_COMMIT_REF_SLUG
    CI_CONTAINER_NAME: ci_job_build_${CI_JOB_ID}
  before_script:
    - >
      if ! docker info &>/dev/null; then
        if [ -z "$DOCKER_HOST" -a "$KUBERNETES_PORT" ]; then
          export DOCKER_HOST='tcp://localhost:2375'.
        fi
      fi
  script:
    # Releasing
    - "Updating docker images..."
    - >
      if [[ -n "$CI_REGISTRY_USER" ]]; then
        "Logging to GitLab Container Registry with CI credentials for release..."
        docker login -u "$CI_REGISTRY_USER" -p "$CI_REGISTRY_PASSWORD".
      fi
    - docker pull "$CI_APPLICATION_REPOSITORY:$CI_APPLICATION_TAG".
    - docker tag "$CI_APPLICATION_REPOSITORY:$CI_APPLICATION_TAG" "$CI_APPLICATION_REPOSITORY:$(cat VERSION)".
    - docker push "$CI_APPLICATION_REPOSITORY:$(cat VERSION)"
    # latest is neede for feature flags
    - docker tag "$CI_APPLICATION_REPOSITORY:$CI_APPLICATION_TAG" "$CI_APPLICATION_REPOSITORY:latest".
    - docker push "$CI_APPLICATION_REPOSITORY:latest"
  Only:
    - master

review:
  stage: review
  Oh:
    KUBE_NAMESPACE: review
    host: $CI_PROJECT_PATH_SLUG-$CI_COMMIT_REF_SLUG
    TILLER_NAMESPACE: kube-system
    CI_APPLICATION_TAG: $CI_COMMIT_REF_SLUG
    name: $CI_ENVIRONMENT_SLUG
  Environment:
    name: review/$CI_PROJECT_PATH/$CI_COMMIT_REF_NAME
    url: http://$CI_PROJECT_PATH_SLUG-$CI_COMMIT_REF_SLUG
    on_stop: stop_review
  Only:
    refs:
      - branches
    kubernetes: active
  except:
    - master
  before_script:
    - helm version --client
    - kubectl version --client
    # providing namespace
    - kubectl describe namespace "$KUBE_NAMESPACE" || kubectl create namespace "$KUBE_NAMESPACE"
    # Tiller
    - "Checking Tiller..."
    - helm init --upgrade
    - kubectl rollout status -n "$TILLER_NAMESPACE" -w "deployment/tiller-deploy"
    - >
      if ! helm version --debug; then
        "Failed to init Tiller."
        exit 1
      fi
  script:
    - export track="${1-stable}"
    - >
      if [["$track" != "stable" ]]; then.
        name="$name-$track"
      fi
    - "Clone deploy repository..."
    - git clone http://gitlab-gitlab/$CI_PROJECT_NAMESPACE/reddit-deploy.git
    - "Download helm dependencies..."
    - helm dep update reddit-deploy/reddit
    - echo "Deploy helm release $name to $KUBE_NAMESPACE"
    - "Upgrading existing release..."
    - echo "helm upgrade --install --wait --set ui.ingress.host="$host" --set $CI_PROJECT_NAME.image.tag="$CI_APPLICATION_TAG" --namespace="$KUBE_NAMESPACE" --version="$CI_PIPELINE_ID-$CI_JOB_ID" "$name" reddit-deploy/reddit/".
    - >
      helm upgrade \
        --install \
        --wait \
        -set ui.ingress.host="$host" \.
        -set $CI_PROJECT_NAME.image.tag="$CI_APPLICATION_TAG" \.
        --namespace="$KUBE_NAMESPACE" \.
        --version="$CI_PIPELINE_ID-$CI_JOB_ID" \.
        "$name" \
        reddit-deploy/reddit/

stop_review:
  stage: cleanup
  It's not:
    GIT_STRATEGY: none
    name: $CI_ENVIRONMENT_SLUG
  Environment:
    name: review/$CI_PROJECT_PATH/$CI_COMMIT_REF_NAME
    action: stop
  when: manual
  allow_failure: true
  Only:
    refs:
      - branches
    kubernetes: active
  except:
    - master
  before_script:
    - helm version --client
    - kubectl version --client
  script:
    - helm delete "$name" --purge
```

Pipeline's been checked out. It's working. 

Surrounding `review` works.

Environment Stop `review` works.

#### comment + tiller plugin

Modifying the Pipeline to work through helm tiller plugin.

`comment/.gitlab-ci.yml`
``Yaml
---
image: vscoder/helm:v2.13.1

stages:
  - build
  - test
  - review
  - release
  - cleanup

build:
  stage: build
  Only:
    -
  image: docker:git
  Services:
    - docker:18.09.7-dind
  It's not:
    DOCKER_DRIVER: overlay2
    CI_REGISTRY: "index.docker.io."
    CI_APPLICATION_REPOSITORY: $CI_REGISTRY/$CI_PROJECT_PATH
    CI_APPLICATION_TAG: $CI_COMMIT_REF_SLUG
    CI_CONTAINER_NAME: ci_job_build_${CI_JOB_ID}
  before_script:
    - >
      if ! docker info &>/dev/null; then
        if [ -z "$DOCKER_HOST" -a "$KUBERNETES_PORT" ]; then
          export DOCKER_HOST='tcp://localhost:2375'.
        fi
      fi
  script:
    # Building
    - "Building Dockerfile-based application..."
    - echo `git show --format="%h" HEAD | head -1` > build_info.txt
    - echo `git rev-parse --abbrev-ref HEAD` >> build_info.txt.
    - docker build -t "$CI_APPLICATION_REPOSITORY:$CI_APPLICATION_TAG" .
    - >
      if [[ -n "$CI_REGISTRY_USER" ]]; then
        "Logging to GitLab Container Registry with CI credentials...for construction"
        docker login -u "$CI_REGISTRY_USER" -p "$CI_REGISTRY_PASSWORD"
      fi
    - "Pushing to GitLab Container Registry..."
    - docker push "$CI_APPLICATION_REPOSITORY:$CI_APPLICATION_TAG"

Test:
  stage: test
  script:
    - exit 0
  Only:
    -

release:
  stage: release
  image: docker
  Services:
    - docker:18.09.7-dind
  It's not:
    CI_REGISTRY: "index.docker.io."
    CI_APPLICATION_REPOSITORY: $CI_REGISTRY/$CI_PROJECT_PATH
    CI_APPLICATION_TAG: $CI_COMMIT_REF_SLUG
    CI_CONTAINER_NAME: ci_job_build_${CI_JOB_ID}
  before_script:
    - >
      if ! docker info &>/dev/null; then
        if [ -z "$DOCKER_HOST" -a "$KUBERNETES_PORT" ]; then
          export DOCKER_HOST='tcp://localhost:2375'.
        fi
      fi
  script:
    # Releasing
    - "Updating docker images..."
    - >
      if [[ -n "$CI_REGISTRY_USER" ]]; then
        "Logging to GitLab Container Registry with CI credentials for release..."
        docker login -u "$CI_REGISTRY_USER" -p "$CI_REGISTRY_PASSWORD".
      fi
    - docker pull "$CI_APPLICATION_REPOSITORY:$CI_APPLICATION_TAG".
    - docker tag "$CI_APPLICATION_REPOSITORY:$CI_APPLICATION_TAG" "$CI_APPLICATION_REPOSITORY:$(cat VERSION)".
    - docker push "$CI_APPLICATION_REPOSITORY:$(cat VERSION)"
    # latest is neede for feature flags
    - docker tag "$CI_APPLICATION_REPOSITORY:$CI_APPLICATION_TAG" "$CI_APPLICATION_REPOSITORY:latest".
    - docker push "$CI_APPLICATION_REPOSITORY:latest"
  Only:
    - master

review:
  stage: review
  Oh:
    KUBE_NAMESPACE: review
    host: $CI_PROJECT_PATH_SLUG-$CI_COMMIT_REF_SLUG
    CI_APPLICATION_TAG: $CI_COMMIT_REF_SLUG
    name: $CI_ENVIRONMENT_SLUG
  Environment:
    name: review/$CI_PROJECT_PATH/$CI_COMMIT_REF_NAME
    url: http://$CI_PROJECT_PATH_SLUG-$CI_COMMIT_REF_SLUG
    on_stop: stop_review
  Only:
    refs:
      - branches
    kubernetes: active
  except:
    - master
  before_script:
    - helm init --client-only # init $HELM_HOME
    - helm plugin install https://github.com/rimusz/helm-tiller # install tiller plugin
    - helm version --client
    - kubectl version --client
    # providing namespace
    - kubectl describe namespace "$KUBE_NAMESPACE" || kubectl create namespace "$KUBE_NAMESPACE"
    # Tiller
    #- echo "Checking Tiller..."
    #- helm init --upgrade
    #- kubectl rollout status -n "$TILLER_NAMESPACE" -w "deployment/tiller-deploy"
    #- >
    # if ! helm version --debug; then #
    # echo "Failed to init Tiller."
    # exit 1
    # fi
  script:
    - export track="${1-stable}"
    - >
      if [["$track" != "stable" ]]; then.
        name="$name-$track"
      fi
    - "Clone deploy repository..."
    - git clone http://gitlab-gitlab/$CI_PROJECT_NAMESPACE/reddit-deploy.git
    - "Download helm dependencies..."
    - helm tiller run -- helm dep update reddit-deploy/reddit.
    - echo "Deploy helm release $name to $KUBE_NAMESPACE"
    - "Upgrading existing release..."
    - echo "helm upgrade --install --wait --set ui.ingress.host="$host" --set $CI_PROJECT_NAME.image.tag="$CI_APPLICATION_TAG" --namespace="$KUBE_NAMESPACE" --version="$CI_PIPELINE_ID-$CI_JOB_ID" "$name" reddit-deploy/reddit/".
    - >
      helm tiller run -- helm upgrade \
        --install \
        --wait \
        -set ui.ingress.host="$host" \.
        -set $CI_PROJECT_NAME.image.tag="$CI_APPLICATION_TAG" \.
        --namespace="$KUBE_NAMESPACE" \.
        --version="$CI_PIPELINE_ID-$CI_JOB_ID" \.
        "$name" \
        reddit-deploy/reddit/

stop_review:
  stage: cleanup
  It's not:
    GIT_STRATEGY: none
    name: $CI_ENVIRONMENT_SLUG
  Environment:
    name: review/$CI_PROJECT_PATH/$CI_COMMIT_REF_NAME
    action: stop
  when: manual
  allow_failure: true
  Only:
    refs:
      - branches
    kubernetes: active
  except:
    - master
  before_script:
    - helm init --client-only
    - helm plugin install https://github.com/rimusz/helm-tiller
    - helm version --client
    - kubectl version --client
  script:
    - helm tiller run -- helm delete "$name" --purge
```

Pipeline is checked: the environment `review ` will deploy, works. Environment deletion works.

If you want, you can move the installation of tiller plugin to the base docker image. I'll leave it in the Pipeline for clarity, as well as not to make it too difficult to build a base docker image for different versions of helm (2 and 3).


#### post + helm3

Fix a bug in passing the helm version when building the docker image
`kubernetes/docker-helm/Dockerfile`
``dockerfile
FROM alpine:3

# variable "HELM_VERSION" must be passed as docker environment during the image build
# docker build --no-cache --build-arg HELM_VERSION=2.13.1 -t vscoder/helm:2.13.1 .

ARG HELM_VERSION

RUN apk add --update --no-cache openssl curl tar gzip bash ca-certificates git && \.
    wget -q -O /etc/apk/keys/sgerrand.rsa.pub https://alpine-pkgs.sgerrand.com/sgerrand.rsa.pub && \.
    wget https://github.com/sgerrand/alpine-pkg-glibc/releases/download/2.23-r3/glibc-2.23-r3.apk && \
    apk add glibc-2.23-r3.apk && \
    curl https://storage.googleapis.com/pub/gsutil.tar.gz | tar -xz -C $HOME && \
    export PATH=${PATH}:$HOME/gsutil && \
    curl https://get.helm.sh/helm-v${HELM_VERSION}-linux-amd64.tar.gz | tar zx && \
    mv linux-amd64/helm /usr/bin/ && \
    helm version --client && \
    curl -o /usr/bin/sync-repo.sh https://raw.githubusercontent.com/kubernetes/helm/master/scripts/sync-repo.sh && \.
    chmod a+x /usr/bin/sync-repo.sh && \
    curl -L -o /usr/bin/kubectl https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl && \
    chmod +x /usr/bin/kubectl && \
    kubectl version --client && \
    rm -rf linux-amd64 && \
    apk del curl tar gzip && \
    rm -f /var/cache/apk/*

CMD ["bash"]
```

Let's build a base image with helm3.
Parameterized helm version in `kubernetes/docker-helm/Makefile`.
``makefile
HELM_VERSION=2.16.1

.PHONY: build publish

build:
	. ./env \
	&& export HELM_VERSION=$${HELM_VERSION} \
	&& ./docker_build.sh

publish:
	. ./env \
	&& export HELM_VERSION=$${HELM_VERSION} \
	&& ./docker_push.sh
```

We will collect and upload to the dockerhab the image with helm 3.0.2.
``shell
cd ./kubernetes/docker-helm
make build publish HELM_VERSION=3.0.2
```
``log
. ./env \
&& export HELM_VERSION=${HELM_VERSION} \
&& ./docker_build.sh
+ echo docker build --build-arg HELM_VERSION=3.0.2 -t vscoder/helm:v3.0.2 .
docker build --build-arg HELM_VERSION=3.0.2 -t vscoder/helm:v3.0.2 .
+ docker build --build-arg HELM_VERSION=3.0.2 -t vscoder/helm:v3.0.2 .
Sending build context to Docker daemon 10.24kB
Step 1/4 : FROM alpine:3
 ---> cc0abc535e36
Step 2/4 : ARG HELM_VERSION
 ---> Using cache
 ---> eb3418f75466
Step 3/4 : RUN apk add --update --no-cache openssl curl tar gzip bash ca-certificates git && wget -q -O /etc/apk/keys/sgerrand.rsa.pub https://alpine-pkgs.sgerrand.com/sgerrand.rsa.pub && wget https://github.com/sgerrand/alpine-pkg-glibc/releases/download/2. 23-r3/glibc-2.23-r3.apk && apk add glibc-2.23-r3.apk && curl https://storage.googleapis.com/pub/gsutil.tar.gz | tar -xz -C $HOME && export PATH=${PATH}:$HOME/gsutil && curl https://get.helm.sh/helm-v${HELM_VERSION}-linux-amd64.tar. gz | tar zx && mv linux-amd64/helm /usr/bin/ && helm version --client && curl -o /usr/bin/sync-repo.sh https://raw.githubusercontent.com/kubernetes/helm/master/scripts/sync-repo.sh && chmod a+x /usr/bin/sync-repo.sh && curl -L -o /usr/bin/kubectl https://storage.googleapis. com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl && chmod +x /usr/bin/kubectl && kubectl version --client && rm -rf linux-amd64 && apk del curl tar gzip && rm -f /var/cache/apk/*.
 ---> Using cache
 ---> 2bff76f532a9
Step 4/4 : CMD ["bash"]
 ---> Using cache
 ---> 4d5ef4d1bfe0
Successfully built 4d5ef4d1bfe0
Successfully tagged vscoder/helm:v3.0.2
. ./env \
&& export HELM_VERSION=${HELM_VERSION} \
&& ./docker_push.sh
+ docker push vscoder/helm:v3.0.2
The push refers to repository [docker.io/vscoder/helm].
63373a9367f2: Pushed 
6b27de954cca: Layer already exists 
v3.0.2: digest: sha256:8e0512402256b17834c6cdf920fe4c688a3a9600aed3d893fb6990e257be2df1 size: 740
```

Let's change the Pipeline accordingly.
`post/.gitlab-ci.yml`
``Yaml
---
image: vscoder/helm:v3.0.2

stages:
  - build
  - test
  - review
  - release
  - cleanup

build:
  stage: build
  Only:
    -
  image: docker:git
  Services:
    - docker:18.09.7-dind
  It's not:
    DOCKER_DRIVER: overlay2
    CI_REGISTRY: "index.docker.io."
    CI_APPLICATION_REPOSITORY: $CI_REGISTRY/$CI_PROJECT_PATH
    CI_APPLICATION_TAG: $CI_COMMIT_REF_SLUG
    CI_CONTAINER_NAME: ci_job_build_${CI_JOB_ID}
  before_script:
    - >
      if ! docker info &>/dev/null; then
        if [ -z "$DOCKER_HOST" -a "$KUBERNETES_PORT" ]; then
          export DOCKER_HOST='tcp://localhost:2375'.
        fi
      fi
  script:
    # Building
    - "Building Dockerfile-based application..."
    - echo `git show --format="%h" HEAD | head -1` > build_info.txt
    - echo `git rev-parse --abbrev-ref HEAD` >> build_info.txt.
    - docker build -t "$CI_APPLICATION_REPOSITORY:$CI_APPLICATION_TAG" .
    - >
      if [[ -n "$CI_REGISTRY_USER" ]]; then
        "Logging to GitLab Container Registry with CI credentials...for construction"
        docker login -u "$CI_REGISTRY_USER" -p "$CI_REGISTRY_PASSWORD"
      fi
    - "Pushing to GitLab Container Registry..."
    - docker push "$CI_APPLICATION_REPOSITORY:$CI_APPLICATION_TAG"

Test:
  stage: test
  script:
    - exit 0
  Only:
    -

release:
  stage: release
  image: docker
  Services:
    - docker:18.09.7-dind
  It's not:
    CI_REGISTRY: "index.docker.io."
    CI_APPLICATION_REPOSITORY: $CI_REGISTRY/$CI_PROJECT_PATH
    CI_APPLICATION_TAG: $CI_COMMIT_REF_SLUG
    CI_CONTAINER_NAME: ci_job_build_${CI_JOB_ID}
  before_script:
    - >
      if ! docker info &>/dev/null; then
        if [ -z "$DOCKER_HOST" -a "$KUBERNETES_PORT" ]; then
          export DOCKER_HOST='tcp://localhost:2375'.
        fi
      fi
  script:
    # Releasing
    - "Updating docker images..."
    - >
      if [[ -n "$CI_REGISTRY_USER" ]]; then
        "Logging to GitLab Container Registry with CI credentials for release..."
        docker login -u "$CI_REGISTRY_USER" -p "$CI_REGISTRY_PASSWORD".
      fi
    - docker pull "$CI_APPLICATION_REPOSITORY:$CI_APPLICATION_TAG".
    - docker tag "$CI_APPLICATION_REPOSITORY:$CI_APPLICATION_TAG" "$CI_APPLICATION_REPOSITORY:$(cat VERSION)".
    - docker push "$CI_APPLICATION_REPOSITORY:$(cat VERSION)"
    # latest is neede for feature flags
    - docker tag "$CI_APPLICATION_REPOSITORY:$CI_APPLICATION_TAG" "$CI_APPLICATION_REPOSITORY:latest".
    - docker push "$CI_APPLICATION_REPOSITORY:latest"
  Only:
    - master

review:
  stage: review
  Oh:
    KUBE_NAMESPACE: review
    host: $CI_PROJECT_PATH_SLUG-$CI_COMMIT_REF_SLUG
    CI_APPLICATION_TAG: $CI_COMMIT_REF_SLUG
    name: $CI_ENVIRONMENT_SLUG
  Environment:
    name: review/$CI_PROJECT_PATH/$CI_COMMIT_REF_NAME
    url: http://$CI_PROJECT_PATH_SLUG-$CI_COMMIT_REF_SLUG
    on_stop: stop_review
  Only:
    refs:
      - branches
    kubernetes: active
  except:
    - master
  before_script:
    # - helm init --client-only
    # - helm plugin install https://github.com/rimusz/helm-tiller
    - helm version --client
    - kubectl version --client
    # providing namespace
    - kubectl describe namespace "$KUBE_NAMESPACE" || kubectl create namespace "$KUBE_NAMESPACE"
  script:
    - export track="${1-stable}"
    - >
      if [["$track" != "stable" ]]; then.
        name="$name-$track"
      fi
    - "Clone deploy repository..."
    - git clone http://gitlab-gitlab/$CI_PROJECT_NAMESPACE/reddit-deploy.git
    - "Download helm dependencies..."
    - helm dep update reddit-deploy/reddit # removed the use of tiller plugin
    - echo "Deploy helm release $name to $KUBE_NAMESPACE"
    - "Upgrading existing release..."
    - echo "helm upgrade --install --wait --set ui.ingress.host="$host" --set $CI_PROJECT_NAME.image.tag="$CI_APPLICATION_TAG" --namespace="$KUBE_NAMESPACE" --version="$CI_PIPELINE_ID-$CI_JOB_ID" "$name" reddit-deploy/reddit/".
    - > # removed the use of tiller plugin
      helm upgrade \
        "$name" \
        reddit-deploy/reddit/ \
        --install \
        --wait \
        -set ui.ingress.host="$host" \.
        -set $CI_PROJECT_NAME.image.tag="$CI_APPLICATION_TAG" \.
        --namespace="$KUBE_NAMESPACE" \.
        --version="$CI_PIPELINE_ID-$CI_JOB_ID".

stop_review:
  stage: cleanup
  It's not:
    GIT_STRATEGY: none
    name: $CI_ENVIRONMENT_SLUG
  Environment:
    name: review/$CI_PROJECT_PATH/$CI_COMMIT_REF_NAME
    action: stop
  when: manual
  allow_failure: true
  Only:
    refs:
      - branches
    kubernetes: active
  except:
    - master
  before_script:
    # - helm init --client-only
    # - helm plugin install https://github.com/rimusz/helm-tiller
    - helm version --client
    - kubectl version --client
  script:
    - helm delete "$name" # removed the use of tiller plugin. Also, helm3 can't use the --purge flag.
```

Pipeline worked successfully (yes, not the first time ^_^ )
``log
helm upgrade --install --wait --set ui.ingress.host=vscoder-post-feature-4 --set post.image.tag=feature-4 --namespace=review --version=15-66 review-vscoder-po-7fbjm5 reddit-deploy/reddit/.
$ helm upgrade \ # collapsed multi-line command
Release "review-vscoder-po-7fbjm5" does not exist. Installing it now.
NAME: review-vscoder-po-7fbjm5.
LAST DEPLOYED: Wed Jan 15 19:02:38 2020
NAMESPACE: review
STATUS: deployed
REVISION: 1
TEST SUITE: None
Job succeeded
```

Environment checked out. It's working.

Removal didn't work. Cause: old base image
``log
Running with gitlab-runner 10.3.0 (5cf5e19a)
  on gitlab-gitlab-runner-875586966-psz7q (0562f0e5)
Using Kubernetes namespace: default
Using Kubernetes executor with image vscoder/helm:v3.0.2 ...
Waiting for pod default/runner-0562f0e5-project-1-concurrent-0bgb74 to be running, status is Pending
Waiting for pod default/runner-0562f0e5-project-1-concurrent-0bgb74 to be running, status is Pending
Waiting for pod default/runner-0562f0e5-project-1-concurrent-0bgb74 to be running, status is Pending
Running on runner-0562f0e5-project-1-concurrent-0bgb74 via gitlab-gitlab-runner-8755586966-psz7q...
Skipping Git repository setup
Skippping Git checkout
Skipping Git submodules setup
$ helm version --client
Client: &version.Version{SemVer: "v2.13.1", GitCommit: "618447cbf203d147601b4b9bd7f8c37a5d39fb4", GitTreeState: "clean"}.
$ kubectl version --client
Client Version: version.Info{Major: "1", Minor: "17", GitVersion: "v1.17. 0", GitCommit: "70132b0f130acc0bed193d9ba59dd186f0e634cf", GitTreeState: "clean", BuildDate: "2019-12-07T21:20:10Z", GoVersion: "go1.13.4", Compiler: "gc", Platform: "linux/amd64".}
$ helm delete "$name" --purge
Error: release: "review-vscoder-po-7fbjm5" not found
ERROR: Job failed: error executing remote command: command terminated with non-zero exit code: Error executing in Docker Container: 1
```

Useful link for gitlab cache theme https://docs.gitlab.com/ce/ci/caching/.

Executed on all 3 nodes of the Cube `sudo docker image rm vscoder/helm:v3.0.2 `.


Shot with his hands under the early, the cube re-created it. In Gitlab, a new ranner is registered.

But! There's a problem. Some of the piplines aren't working out:
``log.
Running with gitlab-runner 10.3.0 (5cf5e19a)
  on gitlab-gitlab-runner-875586966-94clb (d2450449)
Using Kubernetes namespace: default
Using Kubernetes executor with image vscoder/helm:v3.0.2 ...
Waiting for pod default/runner-d2450449-project-1-concurrent-0gjfkz to be running, status is Pending
Waiting for pod default/runner-d2450449-project-1-concurrent-0gjfkz to be running, status is Pending
Waiting for pod default/runner-d2450449-project-1-concurrent-0gjfkz to be running, status is Pending
Waiting for pod default/runner-d2450449-project-1-concurrent-0gjfkz to be running, status is Pending
Waiting for pod default/runner-d2450449-project-1-concurrent-0gjfkz to be running, status is Pending
Waiting for pod default/runner-d2450449-project-1-concurrent-0gjfkz to be running, status is Pending
Waiting for pod default/runner-d2450449-project-1-concurrent-0gjfkz to be running, status is Pending
Waiting for pod default/runner-d2450449-project-1-concurrent-0gjfkz to be running, status is Pending
Waiting for pod default/runner-d2450449-project-1-concurrent-0gjfkz to be running, status is Pending
... # And at the end
ERROR: Job failed (system failure): timedout waiting for pod to start
```

Checked which node ran under: `kubectl get pods` `kubectl describe pod runner-d2450449-project-1-concurrent-0gjfkz `

_gke-reddit-public-main-pool-a1c843ac-kj9h_

The restart was a success.

It's a new brand: Same problem again. Noda `gke-reddit-public-main-pool-a1c843ac-td4d/`
 
There's also an early fall
``shell
kubectl get pods                                                
```
``log
NAME READY STATUS RESTARTS AGE
gitlab-gitlab-766445f7d7-72cl4 1/1 Running 0 23h
gitlab-gitlab-postgresql-66d5b899b8-grfbz 1/1 Running 0 23h
gitlab-gitlab-redis-6c675dd568-b5svr 1/1 Running 0 23h
gitlab-gitlab-runner-875586966-94clb 0/1 Running 0 24m
runner-d2450449-project-1-concurrent-0hp6m7 0/3 Pending 0 2m41s
```
``shell
kubectl describe pod gitlab-gitlab-runner-875586966-94clb
```
``log
Name: gitlab-gitlab-runner-875586966-94clb
Namespace: default
Priority: 0
Node: gke-reddit-public-main-pool-a1c843ac-td4d/10.3.0.12
Start Time: Wed, 15 Jan 2020 22:27:06 +0300
Labels: app=gitlab-gitlab-runner
                pod-template-hash=875586966
Annotations: checksum/configmap: 9881f87576bd484ffb2801f6abf1b90cd637d2a61c44e01b5fbc639d206ddfac
                2bb41baa011e9685826ef270dc14a2c5d51f791686bd9196c26b3df16da95a6f
                cni.projectcalico.org/podIP: 10.4.2.17/32
                kubernetes.io/limit-ranger: LimitRanger plugin set: cpu request for container gitlab-gitlab-runner
Status:         Running
IP: 10.4.2.17
IPs:            <none>
Controlled By:  ReplicaSet/gitlab-gitlab-runner-875586966
Containers:
  gitlab-gitlab-runner:
    Container ID: docker://26cf3fe8bfdecc0cfa7d87127c0ce98a8ee43491244d990b35b25678239dd868
    Image: gitlab/gitlab-runner:alpine-v10.3.0
    Image ID: docker-pullable://gitlab/gitlab-runner@sha256:9b1e53a91fc8914c934b9eacf93365c7af97d97514c71b1825f67c8ee2a2369
    Port:          <none>
    Host Port:     <none>
    Command:
      /pin/bash
      /scripts/entrypoint
    State:          Running
      Started:      Wed, 15 Jan 2020 22:28:52 +0300
    Ready:          False
    Restart Count:  0
    Requests:
      cpu: 100m
    Liveness: exec [/usr/bin/pgrep gitlab.*runner] delay=60s timeout=1s period=10s #success=1 #failure=3.
    Readiness: exec [/usr/bin/pgrep gitlab.*runner] delay=10s timeout=1s period=10s #success=1 #failure=3.
    Environment:
      CI_SERVER_URL: http://gitlab-gitlab.default:8005/
      CI_SERVER_TOKEN: <set to the key 'runner-token' in secret 'gitlab-gitlab-runner'> Optional: false
      REGISTRATION_TOKEN: <set to the key 'runner-registration-token' in secret 'gitlab-gitlab-runner'> Optional: false.
      KUBERNETES_IMAGE: ubuntu:16.04
      KUBERNETES_PRIVILEGED: true
      KUBERNETES_NAMESPACE: default
      KUBERNETES_CPU_LIMIT:               
      KUBERNETES_MEMORY_LIMIT:            
      KUBERNETES_CPU_REQUEST:             
      KUBERNETES_MEMORY_REQUEST: KUBERNETES_MEMORY_REQUEST:          
      KUBERNETES_SERVICE_CPU_LIMIT: KUBERNETES_CPU_LIMIT:       
      KUBERNETES_SERVICE_MEMORY_LIMIT: KUBERNETES_SERVICE_CPU_LIMIT:    
      KUBERNETES_SERVICE_CPU_REQUEST: KUBERNETES_SERVICE_CPU_REQUEST:     
      KUBERNETES_SERVICE_MEMORY_REQUEST: KUBERNETES_SERVICE_SERVICE_CPU_REQUEST:  
      KUBERNETES_HELPERS_CPU_LIMIT:       
      KUBERNETES_HELPERS_MEMORY_LIMIT:    
      KUBERNETES_HELPERS_CPU_REQUEST: KUBERNETES_HELPERS_CPU_REQUEST:     
      KUBERNETES_HELPERS_MEMORY_REQUEST:  
    Mounts:
      /scripts from scripts (rw)
      /var/run/secrets/kubernetes.io/serviceaccount from default-token-l84tq (ro)
Conditions:
  Type Status
  Initialized True 
  Ready False 
  ContainersReady False 
  PodScheduled True 
Volumes:
  var-run-docker-sock:
    Type:          HostPath (bare host directory volume)
    Path:          /var/run/docker.sock
    HostPathType:  
  scripts:
    Type:      ConfigMap (a volume populated by a ConfigMap)
    Name: gitlab-gitlab-runner
    Optional: false
  default-token-l84tq:
    Type:        Secret (a volume populated by a Secret)
    SecretName: default-token-l84tq
    Optional: false
QoS Class:       Burstable
Node-Selectors:  <none>
Tolerations: node.kubernetes.io/not-ready:NoExecute for 300s
                 node.kubernetes.io/unreachable:NoExecute for 300s
Events:
  Type Reason Age From Message
  ---- ------ ---- ---- -------
  Normal Scheduled 25m default-scheduler Successfully assigned default/gitlab-gitlab-runner-875586966-94clb to gke-reddit-public-main-pool-a1c843ac-td4d
  Normal Pulling 25m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Pulling image "gitlab/gitlab-runner:alpine-v10.3.0".
  Normal Pulled 23m kubelet, gke-reddit-public-main-pool-a1c8443ac-td4d Successfully pulled image "gitlab/gitlab-runner:alpine-v10.3.0".
  Normal Created 23m kubelet, gke-reddit-public-main-pool-a1c8443ac-td4d Created container gitlab-gitlab-runner.
  Normal Started 23m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Started container gitlab-gitlab-runner
  Warning FailedMount 8m56s kubelet, gke-reddit-public-main-pool-a1c843ac-td4d MountVolume.SetUp failed for volume "default-token-l84tq" : couldn't propagate object cache: timed out waiting for the condition
  Warning FailedMount 8m56s kubelet, gke-reddit-public-main-pool-a1c843ac-td4d MountVolume.SetUp failed for volume "scripts" : couldn't propagate object cache: timed out waiting for the condition
  Warning FailedMount 5m53s kubelet, gke-reddit-public-main-pool-a1c843ac-td4d MountVolume.SetUp failed for volume "scripts" : couldn't propagate object cache: timed out waiting for the condition
  Warning FailedMount 5m53s kubelet, gke-reddit-public-main-pool-a1c843ac-td4d MountVolume.SetUp failed for volume "default-token-l84tq" : couldn't propagate object cache: timed out waiting for the condition
  ```

That's weird. The rerun of the Pipeline task helped, but the Hitlabrunner is still "lying"
``shell
kubectl get pods                                                
```
``log
NAME READY STATUS RESTARTS AGE
gitlab-gitlab-766445f7d7-72cl4 1/1 Running 0 23h
gitlab-gitlab-postgresql-66d5b899b8-grfbz 1/1 Running 0 23h
gitlab-gitlab-redis-6c675dd568-b5svr 1/1 Running 0 23h
gitlab-gitlab-runner-875586966-94clb 0/1 Running 0 29m
runner-d2450449-project-1-concurrent-0bkvlp 3/3 Running 0 52s
```

After a while, there was another ranner
``log
kubectl get pods
NAME READY STATUS RESTARTS AGE
gitlab-gitlab-766445f7d7-72cl4 1/1 Running 0 23h
gitlab-gitlab-postgresql-66d5b899b8-grfbz 1/1 Running 0 23h
gitlab-gitlab-redis-6c675dd568-b5svr 1/1 Running 0 23h
gitlab-gitlab-runner-875586966-94clb 0/1 Unknown 0 36m
gitlab-gitlab-runner-875586966-qktll 1/1 Running 0 5m24s
runner-d2450449-project-1-concurrent-0bkvlp 3/3 Running 0 7m43s
```

But our assembly has been hanging on
``log
...
(14/17) Installing gcc (5.3.0-r0)
(15/17) Installing musl-dev (1.1.14-r16)
(16/17) Installing .build-deps (0)
(17/17) Upgrading musl-utils (1.1.14-r14 -> 1.1.14-r16)
Executing busybox-1.24.2-r13.trigger
OK: 117 MiB in 48 packages
Collecting prometheus_client==0.0.21 (from -r /app/requirements.txt (line 1))
  Downloading https://files.pythonhosted.org/packages/45/6d/0cc171ce82a8f284133faf12a50018501abdc4b0742e4f8f471b6b2dc81f/prometheus_client-0.0.21.tar.gz
```

I'll restart the Pipeline with my hands ^_^. Let's have a look at the result)))

While the case is moving...

All stages, including the review, have been successful! Encirclement available at http://vscoder-post-feature-10/.

But deleting the release does not work((
``log
Running with gitlab-runner 10.3.0 (5cf5e19a)
  on gitlab-gitlab-runner-875586966-qktll (d0b36d07)
Using Kubernetes namespace: default
Using Kubernetes executor with image vscoder/helm:v3.0.2 ...
Waiting for pod default/runner-d0b36d07-project-1-concurrent-086wv8 to be running, status is Pending
Running on runner-d0b36d07-project-1-concurrent-086wv8 via gitlab-gitlab-runner-875586966-qktll...
Skipping Git repository setup
Skippping Git checkout
Skipping Git submodules setup
$ helm version --client
version.BuildInfo{Version: "v3.0.2", GitCommit: "19e47ee3283ae98139d98460de796c1be1e3975f", GitTreeState: "clean", GoVersion: "go1.13.5" }.
$ kubectl version --client
Client Version: version.Info{Major: "1", Minor: "17", GitVersion: "v1.17. 1", GitCommit: "d224476cd0730baca2b6e357d144171ed74192d6", GitTreeState: "clean", BuildDate: "2020-01-14T21:04:32Z", GoVersion: "go1.13.5", Compiler: "gc", Platform: "linux/amd64".}
$ helm delete "$name"
Error: uninstall: Release not loaded: review-vscoder-po-zthnmc: release: not found
ERROR: Job failed: error executing remote command: command terminated with non-zero exit code: Error executing in Docker Container: 1
```

Q: Where does helm3 keep the release list? In a local directory? Gets it from the cube?

But here's another strange thing: the node is recreated once again.
``shell
kubectl get nodes
```
``log
NAME STATUS ROLES AGE VERSION
gke-reddit-public-gitlab-pool-3b2988e5-mx8f Ready <none> 3h16m v1.15.7-gke.2
gke-reddit-public-main-pool-a1c843ac-kj9h Ready <none> 24m v1.15.7-gke.2
gke-reddit-public-main-pool-a1c843ac-td4d NotReady <none> 11m v1.15.7-gke.2
```
``shell
kubectl describe node gke-reddit-public-main-pool-a1c843ac-td4d
Name: gke-reddit-public-main-pool-a1c843ac-td4d
Roles:              <none>
Labels: all-pools-example=true
                    beta.kubernetes.io/arch=amd64
                    beta.kubernetes.io/fluentd-ds-ready=true
                    beta.kubernetes.io/instance-type=g1-small
                    beta.kubernetes.io/masq-agent-ds-ready=true
                    beta.kubernetes.io/os=linux
                    cloud.google.com/gke-nodepool=main-pool
                    cloud.google.com/gke-os-distribution=cos
                    failure-domain.beta.kubernetes.io/region=us-central1
                    failure-domain.beta.kubernetes.io/zone=us-central1-a
                    kubernetes.io/arch=amd64
                    kubernetes.io/hostname=gke-reddit-public-main-pool-a1c843ac-td4d
                    kubernetes.io/os=linux
                    node.kubernetes.io/masq-agent-ds-ready=true
                    projectcalico.org/ds-ready=true
Annotations: container.googleapis.com/instance_id: 5153271999223746451
                    node.alpha.kubernetes.io/ttl: 0
                    projectcalico.org/IPv4IPTunnelAddr: 10.4.2.1
                    kubernetes.io/controller-managed-attach-detach: true
CreationTimestamp:  Wed, 15 Jan 2020 23:10:18 +0300
Taints:             ToBeDeletedByClusterAutoscaler=1579119624:NoSchedule
                    node.kubernetes.io/unreachable:NoSchedule
                    DeletionCandidateOfClusterAutoscaler=1579119021:PreferNoSchedule
Unschedulable: false
Lease:
  HolderIdentity: gke-reddit-public-main-pool-a1c843ac-td4d
  AcquireTime:     <unset>
  RenewTime: Wed, 15 Jan 2020 23:20:29 +0300
Conditions:
  Type Status LastHeartbeatTime LastTransitionTime Reason Message
  

  CorruptDockerOverlay2 False Wed, 15 Jan 2020 23:20:25 +0300 Wed, 15 Jan 2020 23:10:18 +0300 NoCorruptDockerOverlay2 docker overlay2 is functioning properly
  FrequentUnregisterNetDevice False Wed, 15 Jan 2020 23:20:25 +0300 Wed, 15 Jan 2020 23:10:18 +0300 NoFrequentUnregisterNetDevice node is functioning properly
  FrequentKubeletRestart False Wed, 15 Jan 2020 23:20:25 +0300 Wed, 15 Jan 2020 23:10:18 +0300 NoFrequentKubeletRestart kubelet is functioning properly
  FrequentDockerRestart False Wed, 15 Jan 2020 23:20:25 +0300 Wed, 15 Jan 2020 23:10:18 +0300 NoFrequentDockerRestart docker is functioning properly
  FrequentContainerdRestart False Wed, 15 Jan 2020 23:20:25 +0300 Wed, 15 Jan 2020 23:10:18 +0300 NoFrequentContainerdRestart containerd is functioning properly
  KernelDeadlock False Wed, 15 Jan 2020 23:20:25 +0300 Wed, 15 Jan 2020 23:10:18 +0300 KernelHasNoDeadlock kernel has no deadlock
  ReadonlyFilesystem False Wed, 15 Jan 2020 23:20:25 +0300 Wed, 15 Jan 2020 23:10:18 +0300 FilesystemIsNotReadOnly Filesystem is not read-only
  NetworkUnavailable False Wed, 15 Jan 2020 23:10:19 +0300 Wed, 15 Jan 2020 23:10:19 +0300 RouteCreated NodeController create implicit route
  MemoryPressure Unknown Wed, 15 Jan 2020 23:20:21 +0300 Wed, 15 Jan 2020 23:21:13 +0300 NodeStatusUnknown Kubelet stopped posting node status.
  DiskPressure Unknown Wed, 15 Jan 2020 23:20:21 +0300 Wed, 15 Jan 2020 23:21:13 +0300 NodeStatusUnknown Kubelet stopped posting node status.
  PIDPressure Unknown Wed, 15 Jan 2020 23:20:21 +0300 Wed, 15 Jan 2020 23:21:13 +0300 NodeStatusUnknown Kubelet stopped posting node status.
  Ready Unknown Wed, 15 Jan 2020 23:20:21 +0300 Wed, 15 Jan 2020 23:21:13 +0300 NodeStatusUnknown Kubelet stopped posting node status.
Addresses:
  InternalIP: 10.3.0.16
  ExternalIP: 35.202.167.185
  InternalDNS: gke-reddit-public-main-pool-a1c843ac-td4d.us-central1-a.c.docker-257914.internal
  Hostname: gke-reddit-public-main-pool-a1c843ac-td4d.us-central1-a.c.docker-257914.internal
Capacity:
  attachable-volumes-gce-pd: 15
  cpu: 1
  ephemeral-storage: 26615568Ki
  hugepages-2Mi: 0
  memory: 1732780Ki
  pods: 110
Allocatable:
  attachable-volumes-gce-pd: 15
  cpu: 940m
  ephemeral-storage: 8422780069
  hugepages-2Mi: 0
  memory: 1184940Ki
  pods: 110
System Info:
  Machine ID: f417f94ad5bed3d2924f39b8bb9a7c07
  System UUID: f417f94a-d5be-d3d2-924f-39b8b9a7c07
  Boot ID: c05f745c-8ec0-4ede-b5a9-71beabe87aa5
  Kernel Version:             4.19.76+
  OS Image:                   Container-Optimized OS from Google
  Operating System: linux
  Architecture: amd64
  Container Runtime Version: docker://19.3.1
  Kubelet Version: v1.15.7-gke.2
  Kube-Proxy Version: v1.15.7-gke.2
PodCIDR: 10.4.2.0/24
ProviderID: gce://docker-257914/us-central1-a/gke-reddit-public-main-pool-a1c843ac-td4d
Non-terminated Pods:          (6 in total)
  Namespace Name CPU Requests CPU Memory Requests Memory Limits AGE
  

  kube-system calico-node-x7vv5 100m (10%) 0 (0%) 0 (0%) 0 (0%) 11m
  kube-system fluentd-gcp-v3.1.1-fkn56 100m (10%) 1 (106%) 200Mi (17%) 500Mi (43%) 11m
  kube-system ip-masq-agent-85596 10m (1%) 0 (0%) 16Mi (1%) 0 (0%) 11m
  kube-system kube-proxy-gke-reddit-public-main-pool-a1c843ac-td4d 100m (10%) 0 (0%) 0 (0%) 0 (0%) 11m
  kube-system prometheus-to-sd-4ndfz 1m (0%) 3m (0%) 20Mi (1%) 20Mi (1%) 11m
  nginx-ingress nginx-46fr5 0 (0%) 0 (0%) 0 (0%) 0 (0%) 11m
Allocated resources:
  (Total limits may be over 100 percent, i.e., overcommitted.)
  Resource Requests Limits
  -------- -------- ------
  cpu 311m (33%) 1003m (106%)
  236Mi (20%) 520Mi (44%)
  ephemeral-storage 0 (0%) 0 (0%)
  attachable-volumes-gce-pd 0 0
Events:
  Type Reason Age From Message
  ---- ------ ---- ---- -------
  Normal Starting 47m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Starting kubelet.
  Normal NodeHasSufficientMemory 47m (x2 over 47m) kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeHasSufficientMemory
  Normal NodeHasNoDiskPressure 47m (x2 over 47m) kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeHasNoDiskPressure
  Normal NodeHasSufficientPID 47m (x2 over 47m) kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeHasSufficientPID
  Normal NodeNotReady 47m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeNotReady
  Normal NodeReady 47m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeReady
  Normal NodeAllocatableEnforced 47m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Updated Node Allocatable limit across pods
  Normal Starting 44m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Starting kubelet.
  Normal NodeNotReady 44m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeNotReady
  Normal NodeHasSufficientMemory 44m (x2 over 44m) kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeHasSufficientMemory
  Normal NodeHasNoDiskPressure 44m (x2 over 44m) kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeHasNoDiskPressure
  Normal NodeHasSufficientPID 44m (x2 over 44m) kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeHasSufficientPID
  Normal NodeAllocatableEnforced 44m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Updated Node Allocatable limit across pods
  Normal NodeReady 44m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeReady
  Normal Starting 43m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Starting kubelet.
  Normal NodeHasSufficientMemory 43m (x2 over 43m) kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeHasSufficientMemory
  Normal NodeHasNoDiskPressure 43m (x2 over 43m) kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeHasNoDiskPressure
  Normal NodeHasSufficientPID 43m (x2 over 43m) kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeHasSufficientPID
  Normal NodeNotReady 43m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeNotReady
  Normal NodeAllocatableEnforced 43m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Updated Node Allocatable limit across pods
  Normal NodeReady 43m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeReady
  Normal Starting 41m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Starting kubelet.
  Normal NodeHasSufficientMemory 41m (x2 over 41m) kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeHasSufficientMemory
  Normal NodeHasNoDiskPressure 41m (x2 over 41m) kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeHasNoDiskPressure
  Normal NodeHasSufficientPID 41m (x2 over 41m) kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeHasSufficientPID
  Normal NodeAllocatableEnforced 41m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Updated Node Allocatable limit across pods
  Normal NodeNotReady 40m (x2 over 41m) kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeNotReady
  Normal NodeReady 40m (x2 over 41m) kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeReady
  Normal Starting 38m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Starting kubelet.
  Normal NodeHasSufficientMemory 38m (x2 over 38m) kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeHasSufficientMemory
  Normal NodeNotReady 38m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeNotReady
  Normal NodeHasSufficientPID 38m (x2 over 38m) kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeHasSufficientPID
  Normal NodeHasNoDiskPressure 38m (x2 over 38m) kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeHasNoDiskPressure
  Normal NodeAllocatableEnforced 38m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Updated Node Allocatable limit across pods
  Normal NodeReady 38m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeReady
  Normal Starting 36m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Starting kubelet.
  Normal NodeHasSufficientMemory 36m (x2 over 36m) kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeHasSufficientMemory
  Normal NodeHasNoDiskPressure 36m (x2 over 36m) kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeHasNoDiskPressure
  Normal NodeHasSufficientPID 36m (x2 over 36m) kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeHasSufficientPID
  Normal NodeNotReady 36m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeNotReady
  Normal NodeReady 36m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeReady
  Normal NodeAllocatableEnforced 36m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Updated Node Allocatable limit across pods
  Normal Starting 35m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Starting kubelet.
  Normal NodeHasSufficientMemory 35m (x2 over 35m) kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeHasSufficientMemory
  Normal NodeHasNoDiskPressure 35m (x2 over 35m) kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeHasNoDiskPressure
  Normal NodeHasSufficientPID 35m (x2 over 35m) kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeHasSufficientPID
  Normal NodeNotReady 35m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeNotReady
  Normal NodeAllocatableEnforced 35m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Updated Node Allocatable limit across pods
  Normal NodeReady 35m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeReady
  Normal Starting 33m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Starting kubelet.
  Normal NodeNotReady 33m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeNotReady
  Normal NodeHasSufficientMemory 33m (x2 over 33m) kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeHasSufficientMemory
  Normal NodeHasNoDiskPressure 33m (x2 over 33m) kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeHasNoDiskPressure
  Normal NodeHasSufficientPID 33m (x2 over 33m) kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeHasSufficientPID
  Normal NodeReady 33m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeReady
  Normal NodeAllocatableEnforced 33m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Updated Node Allocatable limit across pods
  Normal Starting 32m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Starting kubelet.
  Normal NodeHasSufficientPID 32m (x2 over 32m) kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeHasSufficientPID
  Normal NodeHasSufficientMemory 32m (x2 over 32m) kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeHasSufficientMemory
  Normal NodeNotReady 32m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeNotReady
  Normal NodeHasNoDiskPressure 32m (x2 over 32m) kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeHasNoDiskPressure
  Normal NodeAllocatableEnforced 32m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Updated Node Allocatable limit across pods
  Normal NodeReady 31m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeReady
  Normal NoFrequentKubeletRestart 30m systemd-monitor, gke-reddit-public-main-pool-a1c843ac-td4d Node condition FrequentKubeletRestart is now: Unknown, reason: NoFrequentKubeletRestart .
  Normal NoFrequentUnregisterNetDevice 30m kernel-monitor, gke-reddit-public-main-pool-a1c843ac-td4d Node condition FrequentUnregisterNetDevice is now: Unknown, reason: NoFrequentUnregisterNetDevice .
  Normal Starting 28m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Starting kubelet.
  Normal NodeNotReady 28m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeNotReady
  Normal NodeHasSufficientMemory 28m (x2 over 28m) kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeHasSufficientMemory
  Normal NodeHasNoDiskPressure 28m (x2 over 28m) kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeHasNoDiskPressure
  Normal NodeHasSufficientPID 28m (x2 over 28m) kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeHasSufficientPID
  Normal NodeAllocatableEnforced 28m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Updated Node Allocatable limit across pods
  Normal NodeReady 28m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeReady
  Normal NoFrequentUnregisterNetDevice 25m kernel-monitor, gke-reddit-public-main-pool-a1c843ac-td4d Node condition FrequentUnregisterNetDevice is now: False, reason: NoFrequentUnregisterNetDevice .
  Normal FrequentKubeletRestart 25m (x2 over 36m) systemd-monitor, gke-reddit-public-main-pool-a1c843ac-td4d Node condition FrequentKubeletRestart is now: True, reason: FrequentKubeletRestart .
  Normal Starting 11m kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Starting kubelet.
  Normal NodeAllocatableEnforced 11m kubelet, gke-reddit-public-main-pool-a1c8443ac-td4d Updated Node Allocatable limit across pods
  Normal NodeHasNoDiskPressure 11m (x7 over 11m) kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeHasNoDiskPressure
  Normal NodeHasSufficientMemory 11m (x8 over 11m) kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeHasSufficientMemory
  Normal NodeHasSufficientPID 11m (x8 over 11m) kubelet, gke-reddit-public-main-pool-a1c843ac-td4d Node gke-reddit-public-main-pool-a1c843ac-td4d status is now: NodeHasSufficientPID
  Normal Starting 11m kube-proxy, gke-reddit-public-main-pool-a1c843ac-td4d Starting kube-proxy.
```

Eventually, GKE removed the node. But maybe he just needs a fatter node? ))

Replace `g1-small` with `n1-standard-1` for node pool main.

I did. Restarted the Pipeline. And Hitlab became `Evicted`.
``shell
kubectl get pods 
```
``log
NAME READY STATUS RESTARTS AGE
gitlab-gitlab-766445f7d7-72cl4 0/1 Evicted 0 24h
gitlab-gitlab-766445f7d7-7p2gd 0/1 Running 0 57s
gitlab-gitlab-postgresql-66d5b899b8-grfbz 1/1 Running 0 24h
gitlab-gitlab-redis-6c675dd568-b5svr 1/1 Running 0 24h
gitlab-gitlab-runner-875586966-ljkcn 1/1 Running 0 13m
runner-34e3fb54-project-1-concurrent-09r8gd 3/3 Running 0 2m
runner-d2450449-project-1-concurrent-0bkvlp 3/3 Running 0 55m
```

Our Hitlab ate all my memory...
``log
kubelet, gke-reddit-public-gitlab-pool-3b2988e5-mx8f The node was low on resource: memory. Container gitlab was using 2703536Ki, which exceeds its request of 0.
```

And the one created under the Hitlab was launched only the second time.

Once again, I've fixed the Pipeline
`post/.gitlab-ci.yml`
``Yaml
---
image: vscoder/helm:v3.0.2

stages:
  - build
  - test
  - review
  - release
  - cleanup

build:
  stage: build
  Only:
    -
  image: docker:git
  Services:
    - docker:18.09.7-dind
  It's not:
    DOCKER_DRIVER: overlay2
    CI_REGISTRY: "index.docker.io."
    CI_APPLICATION_REPOSITORY: $CI_REGISTRY/$CI_PROJECT_PATH
    CI_APPLICATION_TAG: $CI_COMMIT_REF_SLUG
    CI_CONTAINER_NAME: ci_job_build_${CI_JOB_ID}
  before_script:
    - >
      if ! docker info &>/dev/null; then
        if [ -z "$DOCKER_HOST" -a "$KUBERNETES_PORT" ]; then
          export DOCKER_HOST='tcp://localhost:2375'.
        fi
      fi
  script:
    # Building
    - "Building Dockerfile-based application..."
    - echo `git show --format="%h" HEAD | head -1` > build_info.txt
    - echo `git rev-parse --abbrev-ref HEAD` >> build_info.txt.
    - docker build -t "$CI_APPLICATION_REPOSITORY:$CI_APPLICATION_TAG" .
    - >
      if [[ -n "$CI_REGISTRY_USER" ]]; then
        "Logging to GitLab Container Registry with CI credentials...for construction"
        docker login -u "$CI_REGISTRY_USER" -p "$CI_REGISTRY_PASSWORD"
      fi
    - "Pushing to GitLab Container Registry..."
    - docker push "$CI_APPLICATION_REPOSITORY:$CI_APPLICATION_TAG"

Test:
  stage: test
  script:
    - exit 0
  Only:
    -

release:
  stage: release
  image: docker
  Services:
    - docker:18.09.7-dind
  It's not:
    CI_REGISTRY: "index.docker.io."
    CI_APPLICATION_REPOSITORY: $CI_REGISTRY/$CI_PROJECT_PATH
    CI_APPLICATION_TAG: $CI_COMMIT_REF_SLUG
    CI_CONTAINER_NAME: ci_job_build_${CI_JOB_ID}
  before_script:
    - >
      if ! docker info &>/dev/null; then
        if [ -z "$DOCKER_HOST" -a "$KUBERNETES_PORT" ]; then
          export DOCKER_HOST='tcp://localhost:2375'.
        fi
      fi
  script:
    # Releasing
    - "Updating docker images..."
    - >
      if [[ -n "$CI_REGISTRY_USER" ]]; then
        "Logging to GitLab Container Registry with CI credentials for release..."
        docker login -u "$CI_REGISTRY_USER" -p "$CI_REGISTRY_PASSWORD".
      fi
    - docker pull "$CI_APPLICATION_REPOSITORY:$CI_APPLICATION_TAG".
    - docker tag "$CI_APPLICATION_REPOSITORY:$CI_APPLICATION_TAG" "$CI_APPLICATION_REPOSITORY:$(cat VERSION)".
    - docker push "$CI_APPLICATION_REPOSITORY:$(cat VERSION)"
    # latest is neede for feature flags
    - docker tag "$CI_APPLICATION_REPOSITORY:$CI_APPLICATION_TAG" "$CI_APPLICATION_REPOSITORY:latest".
    - docker push "$CI_APPLICATION_REPOSITORY:latest"
  Only:
    - master

review:
  stage: review
  Oh:
    KUBE_NAMESPACE: review
    host: $CI_PROJECT_PATH_SLUG-$CI_COMMIT_REF_SLUG
    CI_APPLICATION_TAG: $CI_COMMIT_REF_SLUG
    name: $CI_ENVIRONMENT_SLUG
  Environment:
    name: review/$CI_PROJECT_PATH/$CI_COMMIT_REF_NAME
    url: http://$CI_PROJECT_PATH_SLUG-$CI_COMMIT_REF_SLUG
    on_stop: stop_review
  Only:
    refs:
      - branches
    kubernetes: active
  except:
    - master
  before_script:
    # - helm init --client-only
    # - helm plugin install https://github.com/rimusz/helm-tiller
    - helm version --client
    - kubectl version --client
    # providing namespace
    - kubectl describe namespace "$KUBE_NAMESPACE" || kubectl create namespace "$KUBE_NAMESPACE"
  script:
    - export track="${1-stable}"
    - >
      if [["$track" != "stable" ]]; then.
        name="$name-$track"
      fi
    - "Clone deploy repository..."
    - git clone http://gitlab-gitlab/$CI_PROJECT_NAMESPACE/reddit-deploy.git
    - "Download helm dependencies..."
    - helm dep update reddit-deploy/reddit
    - echo "Deploy helm release $name to $KUBE_NAMESPACE"
    - "Upgrading existing release..."
    - echo "helm upgrade --install --wait --set ui.ingress.host="$host" --set $CI_PROJECT_NAME.image.tag="$CI_APPLICATION_TAG" --namespace="$KUBE_NAMESPACE" --version="$CI_PIPELINE_ID-$CI_JOB_ID" "$name" reddit-deploy/reddit/".
    - >
      helm upgrade \
        "$name" \
        reddit-deploy/reddit/ \
        --install \
        --wait \
        -set ui.ingress.host="$host" \.
        -set $CI_PROJECT_NAME.image.tag="$CI_APPLICATION_TAG" \.
        --namespace="$KUBE_NAMESPACE" \.
        --version="$CI_PIPELINE_ID-$CI_JOB_ID".

stop_review:
  stage: cleanup
  It's not:
    KUBE_NAMESPACE: review # Added for transfer to --namespace
    GIT_STRATEGY: none
    name: $CI_ENVIRONMENT_SLUG
  Environment:
    name: review/$CI_PROJECT_PATH/$CI_COMMIT_REF_NAME
    action: stop
  when: manual
  allow_failure: true
  Only:
    refs:
      - branches
    kubernetes: active
  except:
    - master
  before_script:
    # - helm init --client-only
    # - helm plugin install https://github.com/rimusz/helm-tiller
    - helm version --client
    - kubectl version --client
  script:
    - helm delete "$name" --namespace="$KUBE_NAMESPACE" # Added --namespace
```

And now all stages, including the removal of the environment, have been successful! The availability of the environment has also been verified.


##### reddit-deploy

Repair the Pipeline for reddit-deploy (`reddit-deploy/.gitlab-ci.yml`) in the same way, getting rid of auto_devops.

**The old** option
``Yaml
---
image: alpine:latest

(Sighs)
  - test
  - staging
  - production

Test:
  stage: test
  script:
    - exit 0
  Only:
    -
    -

Staging:
  stage: staging
  script:
    - install_dependencies
    - ensure_namespace
    - install_tiller
    -
  It's not:
    KUBE_NAMESPACE: staging
  Environment:
    name: staging
    url: http://staging
  Only:
    refs:
      - master
    kubernetes: active

production:
  stage: production
  script:
    - install_dependencies
    - ensure_namespace
    - install_tiller
    -
  It's not:
    KUBE_NAMESPACE: production
  Environment:
    name: production
    url: http://production
  when: manual
  Only:
    refs:
      - master
    kubernetes: active

.auto_devops: &auto_devops |.
  # Auto DevOps and functions
  ["$TRACE" ] && set -x.
  export CI_REGISTRY="index.docker.io"
  export CI_APPLICATION_REPOSITORY=$CI_REGISTRY/$CI_PROJECT_PATH
  export CI_APPLICATION_TAG=$CI_COMMIT_REF_SLUG
  export CI_CONTAINER_NAME=ci_job_build_${CI_JOB_ID}
  export TILLER_NAMESPACE="kube-system"

  function deploy() {
    echo $KUBE_NAMESPACE
    track="${1-stable}"
    name="$CI_ENVIRONMENT_SLUG".
    helm dep build reddit

    # for microservice in $(helm dep ls | grep "file://" | awk '{print $1}') ; do
    # SET_VERSION="$SET_VERSION \ -set $microservice.image.tag='$(curl http://gitlab-gitlab/$CI_PROJECT_NAMESPACE/ui/raw/master/VERSION)''.

    helm upgrade --install \
      --wait \
      -set ui.ingress.host="$host" \.
      -set ui.image.tag="$(curl http://gitlab-gitlab/$CI_PROJECT_NAMESPACE/ui/raw/master/VERSION)". \
      -set post.image.tag="$(curl http://gitlab-gitlab/$CI_PROJECT_NAMESPACE/post/raw/master/VERSION)". \
      -set comment.image.tag="$(curl http://gitlab-gitlab/$CI_PROJECT_NAMESPACE/comment/raw/master/VERSION)". \
      --namespace="$KUBE_NAMESPACE" \.
      --version="$CI_PIPELINE_ID-$CI_JOB_ID" \.
      "$name" \
      reddit
  }

  function install_dependencies() {

    apk add -U openssl curl tar gzip bash ca-certificates git
    wget -q -O /etc/apk/keys/sgerrand.rsa.pub https://alpine-pkgs.sgerrand.com/sgerrand.rsa.pub.
    wget https://github.com/sgerrand/alpine-pkg-glibc/releases/download/2.23-r3/glibc-2.23-r3.apk
    apk add glibc-2.23-r3.apk
    rm glibc-2.23-r3.apk

    curl https://kubernetes-helm.storage.googleapis.com/helm-v2.13.1-linux-amd64.tar.gz | tar zx

    mv linux-amd64/helm /usr/bin/
    helm version --client

    curl -L -o /usr/bin/kubectl https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl
    chmod +x /usr/bin/kubectl
    kubectl version --client
  }

  function ensure_namespace() {
    kubectl describe namespace "$KUBE_NAMESPACE" || kubectl create namespace "$KUBE_NAMESPACE"
  }

  function install_tiller() {
    "Checking Tiller..."
    helm init --upgrade
    kubectl rollout status -n "$TILLER_NAMESPACE" -w "deployment/tiller-deploy"
    if ! helm version --debug; then
      "Failed to init Tiller."
      return one.
    fi
    echo ""
  }

  function delete() {
    track="${1-stable}"
    name="$CI_ENVIRONMENT_SLUG".
    helm delete "$name" || true
  }

before_script:
  - *auto_devops
```

**New** version modified according to the task
``Yaml
---
---
image: vscoder/helm:v3.0.2

stages:
  - test
  - staging
  - production

Test:
  stage: test
  script:
    - exit 0
  Only:
    -
    -

Staging:
  stage: staging
  It's not:
    KUBE_NAMESPACE: staging
    name: $CI_ENVIRONMENT_SLUG
  before_script:
    - helm version --client
    - kubectl version --client
    - kubectl describe namespace "$KUBE_NAMESPACE" || kubectl create namespace "$KUBE_NAMESPACE"
  script:
    - echo KUBE_NAMESPACE=$KUBE_NAMESPACE
    - export track="${1-stable}"
    - "Download helm dependencies..."
    - helm dep update reddit
    - >
      # for microservice in $(helm dep ls | grep "file://" | awk '{print $1}') ; do
      # SET_VERSION="$SET_VERSION \ -set $microservice.image.tag='$(curl http://gitlab-gitlab/$CI_PROJECT_NAMESPACE/ui/raw/master/VERSION)''.
    - >
      echo helm upgrade --install --wait --set ui.ingress.host="$host" --set ui.image.tag="$(curl http://gitlab-gitlab/$CI_PROJECT_NAMESPACE/ui/raw/master/VERSION)" --set post.image. tag="$(curl http://gitlab-gitlab/$CI_PROJECT_NAMESPACE/post/raw/master/VERSION)" -set comment.image.tag="$(curl http://gitlab-gitlab/$CI_PROJECT_NAMESPACE/comment/raw/master/VERSION)" --namespace="$KUBE_NAMESPACE" --version="$CI_PIPELINE_ID-$CI_JOB_ID" "$name" reddit.
    - >
      helm upgrade --install \
        --wait \
        -set ui.ingress.host="$host" \.
        -set ui.image.tag="$(curl http://gitlab-gitlab/$CI_PROJECT_NAMESPACE/ui/raw/master/VERSION)". \
        -set post.image.tag="$(curl http://gitlab-gitlab/$CI_PROJECT_NAMESPACE/post/raw/master/VERSION)". \
        -set comment.image.tag="$(curl http://gitlab-gitlab/$CI_PROJECT_NAMESPACE/comment/raw/master/VERSION)". \
        --namespace="$KUBE_NAMESPACE" \.
        --version="$CI_PIPELINE_ID-$CI_JOB_ID" \.
        "$name" \
        reddit
  Environment:
    name: staging
    url: http://staging
  Only:
    refs:
      - master
    kubernetes: active

production:
  stage: production
  It's not:
    KUBE_NAMESPACE: production
    name: $CI_ENVIRONMENT_SLUG
  before_script:
    - helm version --client
    - kubectl version --client
    - kubectl describe namespace "$KUBE_NAMESPACE" || kubectl create namespace "$KUBE_NAMESPACE"
  script:
    - echo KUBE_NAMESPACE=$KUBE_NAMESPACE
    - export track="${1-stable}"
    - "Download helm dependencies..."
    - helm dep update reddit
    - >
      # for microservice in $(helm dep ls | grep "file://" | awk '{print $1}') ; do
      # SET_VERSION="$SET_VERSION \ -set $microservice.image.tag='$(curl http://gitlab-gitlab/$CI_PROJECT_NAMESPACE/ui/raw/master/VERSION)''.
    - >
      echo helm upgrade --install --wait --set ui.ingress.host="$host" --set ui.image.tag="$(curl http://gitlab-gitlab/$CI_PROJECT_NAMESPACE/ui/raw/master/VERSION)" --set post.image. tag="$(curl http://gitlab-gitlab/$CI_PROJECT_NAMESPACE/post/raw/master/VERSION)" -set comment.image. tag="$(curl http://gitlab-gitlab/$CI_PROJECT_NAMESPACE/comment/raw/master/VERSION)" --namespace="$KUBE_NAMESPACE" --version="$CI_PIPELINE_ID-$CI_JOB_ID" "$name" reddit.
    - >
      helm upgrade --install \
        --wait \
        -set ui.ingress.host="$host" \
        -set ui.image.tag="$(curl http://gitlab-gitlab/$CI_PROJECT_NAMESPACE/ui/raw/master/VERSION)". \
        -set post.image.tag="$(curl http://gitlab-gitlab/$CI_PROJECT_NAMESPACE/post/raw/master/VERSION)". \
        -set comment.image.tag="$(curl http://gitlab-gitlab/$CI_PROJECT_NAMESPACE/comment/raw/master/VERSION)". \
        --namespace="$KUBE_NAMESPACE." \
        --version="$CI_PIPELINE_ID-$CI_JOB_ID". \
        "$name" \
        reddit
  Environment:
    name: production
    url: http://production
  when: manual
  Only:
    refs:
      - master
    kubernetes: active
```

During the deploying process, an error occurred that the resources being created already exist (unfortunately, the log cannot be obtained anymore).

It was necessary to delete `staging` and `prodaction`, created earlier using `helm-2.13.1`.
``hell``.
helm-2.13.1 delete production --purge
helm-2.13.1 delete staging --purge
```
TODO: figure out how to switch to helm3 without removing `production` ^_^.


All stages are working. Surrounds are being created. Releases are being deposited. Surrounds are working.


### "## Task from \ "..: Automatic deploying

Now we have staging and production - at the push of a button. Tie the image build Pipeline and deploying Pipeline to staging and production so that after the release of the image from the branch the wizard starts deploying the new version of the application on production

As I understood from the task, the pipelin `reddit-deploy/.gitlab-ci.yml` (including the jobug `production`) needs to automatically start when the jobug `reelease` starts in `*/.gitlab-ci.yml` any of the 3 services (`ui`, `post` or `comment`).

Read: https://docs.gitlab.com/сe/ci/yaml/#trigger-premium.

So it's a premium Hitlab ficha. But still, let's make the necessary changes.

In `reddit-deploy/.gitlab-ci.yml`job `production` replace `when: manual` with `when: on_success`.

TODO: change app's pipelines

Second option: https://docs.gitlab.com/ce/ci/triggers/.

Test for ui:

See Project ID: _Settings_ -> _General_ -> _General project settings_ -> **Project ID** in our case ***4***.
![](kubernetes/img/screenshot-gitlab-projectid.png)

Let's add a team to the end of the `script` section.
``shell
- curl -v --request POST --form "token=$CI_JOB_TOKEN" --form ref=master http://gitlab-gitlab/api/v4/projects/4/trigger/pipeline.
```

It's a mistake:
``log
curl: (28) Failed to connect to gitlab-gitlab port 443: Operation timed out
```

There's an extra subnet...
![](kubernetes/img/screenshot-vpc-subnetworks.png)

On both of them (there are now two), the default gateway is `10.3.0.1`, so they are both in the subnet `reddit-public-network-5opx-subnetwork-public`. Yes, I know, you can look at it in a different way)).

Perhaps the subnet `reddit-public-network-5opx-subnetwork-private` is left over from the previously created `private` cluster... TODO: figure it out.

But the subnetwork has nothing to do with this.

After the command is brought to the next view:
``shell
curl -v --request POST --form "token=$CI_JOB_TOKEN" --form ref=master http://gitlab-gitlab/api/v4/projects/4/trigger/pipeline.
```
Got a mistake.
``log
curl -v --request POST --form "token=$CI_JOB_TOKEN" --form ref=master http://gitlab-gitlab/api/v4/projects/4/trigger/pipeline.
* Trying 10.4.2.243:80... *
* TCP_NODELAY set
* Connected to gitlab-gitlab (10.4.2.243) port 80 (#0)
> POST /api/v4/projects/4/trigger/pipeline HTTP/1.1
> Host: gitlab-gitlab
> User-Agent: curl/7.67.0
> Accept: */*
> Content-Length: 258
> Content-Type: multipart/form-data; boundary=------------------------------3bba22cfb87cb6b0
> 
} [258 bytes data]
# We are completely uploaded and fine
{"message": "404 Not Found" }* Mark bundle as not supporting multiuse
< HTTP/1.1 404 Not Found
< Cache-Control: no-cache
< Content-Length: 27
< Content-Type: application/json
< Date: Fri, 17 Jan 2020 19:57:05 GMT
< Vary: Origin
< X-Content-Type-Options: nosniff
< X-Frame-Options: SAMEORIGIN
< X-Request-Id: 182d383e-7ac9-40ae-a152-d10ce875856e
< X-Runtime: 0.029111
< 
{[27 bytes data]
```

Again, B - Attention: https://docs.gitlab.com/ce/ci/multi_project_pipelines.html.

It's a **Premium Ficha**, not available in the free version...
> Available in GitLab Premium, GitLab.com Silver, and higher tiers

But in theory, it should work)))

I will consider the task completed ^_^.

I'll leave it to the ui only.


### Completion

Put the `.gitlab-ci.yml' files obtained during the work in the source folder for each component of the application.

Done. Placed in `./src/*/.gitlab-ci.yml`.

File `.gitlab-ci.yml` for reddit-deploy put in `charts`.

Done. Placed in `kubernetes/Charts/.gitlab-ci.yml`.

All changes that were made to Chart's are moved to the charts folder created at the beginning.

Done. Placed in `kubernetes/Charts`.

Folder `Gitlab_ci` - ** no commission**!

Removed all `.git` directories from `./src/*/` as well.

Problem: The `./src/post` directory in the repository is empty.
``shell
LANG=C git add src/post/.gitlab-ci.yml
```
``log
fatal: Pathspec 'src/post/.gitlab-ci.yml' is in submodule 'src/post'.
```

Medicine: https://stackoverflow.com/a/31270959/3488348
``shell
 git rm --cached src/post
 git add src/post
 ```

## HomeWork 23: Kubernetes. Monitoring and Logging

### Preparations

#### Setting up infrastructure

In `kubernetes/terraform/main.tf` rbac, logging and monitoring are disabled and 2 node-pools are described.
``conf
module "gke_cluster" {
  ...
  enable_legacy_abac = "true" # off rbac
  logging_service = "none" # logging is disabled
  monitoring_service = "none" # disabled monitoring
}
resource "google_container_node_pool" "node_pool" {
  node_config {
    machine_type = "g1-small" # Instance type for the first pool
    ...
  }
  autoscaling {
    min_node_count = "2" # minimum 2 nodes
    max_node_count = "3"
  }
  ...
}
resource "google_container_node_pool" "elastic_node_pool" {
  initial_node_count = "1" # number of nodes, autoscaling not enabled
  node_config {
    machine_type = "n1-standard-2" #instance type for the second pool
    labels = {
      elastichost = true # add label
    }
    ...
  }
  ...
}
```

Infrastructure applied
``shell
cd kubernetes/terraform
make init apply
```
and created after about 15 minutes.

Let's set a context for kubectl.
``shell
gcloud container clusters get-credentials reddit-public --zone us-central1-a --project docker-257914
```
``log
Fetching cluster endpoint and auth data.
kubeconfig entry generated for reddit-public.
```

#### Installing the nginx-ingress-controller

##### The remote sensing path

From the Helm Chart, install the ingress controller nginx
``shell
helm install stable/nginx-ingress --name nginx
```
but we'll go the other way.

##### The path of terraform

Let's create a file `kubernetes/terraform/nginx-ingress-controller.tf`.
``conf
provider "helm" {
  kubernetes {
    host = module.gke_cluster.endpoint

    client_certificate = module.gke_cluster.client_certificate
    client_key = module.gke_cluster.client_key
    cluster_ca_certificate = module.gke_cluster.cluster_ca_certificate
  }
}
data "helm_repository" "stable" {
  name = "stable"
  url = "https://kubernetes-charts.storage.googleapis.com"
}
resource "helm_release" "nginx" {
  name = "nginx"
  chart = "stable/nginx-ingress"
  repository = data.helm_repository.stable.metadata[0].name

  cleanup_on_fail = true
  wait = true
}
```

Find the IP address given by nginx
``shell
kubectl get svc
```
``log
NAME TYPE CLUSTER-IP EXTERNAL-IP PORT(S) AGE
kubernetes ClusterIP 10.4.0.1 <none> 443/TCP 39m
nginx-nginx-ingress-controller LoadBalancer 10.4.7.187 34.69.197.128 80:32087/TCP,443:30552/TCP 9m59s
nginx-nginx-ingress-default-backend ClusterIP 10.4.5.206 <none> 80/TCP 9m59s
```

Add to `/etc/hosts`
```
34.69.197.128 reddit reddit-prometheus reddit-grafana reddit-non-prod production reddit-kibana staging prod
```

### Plan

- Deploying Prometheus in k8s
- Setting up Prometheus and Grafana to collect metrics
- Setting up EFK to collect logs

### Monitoring

#### Stack

We will use the tools we already know in the task:
- *prometheus * - metrics collection server
- *grafana* - metrics visualization server
- *alertmanager * - a prometheus component for allergies different *
- exporters for prometheus metrics

Prometheus is perfect for working with containers and dynamic placement of services.
The general scheme of work is presented on the following slide

#### Let's install Prometheus

Prometheus will be put on the Helm Chart

Download prometheus locally in `Charts` directory
``shell
cd kubernetes/charts &&helm fetch --untar stable/prometheus
```

Create a file `custom_values.yml` inside the chart directory.
``Yaml
rbac:
  create: false

Alertmanager:
  ## If false, alertmanager will not be installed
  ##
  enabled: false

  # Defines the serviceAccountName to use when `rbac.create=false`
  serviceAccountName: default

  ## alertmanager container name
  ##
  name: alertmanager

  ## alertmanager container image
  ##
  image:
    repository: prom/alertmanager
    tag: v0.10.0
    pullPolicy: IfNotPresent

  ## Additional alertmanager container
  ##
  extraArgs: {}

  ## The URL prefix at which the container can be accessed. Useful in the case the '-web.external-url' includes a slug
  ## so that the various internal URLs are still able to access as they are in the default case.
  ## (Optional)
  baseURL: "/"

  ## Additional alertmanager container environment variable
  ## For instance to add a http_proxy
  ##
  extraEnv: {}

  ## ConfigMap override where fullname is {{{.Release.Name}}-{{{.Values.alertmanager.configMapOverrideName}}.
  ## Defining configMapOverrideName will cause templates/alertmanager-configmap.yaml
  ## to NOT generate a ConfigMap resource
  ##
  configMapOverrideName: ""

  ingress:
    ## If true, alertmanager Ingress will be created
    ##
    enabled: false

    ## alertmanager Ingress annotations
    ##
    annotations: {}
    # kubernetes.io/ingress.class: nginx
    # kubernetes.io/tls-acme: 'true'

    ## alertmanager Ingress hostnames
    ## Must be provided if Ingress is enabled
    ##
    Hosts: []
    # - alertmanager.domain.com

    ## alertmanager Ingress TLS configuration
    ## Secrets must be manually created in the namespace
    ##
    tls: []
    # - secretName: prometheus-alerts-tls
    # hosts:
    # - alertmanager.domain.com

  ## Alertmanager Deployment Strategy type
  # strategy:
  # type: Recreate

  ## Node labels for alertmanager pod assignment
  ## Ref: https://kubernetes.io/docs/user-guide/node-selection/
  ##
  nodeSelector: {}

  persistentVolume:
    ## If true, alertmanager will create/use a Persistent Volume Claim
    ## If false, use emptyDir
    ##
    entitled: true

    ## alertmanager data Persistent Volume access modes
    ## Must match those of existing PV or dynamic provisioner
    ## Ref: http://kubernetes.io/docs/user-guide/persistent-volumes/
    ##
    accessModes:
      - ReadWriteOnce

    ## alertmanager data Persistent Volume Claim annotations
    ##
    annotations: {}

    ## alertmanager data Persistent Volume existing claim name
    ## Requires alertmanager.persistentVolume.enabled: true
    ## If defined, PVC must be created manually before volume will be bound
    ""

    ## alertmanager data Persistent Volume mount root path
    ##
    mountPath: /data

    ## alertmanager data Persistent Volume size
    ##
    size: 2Gi

    ## alertmanager data Persistent Volume Storage Class
    ## If defined, storageClassName: <storageClass>
    ## If set to "-", storageClassName: "", which disables dynamic provisioning
    ## If undefined (the default) or set to null, no storageClassName spec is
    ## set, selecting the default provisioner.  (gp2 on AWS, standard on
    ## GKE, AWS & OpenStack)
    ##
    # storageClass: "-"

    ## Subdirectory of alertmanager data Persistent Volume to mount
    ## Useful if the volume's root directory is not empty
    ##
    subPath: ""

  ## Annotations to be added to alertmanager pods
  ##
  podAnnotations: {}

  replicaCount: 1

  ## alertmanager resource requests and limits
  ## Ref: http://kubernetes.io/docs/user-guide/compute-resources/
  ##
  Resources: {}
    # limits. #
    # cpu: 10m
    # memory: 32Mi
    # requests:
    # cpu: 10m
    # memory: 32Mi

  service:
    annotations: {}
    The labels: {}
    clusterIP: ""

    ## List of IP addresses at which the alertmanager service is available
    ## Ref: https://kubernetes.io/docs/user-guide/services/#external-ips
    ##
    externalIPs: []

    loadBalancerIP: ""
    loadBalancerSourceRanges: []
    servicePort: 80
    # nodePort: 30000
    Type: ClusterIP

## Monitors ConfigMap changes and POSTs to a URL
## Ref: https://github.com/jimmidyson/configmap-reload
##
ConfmapReload:
  ## configmap-reload container name
  ##
  name: configmap-reload

  ## configmap-reload container image
  ##
  image:
    repository: jimmidyson/configmap-reload
    tag: v0.1
    pullPolicy: IfNotPresent

  ## configmap-reload resource requests and limits
  ## Ref: http://kubernetes.io/docs/user-guide/compute-resources/
  ##
  Resources: {}

kubeStateMetrics:
  ## If false, the kube-state-metrics will not be installed
  ##
  enabled: false

  # Defines the serviceAccountName to use when `rbac.create=false`
  serviceAccountName: default

  ## kube-state-metrics container name
  ##
  name: kube-state-metrics

  ## kube-state-metrics container image
  ##
  image:
    repository: gcr.io/google_containers/kube-state-metrics
    tag: v1.1.0
    pullPolicy: IfNotPresent

  ## Node labels for kube-state-metrics pod assignment
  ## Ref: https://kubernetes.io/docs/user-guide/node-selection/
  ##
  nodeSelector: {}

  ## Annotations to be added to kube-state-metrics pods
  ##
  podAnnotations: {}

  replicaCount: 1

  ## kube-state-metrics resource requests and limits
  ## Ref: http://kubernetes.io/docs/user-guide/compute-resources/
  ##
  Resources: {}
    # limits. #
    # cpu: 10m
    # memory: 16Mi
    # requests:
    # cpu: 10m
    # memory: 16Mi

  service:
    annotations:
      prometheus.io/scrape: "true"
    The labels: {}

    clusterIP: None

    ## List of IP addresses at which the kube-state-metrics service is available
    ## Ref: https://kubernetes.io/docs/user-guide/services/#external-ips
    ##
    externalIPs: []

    loadBalancerIP: ""
    loadBalancerSourceRanges: []
    servicePort: 80
    Type: ClusterIP

nodeExporter:
  ## If false, node-exporter will not be installed
  ##
  enabled: false

  # Defines the serviceAccountName to use when `rbac.create=false`
  serviceAccountName: default

  ## node-exporter container name
  ##
  name: node-exporter

  ## node-exporter container image
  ##
  image:
    repository: prom/node-exporter
    tag: v0.15.1
    pullPolicy: IfNotPresent

  ## Custom Update Strategy
  ##
  updateStrategy:
    type: OnDelete

  ## Additional node-exporter container
  ##
  extraArgs: {}

  ## Additional node-exporter hostPath mounts
  ##
  extraHostPathMounts: []
    # - name: textfile-dir
    # mountPath: /srv/txt_collector
    # hostPath: /var/lib/node-exporter
    # readOnly: true

  ## Node tolerations for node-exporter scheduling to nodes with taints
  ## Ref: https://kubernetes.io/docs/concepts/configuration/assign-pod-node/
  ##
  tolerations: []
    # - key: "key"
    # operator: "Equal|Exists"
    # value: "value"
    # effect: "NoSchedule|PreferNoSchedule|NoExecute(1.6 only)"

  ## Node labels for node-exporter pod assignment
  ## Ref: https://kubernetes.io/docs/user-guide/node-selection/
  ##
  nodeSelector: {}

  ## Annotations to be added to node-exporter pods
  ##
  podAnnotations: {}

  ## node-exporter resource limits & requests
  ## Ref: https://kubernetes.io/docs/user-guide/compute-resources/
  ##
  Resources: {}
    # limits. #
    # cpu: 200m
    # memory: 50Mi
    # requests:
    # cpu: 100m
    # memory: 30Mi

  service:
    annotations:
      prometheus.io/scrape: "true"
    The labels: {}

    clusterIP: None

    ## List of IP addresses at which the node-exporter service is available
    ## Ref: https://kubernetes.io/docs/user-guide/services/#external-ips
    ##
    externalIPs: []

    hostPort: 9,100
    loadBalancerIP: ""
    loadBalancerSourceRanges: []
    servicePort: 9,100
    Type: ClusterIP

server:
  ## Prometheus server container name
  ##
  name: server

  # Defines the serviceAccountName to use when `rbac.create=false`
  serviceAccountName: default

  ## Prometheus server container image
  ##
  image:
    repository: prom/prometheus
    tag: v2.0.0
    pullPolicy: IfNotPresent

  ## (optional) alertmanager hostname
  ## only used if alertmanager. enabled = false
  alertmanagerHostname: ""

  ## The URL prefix at which the container can be accessed. Useful in the case the '-web.external-url' includes a slug
  ## so that the various internal URLs are still able to access as they are in the default case.
  ## (Optional)
  baseURL: ""

  ## Additional Prometheus server container
  ##
  extraArgs: {}

  ## Additional Prometheus server hostPath mounts
  ##
  extraHostPathMounts: []
    # - name: certs-dir
    # mountPath: /etc/kubernetes/certs
    # hostPath: /etc/kubernetes/certs
    # readOnly: true

  ## ConfigMap override where fullname is {{{.Release.Name}}-{{{.Values.server.configMapOverrideName}}.
  ## Defining configMapOverrideName will cause templates/server-configmap.yaml
  ## to NOT generate a ConfigMap resource
  ##
  configMapOverrideName: ""

  ingress:
    ## If true, Prometheus server Ingress will be created
    ##
    entitled: true

    ## Prometheus server Ingress annotations
    ##
    annotations: {}
    # kubernetes.io/ingress.class: nginx
    # kubernetes.io/tls-acme: 'true'

    ## Prometheus server Ingress hostnames
    ## Must be provided if Ingress is enabled
    ##
    Hosts:
     - reddit-prometheus

    ## Prometheus server Ingress TLS configuration
    ## Secrets must be manually created in the namespace
    ##
    tls: []
    # - secretName: prometheus-server-tls
    # hosts:
    # - prometheus.domain.com

  ## Server Deployment Strategy type
  # strategy:
  # type: Recreate

  ## Node tolerations for server scheduling to nodes with taints
  ## Ref: https://kubernetes.io/docs/concepts/configuration/assign-pod-node/
  ##
  tolerations: []
    # - key: "key"
    # operator: "Equal|Exists"
    # value: "value"
    # effect: "NoSchedule|PreferNoSchedule|NoExecute(1.6 only)"

  ## Node labels for Prometheus server pod assignment
  ## Ref: https://kubernetes.io/docs/user-guide/node-selection/
  nodeSelector: {}

  persistentVolume:
    ## If true, Prometheus server will create/use a Persistent Volume Claim
    ## If false, use emptyDir
    ##
    entitled: true

    ## Prometheus server data Persistent Volume access modes
    ## Must match those of existing PV or dynamic provisioner
    ## Ref: http://kubernetes.io/docs/user-guide/persistent-volumes/
    ##
    accessModes:
      - ReadWriteOnce

    ## Prometheus server data Persistent Volume annotations
    ##
    annotations: {}

    ## Prometheus server data Persistent Volume existing claim name
    ## Requires server.persistentVolume.enabled: true
    ## If defined, PVC must be created manually before volume will be bound
    ""

    ## Prometheus server data Persistent Volume mount root path
    ##
    mountPath: /data

    ## Prometheus server data Persistent Volume size
    ##
    size: 8Gi

    ## Prometheus server data Persistent Volume Storage Class
    ## If defined, storageClassName: <storageClass>
    ## If set to "-", storageClassName: "", which disables dynamic provisioning
    ## If undefined (the default) or set to null, no storageClassName spec is
    ## set, selecting the default provisioner.  (gp2 on AWS, standard on
    ## GKE, AWS & OpenStack)
    ##
    # storageClass: "-"

    ## Subdirectory of Prometheus server data Persistent Volume to mount
    ## Useful if the volume's root directory is not empty
    ##
    subPath: ""

  ## Annotations to be added to Prometheus server pods
  ##
  podAnnotations: {}
    # iam.amazonaws.com/role: prometheus

  replicaCount: 1

  # Prometheus server resource requests and
  ## Ref: http://kubernetes.io/docs/user-guide/compute-resources/
  ##
  Resources: {}
    # limits. #
    # cpu: 500m
    # memory: 512Mi
    # requests:
    # cpu: 500m
    # memory: 512Mi

  service:
    annotations: {}
    The labels: {}
    clusterIP: ""

    ## List of IP addresses at which the Prometheus server service is
    ## Ref: https://kubernetes.io/docs/user-guide/services/#external-ips
    ##
    externalIPs: []

    loadBalancerIP: ""
    loadBalancerSourceRanges: []
    servicePort: 80
    Type: LoadBalancer

  ## Prometheus server pod termination grace period
  ##
  I don't know what you're talking about: 300

  ## Prometheus data retention period (i.e 360h)
  ##
  I'm sorry: ""

pushgateway:
  ## If false, the pushgateway will not be installed
  ##
  enabled: false

  ## pushgateway container name
  ##
  name: pushgateway

  ## pushgateway container image
  ##
  image:
    repository: prom/pushgateway
    tag: v0.4.0
    pullPolicy: IfNotPresent

  ## Additional pushgateway container
  ##
  extraArgs: {}

  ingress:
    ## If true, pushgateway Ingress will be created
    ##
    enabled: false

    ## pushgateway Ingress annotations
    ##
    annotations:
    # kubernetes.io/ingress.class: nginx
    # kubernetes.io/tls-acme: 'true'

    ## pushgateway Ingress hostnames
    ## Must be provided if Ingress is enabled
    ##
    Hosts: []
    # - pushgateway.domain.com

    ## pushgateway Ingress TLS configuration
    ## Secrets must be manually created in the namespace
    ##
    tls: []
    # - secretName: prometheus-alerts-tls
    # hosts:
    # - pushgateway.domain.com

  ## Node labels for pushgateway pod assignment
  ## Ref: https://kubernetes.io/docs/user-guide/node-selection/
  ##
  nodeSelector: {}

  ## Annotations to be added to pushgateway pods
  ##
  podAnnotations: {}

  replicaCount: 1

  ## pushgateway resource requests and
  ## Ref: http://kubernetes.io/docs/user-guide/compute-resources/
  ##
  Resources: {}
    # limits. #
    # cpu: 10m
    # memory: 32Mi
    # requests:
    # cpu: 10m
    # memory: 32Mi

  service:
    annotations:
      prometheus.io/probe: pushgateway
    The labels: {}
    clusterIP: ""

    ## List of IP addresses at which the pushgateway service is
    ## Ref: https://kubernetes.io/docs/user-guide/services/#external-ips
    ##
    externalIPs: []

    loadBalancerIP: ""
    loadBalancerSourceRanges: []
    servicePort: 9091
    Type: ClusterIP

## alertmanager ConfigMap entries
##
AlertmanagerFiles:
  alertmanager.yml: |-
    global:
      # slack_api_url: ''

    receivers:
      - name: default-receiver
        # slack_configs:
        # - channel: '@you'
        # send_resolved: true

    The route:
      group_wait: 10s
      group_interval: 5m
      default-receiver
      repeat_interval: 3h

## Prometheus server ConfigMap entries
##
serverFiles:
  alerts: {}
  Rules: {}

  prometheus.yml:
    rule_files:
      - /etc/config/rules
      - /etc/config/alerts

    global:
      scrape_interval: 30s

    scrape_configs:
      - job_name: prometheus
        static_configs:
          - targets:
            - localhost:9090

      # A scrape configuration for running Prometheus on a Kubernetes cluster. #
      # This uses separate scrape configs for cluster components (i.e. API server, node)
      # and services to allow each to use different authentication configs. #
      #
      # Kubernetes labels will be added as Prometheus labels on metrics via the
      # Labelmap # relabeling action.

      # Scrape config for API servers.
      #
      # Kubernetes exposes API servers as endpoints to the default/kubernetes
      # service so this uses `endpoints` role and uses relabelling to only keep
      # the endpoints associated with the default/kubernetes service using the
      # default named port #https # This works for single API server deployments as
      # well as HA API server deployments.
      - job_name: 'kubernetes-apiservers'

        kubernetes_sd_configs:
          - role: endpoints

        # Default to scraping over https. If required, just disable this or change to
        # `http''.
        `https`

        # This TLS & bearer token file config is used to connect to the actual scrape
        # endpoints for cluster. This is separate to discovery auth
        # configuration because & scraping are two separate concerns in
        # Prometheus. The discovery auth config is automatic if Prometheus runs inside
        # the cluster. Otherwise, more config options have to be provided within the
        # <kubernetes_sd_config>.
        tls_config:
          ca_file: /var/run/secrets/kubernetes.io/serviceaccount/ca.crt
          # If your node is self-signed or using a different CA to the
          # master CA, then disable certificate verification below. # Note that
          # certificate verification is an integral part of a secure infrastructure
          # so this should only be disabled in a controlled environment. # You can
          #disable certificate verification by uncommenting the line below.
          #
          insecure_skip_verify: true
        bearer_token_file: /var/run/secrets/kubernetes.io/serviceaccount/token

        # Keep only the default/kubernetes service endpoints for the https port. This
        # will add for each API server which Kubernetes adds an endpoint to
        # the default/kubernetes service #
        relabel_configs:
          - source_labels: [__meta_kubernetes_namespace, __meta_kubernetes_service_name, __meta_kubernetes_endpoint_port_name]
            action: keep
            regex: default;kubernetes;https

      - job_name: 'kubernetes-nodes'

        # Default to scraping over https. If required, just disable this or change to
        # `http''.
        `https`

        # This TLS & bearer token file config is used to connect to the actual scrape
        # endpoints for cluster. This is separate to discovery auth
        # configuration because & scraping are two separate concerns in
        # Prometheus. The discovery auth config is automatic if Prometheus runs inside
        # the cluster. Otherwise, more config options have to be provided within the
        # <kubernetes_sd_config>.
        tls_config:
          ca_file: /var/run/secrets/kubernetes.io/serviceaccount/ca.crt
          # If your node is self-signed or using a different CA to the
          # master CA, then disable certificate verification below. # Note that
          # certificate verification is an integral part of a secure infrastructure
          # so this should only be disabled in a controlled environment. # You can
          #disable certificate verification by uncommenting the line below.
          #
          insecure_skip_verify: true
        bearer_token_file: /var/run/secrets/kubernetes.io/serviceaccount/token

        kubernetes_sd_configs:
          - role: node

        relabel_configs:
          - action: labelmap
            regex: __meta_kubernetes_node_label_(.+)
          - target_label: __address__
            replacement: kubernetes.default.svc:443
          - source_labels: [__meta_kubernetes_node_name]
            regex: (.+)
            target_label: __metrics_path__
            I'm sorry: /api/v1/nodes/${1}/proxy/metrics/cadvisor

      # Scrape config for service endpoints.
      #
      # The relabeling allows the actual service scrape endpoint to be configured
      # through the following annotations:
      #
      # `prometheus.io/scrape # Only scrape services that have a value of `true'.
      # `prometheus.io/scheme # If the metrics endpoint is secured then you will need
      # to set this to `https` & most likely set the `tls_config` of the scrape config.
      # `prometheus.io/path # If the metrics path is not `/metrics` override this.
      # `prometheus.io/port': If the metrics path is not `/metrics` override this: If the metrics are exposed on a different port to the
      # service then set this appropriately.
      - job_name: 'kubernetes-service-endpoints'.

        kubernetes_sd_configs:
          - role: endpoints

        relabel_configs:
          - source_labels: [__meta_kubernetes_service_annotation_prometheus_io_scrape]
            action: keep
            regex: true
          - source_labels: [__meta_kubernetes_service_annotation_prometheus_io_scheme]
            action: replace
            target_label: __scheme__
            regex: (https?)
          - source_labels: [__meta_kubernetes_service_annotation_prometheus_io_path]
            action: replace
            target_label: __metrics_path__
            regex: (.+)
          - source_labels: [__address__, __meta_kubernetes_service_annotation_prometheus_io_port]
            action: replace
            target_label: __address__
            regex: (.+)??::\d+);(\d+)
            replacement: $1:$2
          - action: labelmap
            regex: __meta_kubernetes_service_label_(.+)
          - source_labels: [__meta_kubernetes_namespace]
            action: replace
            target_label: kubernetes_namespace
          - source_labels: [__meta_kubernetes_service_name]
            action: replace
            target_label: kubernetes_name

      - job_name: 'prometheus-pushgateway'.
        honor_labels: true

        kubernetes_sd_configs:
          - role: service

        relabel_configs:
          - source_labels: [__meta_kubernetes_service_annotation_prometheus_io_probe]
            action: keep
            pushgateway

      # Example scrape config for probing services through the Blackbox Exporter.
      #
      # The relabeling allows the actual service scrape endpoint to be configured
      # through the following annotations:
      #
      # `prometheus.io/probe # Only probe services that have a value of `true'.
      - job_name: 'kubernetes-services'

        metrics_path: /probe
        params:
          module: [http_2xx]

        kubernetes_sd_configs:
          - role: service

        relabel_configs:
          - source_labels: [__meta_kubernetes_service_annotation_prometheus_io_probe]
            action: keep
            regex: true
          - source_labels: [__address__]
            target_label: __param_target
          - target_label: __address__
            blackbox
          - source_labels: [__param_target]
            target_label: instance
          - action: labelmap
            regex: __meta_kubernetes_service_label_(.+)
          - source_labels: [__meta_kubernetes_namespace]
            target_label: kubernetes_namespace
          - source_labels: [__meta_kubernetes_service_name]
            target_label: kubernetes_name

      # Example scrape config for pods
      #
      # The relabeling allows the actual pod scrape endpoint to be configured via the
      # following annotations:
      #
      # `prometheus.io/scrape # Only scrape pods that have a value of `true'.
      # `prometheus.io/path # If the metrics path is not `metrics` override this.
      # `prometheus.io/port': If the metrics path is not `metrics` override this: Scrape the pod on the indicated port instead of the default of `9102'.
      - job_name: 'kubernetes-pods'.

        kubernetes_sd_configs:
          - role: pod

        relabel_configs:
          - source_labels: [__meta_kubernetes_pod_annotation_prometheus_io_scrape]
            action: keep
            regex: true
          - source_labels: [__meta_kubernetes_pod_annotation_prometheus_io_path]
            action: replace
            target_label: __metrics_path__
            regex: (.+)
          - source_labels: [__address__, __meta_kubernetes_pod_annotation_prometheus_io_port]
            action: replace
            regex: (.+):??:\d+);(\d+)
            ${1}:${2}.
            target_label: __address__
          - action: labelmap
            regex: __meta_kubernetes_pod_label_(.+)
          - source_labels: [__meta_kubernetes_namespace]
            action: replace
            target_label: kubernetes_namespace
          - source_labels: [__meta_kubernetes_pod_name]
            action: replace
            target_label: kubernetes_pod_name

networkPolicy:
  ## Enable creation of networkPolicy resources.
  ##
  enabled: false
```

The main differences from `values.yml`:
- some of the installed services are disabled (pushgateway, alertmanager, kube-state-metrics)
- Enabled Ingress creation for connection via nginx
- fixed endpoint for cadvisor metrics
- collection interval of metrics has been reduced (from 1 minute to 30 seconds).

Run Prometheus in k8s from `Charts/prometheus`.
``shell
helm upgrade prom . -f custom_values.yml --install
```

Check: http://reddit-prometheus successfully)


#### Targets

We already have a number of endpoints in place to collect metrics:
- Metrics from the API server.
- node metrics from cadvisors
- prometheus itself

Note that you can collect cadvisor's metrics...
is part of the kubelet) through a proxy request to the kube-apiserver

If you go by ssh to any of the cluster machines and request `curl http://localhost:4194/metrics` you will get the same metrics from kubelet directly.

**But the option with kube-api is preferable, because this traffic
is encrypted by TLS and requires authentication.

Targettes for metrics collection are found using service discovery
(**SD**) configured in the prometheus config (`custom_values.yml`).

`prometheus.yml`:
``Yaml
...
- job_name: 'kubernetes-apiservers' # kubernetes-apiservers (1/1 up)
...
- job_name: 'kubernetes-nodes' # kubernetes-nodes (3/3 up)
  kubernetes_sd_configs: # Service Discovery settings (to search for targets)
  - role: node
    scheme: https # Connection settings to targets (to collect metrics)
    tls_config:
      ca_file: /var/run/secrets/kubernetes.io/serviceaccount/ca.crt
      insecure_skip_verify: true
    bearer_token_file: /var/run/secrets/kubernetes.io/serviceaccount/token
    relabel_configs: # Settings of different labels, filtering the found tags, their changes
```

Using SD in kubernetes allows us to dynamically change the cluster (both hosts and services and applications).

The targets for monitoring are found through requests to the k8s API:
`prometheus.yml`
``Yaml
...
  scrape_configs:
    - job_name: 'kubernetes-nodes'.
      kubernetes_sd_configs:
        - role: node # Role object to be found:
                      # - node
                      # - endpoints
                      # - pod
                      # - service
                      # - ingress
```

Since prometheus metrics are collected over a standard HTTP protocol, additional settings may be required for secure access to the metrics.

Below are the settings for collecting metrics from k8s AP
``Yaml
scheme: https
tls_config:
  ca_file: /var/run/secrets/kubernetes.io/serviceaccount/ca.crt
  insecure_skip_verify: true
bearer_token_file: /var/run/secrets/kubernetes.io/serviceaccount/token
```

1. Connection scheme - http (default) or https
2. TLS configuration - server root certificate for checking the server authenticity
3. Token to authenticate with the server.

Targets:
- gke-cluster-1-default-pool-f9c66281-kxrc
- gke-cluster-1-default-pool-f9c66281-8gkc
- gke-cluster-1-big-pool-b4209075-jlnq

#### Relabel config

https://prometheus.io/docs/prometheus/latest/configuration/configuration/#relabel_config

``Yaml
#Kubernetes nodes
relabel_configs:
  - action: labelmap # convert all k8s of target labels to prometheus labels
    regex: __meta_kubernetes_node_label_(.+)
  - target_label: __address__ # Change label for metrics collection address
    replacement: kubernetes.default.svc:443
  - source_labels: [__meta_kubernetes_node_name] # Change the label for the path for collecting metrics
    regex: (.+)
    target_label: __metrics_path__
    replacement: /api/v1/nodes/${1}/proxy/metrics/cadvisor
```

We'll end up with labels like this in prometheus:
```
beta_kubernetes_io_arch="amd64"
beta_kubernetes_io_fluentd_ds_ready="true".
beta_kubernetes_io_instance_type="n1-standard-2".
beta_kubernetes_io_masq_agent_ds_ready="true".
beta_kubernetes_io_os="linux".
cloud_google_com_gke_nodepool="elastic-pool".
cloud_google_com_gke_os_distribution="cos".
elastichost="true"
failure_domain_beta_kubernetes_io_region="us-central1"
failure_domain_beta_kubernetes_io_zone="us-central1-a"
instance="gke-reddit-public-elastic-pool-6fb5390b-fc8w."
kubernetes_io_arch="amd64"
kubernetes_io_hostname="gke-reddit-public-elastic-pool-6fb5390b-fc8w".
kubernetes_io_os="linux"
node_kubernetes_io_masq_agent_ds_ready="true".
projectcalico_org_ds_ready="true"
```

#### Metrics

All metrics found on endpoints will immediately appear in the list (Graph tab). Cadvisor metrics start with `container_`.

Cadvisor collects only information about resource consumption and performance of individual dockers. It doesn't know anything about the essence of k8s (deployments, replicasettes, ...).

To collect this information, we will use the service `kube-state-metrics`. He's on the Prometheus charts. Let's turn it on.

`prometheus/custom_values.yml'.
``Yaml
kubeStateMetrics:
  enabled: true
```

Update release
``shell
helm upgrade prom . -f custom_values.yml --install
```
``log
coalesce.go:196: warning: cannot overwrite table with no table for annotations (map[])
coalesce.go:196: warning: cannot overwrite table with non table for alertmanager.yml (map[global:map[] receivers:[map[name:default-receiver]] route:map[group_interval:5m group_wait:10s receiver:default-receiver repeat_interval:3h]).
Release "prom" has been upgraded. Happy Helming!
NAME: prom
LAST DEPLOYED: Sun Feb 16 22:04:39 2020
NAMESPACE: default
STATUS: deployed
REVISION: 2
TEST SUITE: None
NOTES:
The Prometheus server can be accessed via port 80 on the following DNS name from within your cluster:
prom-prometheus-server.default.svc.cluster.local

From outside the cluster, the server URL(s) are:
http://reddit-prometheus


#################################################################################
##### WARNING: Pod Security Policy has been moved to a global property.  #####
##### use .Values.podSecurityPolicy.
###### annotations #####
##### (e.g. .Values.nodeExporter.podSecurityPolicy.annotations) #####.
#################################################################################



For more information on running Prometheus, visit:
https://prometheus.io/
```

at Targets:
| Endpoint | State | Labels | Last Scrape | Error |
  -------------------------------------------------------------------------- | ----------- | ---------------------------------------------------------------------------------------- |
| http://10.4.1.3:8080/metrics | UP | app="prometheus" chart="prometheus-10.4.0" component="kube-state-metrics" heritage="Helm" instance="10.4.1.3:8080" kubernetes_name="prom-prometheus-kube-state-metrics" kubernetes_namespace="default" release="prom" | 5.875s ago |.
| http://10.4.1.3:8081/metrics | DOWN | app="prometheus" chart="prometheus-10.4.0" component="kube-state-metrics" heritage="Helm" instance="10.4.1. 3:8081" kubernetes_name="prom-prometheus-kube-state-metrics" kubernetes_namespace="default" release="prom" | 27.232s ago | Get http://10.4.1.3:8081/metrics: dial tcp 10.4.1.3:8081: getsockopt: connection refused |.

For the time being, let's leave the second engipoint out of the way, on TODO: since the necessary metrics are given away

in Graph: `kube_...` and there are many))))

#### Assignment

Similar to kube_state_metrics, enable (enabled: true) the subpaths of node-exporter in `custom_values.yml'.
```yaml
nodeExporter:
  ## If false, node-exporter will not be installed
  ##
  entitled: true
```
``shell
helm upgrade prom . -f custom_values.yml --install
```
``log
console output is similar to the previous
```

Make sure the metrics started gathering with them.

There's a lot of metrics `node_*.


#### Application metrics

Run the application from the helm reddit chart (remember, unlike the RS we have here helm3 ^_^).
``shell
cd kubernetes/Charts/
helm upgrade reddit-test ./reddit --install
kubectl describe namespace production || kubectl create namespace production
helm upgrade production --namespace production ./reddit --install
kubectl describe namespace staging || kubectl create namespace staging
helm upgrade staging --namespace staging ./reddit --install
```

We used to "hardcodile" the addresses/dns-names of our applications to collect metrics from them.

`prometheus.yml`
``Yaml
- job_name: 'ui'
  static_configs:
    - targets:
      - 'ui:9292'.
- job_name: 'comment'
  static_configs:
    - targets:
      - 'comment:9292'
```

Now we can use the ServiceDiscovery mechanism to discover applications running in k8s.

We will look for applications in the same way as for k8s services.

We're going to upgrade the prometheus configuration:
`custom_values.yml`.
``Yaml
  - job_name: "reddit endpoints"
    kubernetes_sd_configs:
      - role: endpoints
    relabel_configs:
      - source_labels: [__meta_kubernetes_service_label_app]
        action: keep # We use the keep action to keep
        regex: reddit # only endpoints of tagged services
                       # "app=reddit"
```

Update prometheus release
``shell
cd ./prometheus
helm upgrade prom . -f custom_values.yml --install
```
``log
coalesce.go:196: warning: cannot overwrite table with no table for annotations (map[])
coalesce.go:196: warning: cannot overwrite table with non table for alertmanager.yml (map[global:map[] receivers:[map[name:default-receiver]] route:map[group_interval:5m group_wait:10s receiver:default-receiver repeat_interval:3h]).
Release "prom" has been upgraded. Happy Helming!
NAME: prom
LAST DEPLOYED: Tue Feb 18 22:15:38 2020
NAMESPACE: default
STATUS: deployed
REVISION: 4
TEST SUITE: None
NOTES:
The Prometheus server can be accessed via port 80 on the following DNS name from within your cluster:
prom-prometheus-server.default.svc.cluster.local

From outside the cluster, the server URL(s) are:
http://reddit-prometheus


#################################################################################
##### WARNING: Pod Security Policy has been moved to a global property.  #####
##### use .Values.podSecurityPolicy.
###### annotations #####
##### (e.g. .Values.nodeExporter.podSecurityPolicy.annotations) #####.
#################################################################################



For more information on running Prometheus, visit:
https://prometheus.io/
```

We got the endpoints, but we don't know what the hell it is. Let's add the k8s tags

All labels and k8s annotations are initially displayed in prometheus format:
- `__meta_kubernetes_service_label_labelname`.
- `__meta_kubernetes_service_annotation_annotationname`.

`custom_values.yml`
``Yaml
relabel_configs:
  - action: labelmap # Show all group matches
    regex: __meta_kubernetes_service_label_(.+) # from regex to Prometheus labels
```

Update prometheus release
``shell
helm upgrade prom . -f custom_values.yml --install
```

Now we see the labels of k8s assigned by POD (on the example of the metric `ui_request_count`).

Let's add more labels for prometheus and update the helm release Since the labels of the kind `__meta*` are not published, you need to create your own by transferring the information into them.
``Yaml
- source_labels: [__meta_kubernetes_namespace]
  target_label: kubernetes_namespace
- source_labels: [__meta_kubernetes_service_name]
  target_label: kubernetes_name
```

Update the prometheus release and...
``shell
helm upgrade prom . -f custom_values.yml --install
```

Now we collect metrics from all reddit's services in the 1st group of targets. We can separate the target components from each other (by environment, by component itself) and also disable and enable the monitoring option for them using the same variables. For example, we can add 1 more job to the config:
```Yaml
- job_name: 'reddit-production'
   kubernetes_sd_configs:
     - role: endpoints
   relabel_configs:
     - action: labelmap
       regex: __meta_kubernetes_service_label_(.+)
     - source_labels: [__meta_kubernetes_service_label_app, __meta_kubernetes_namespace].
       action: keep # For different labels
       regex: reddit;(production|staging)+ # different regexes
     - source_labels: [__meta_kubernetes_namespace]
       target_label: kubernetes_namespace
     - source_labels: [__meta_kubernetes_service_name]
       target_label: kubernetes_name
```

Let's update the prometheus release and see.
``shell
helm upgrade prom . -f custom_values.yml --install
```
and we see the corresponding targets.

Metrics will be displayed for all application instances

#### Assignment

Break down the configuration of the job's reddit endpoints (slide 24) so that there are 3 jobs for each of the application components (post-endpoints, comment-endpoints, ui-endpoints) and remove the reddit endpoints.

easy:
```yaml
      - job_name: "comment-endpoints"
        kubernetes_sd_configs:
          - role: endpoints
        relabel_configs:
          - source_labels: [__meta_kubernetes_service_label_app]
            action: keep
            regex: reddit
          - source_labels: [__meta_kubernetes_service_label_component]
            action: keep
            regex: comment
          - action: labelmap # Show all group matches
            regex: __meta_kubernetes_service_label_(.+) # from regex to Prometheus labels
          - source_labels: [__meta_kubernetes_namespace]
            target_label: kubernetes_namespace
          - source_labels: [__meta_kubernetes_service_name]
            target_label: kubernetes_name

      - job_name: "ui-endpoints"
        kubernetes_sd_configs:
          - role: endpoints
        relabel_configs:
          - source_labels: [__meta_kubernetes_service_label_app]
            action: keep
            regex: reddit
          - source_labels: [__meta_kubernetes_service_label_component]
            action: keep
            regex: ui
          - action: labelmap # Show all group matches
            regex: __meta_kubernetes_service_label_(.+) # from regex to Prometheus labels
          - source_labels: [__meta_kubernetes_namespace]
            target_label: kubernetes_namespace
          - source_labels: [__meta_kubernetes_service_name]
            target_label: kubernetes_name

      - job_name: "post-endpoints"
        kubernetes_sd_configs:
          - role: endpoints
        relabel_configs:
          - source_labels: [__meta_kubernetes_service_label_app]
            action: keep
            regex: reddit
          - source_labels: [__meta_kubernetes_service_label_component]
            action: keep
            regex: post
          - action: labelmap # Show all group matches
            regex: __meta_kubernetes_service_label_(.+) # from regex to Prometheus labels
          - source_labels: [__meta_kubernetes_namespace]
            target_label: kubernetes_namespace
          - source_labels: [__meta_kubernetes_service_name]
            target_label: kubernetes_name
```

#### Visualization

Let's put a grafana with helm.
``shell
helm upgrade --install grafana stable/grafana --set "server.adminPassword=admin" \
  -set "server.service.type=NodePort" \
  -set "server.ingress.enabled=true" \
  -set "server.ingress.hosts={reddit-grafana}"
```

##### Thrushes, robberies

And there's a surprise waiting for us: http://reddit-grafana/ returns `default backend - 404`.

After reading a little https://github.com/helm/charts/tree/master/stable/grafana, we conclude:

There's a mistake in the remote sensing.
``shell
helm upgrade --install grafana stable/grafana --set "adminPassword=admin" \
  -set "service.type=NodePort" \
  -set "ingress.enabled=true" \
  -set "ingress.hosts={reddit-grafana}"
```

and get a web interface at http://reddit-grafana/.

Came in, changed the password.

Add prometheus data-source. Find the address from the prometheus server service name.
``shell
kubectl get svc
```
http://prom-prometheus-server

done

Add [most common] (https://grafana.com/grafana/dashboards/315) dashboard for tracking
resource states k8s

Add your own dashboards created earlier (in remote monitoring). They should also successfully display the data.

In the dashboard `UI metrics` it was necessary to replace the parameter `job="ui" with `component="ui".

The rest is going on.


#### Templating

At the moment, the charts related to the application simultaneously display the values of metrics from all sources at once. With a large number of environments and their dynamic changes, it makes sense to make the setup of our dashboards in Grafana dynamic and convenient.

This can be done in our case with the help of the mechanism of templating.

#### UI metrics

Let's create a new variable.

| Key | Value |
| ------------------ | ---------------------------- |
| Name | namespace |
| Type | Query |
| Label | env |
| Datasource | Prometheus |
| Refresh | On Dashboard Load |
| Query | `label_values(namespace)` |
| Regex | `/.+/` all non-empty values |.
| Sort | Alphabetical (asc) |
| Multi-value | true |
| Include All option | true |

We have a list with the values of the variable.

So far, they're useless. For their use to have an effect, you need to template requests to Prometheus


- Title: `UI http request response time 95 quantile ($namespace) `
- Metrics: `histogram_quantile(0.95, sum(rate(ui_request_response_time_bucket{kubernetes_namespace=~"$namespace"}[5m])) by (le))`.

- Title: `UI http count ($namespace) `
- Metrics: `rate(ui_request_count{kubernetes_namespace=~"$namespace",http_status=~"^[45].*"}[1m])`.

- Title: `UI http requests count ($namespace) `
- Metrics: `rate(ui_request_count{kubernetes_namespace=~"$namespace",component="ui"}[1m])`.

The dashboard was saved in [monitoring/grafana/dashboards/k8s_UI_Service_Monitoring.json].

#### Business Logic Monitoring

Let's create a new variable.

| Key | Value |
| ------------------ | ---------------------------- |
| Name | namespace |
| Type | Query |
| Label | env |
| Datasource | Prometheus |
| Refresh | On Dashboard Load |
| Query | `label_values(namespace)` |
| Regex | `/.+/` all non-empty values |.
| Sort | Alphabetical (asc) |
| Multi-value | true |
| Include All option | true |

We have a list with the values of the variable.

So far, they're useless. For their use to have an effect, you need to template requests to Prometheus

- Title: `Post count ($namespace) `
- Metrics: `rate(post_count{kubernetes_namespace=~"$namespace"}[1h])`.

- Title: `Comment count ($namespace) `
- Metrics: `rate(comment_count{kubernetes_namespace=~"$namespace"}[1h])`.

Dashboard was saved in [monitoring/grafana/dashboards/k8s_Business_Logic_Monitoring.json].

#### Mixed charts

Import the following chart: https://grafana.com/grafana/dashboards/741.

Interesting figure `Deployment memory usage` = 119%. It's a rather strange figure.

This graph uses both metrics and templates from cAdvisor and kube-state-metrics to display summary information on deployments.


### Task from \*: alertmanager

In general, the principles of working with tools have not changed. Only features have been added, so we can use the old developments for k8s as well.

Task: run alertmanager in k8s and configure rules to control availability of api server and k8s hosts

[Rule Description Format](https://prometheus.io/docs/prometheus/latest/configuration/alerting_rules/)

Change `kubernetes/Charts/prometheus/custom_values.yml`.
``Yaml
Alertmanager:
  enabled: true
  ...
  ...ingress:
    enabled: true
    Hosts:
      - reddit-alertmanager
    ...
  service:
    type: LoadBalancer
    ...
```

Deposit .
``shell
cd kubernetes/Charts/prometheus
helm upgrade prom . -f custom_values.yml --install
```

When trying to go to http://reddit-alertmanager/, we see error 503: Service Temporarily Unavailable.
Cause: `Error syncing load balancer: failed to ensure a static IP for load balancer (adff8df779459482fad7d84091869a95(default/prom-prometheus-alertmanager)): error creating gce static IP address: googleapi: Error 403: QUOTA_EXCEEDED - Quota 'STATIC_ADDRESSES' exceeded.  Limit: 1.0 in region us-central1.`.

Let's try it in a different way.
``Yaml
Alertmanager:
  service:
    type: ClusterIP
```
```
Error: UPGRADE FAILED: cannot patch "prom-prometheus-alertmanager" with kind Service: Service "prom-prometheus-alertmanager" is invalid: spec.ports[0]. nodePort: Forbidden: may not be used when `type' is 'ClusterIP'.
```

Let's do the nginx-ingress-controller.

#### nginx-ingress-controller

Added chart `kubernetes/Charts/ingress-nginx`.
```
ingress-nginx
├── Chart.yaml
└── values.yaml

0 directories, 2 files
```
`Chart.yaml`
``Yaml
---
apiVersion: v2
name: nginx-ingress
version: 0.1.0
description: cluster-wide nginx ingress
I'm not:
  - name: Aleksey Koloskov
    email: vsyscoder@gmail.com

I'm sorry:
  - name: nginx-ingress
    version: 1.30.0
    repository: https://kubernetes-charts.storage.googleapis.com/
```

`values.yaml`
``Yaml
---
nginx-ingress:
  publishService:
    enabled: true
  rbac:
    create: false
  Oh..:
    service:
      loadBalancerIP:
    scope:
      enabled: true
      namespace:
```

Created `kubernetes/Charts/Makefile`
``makefile
NS?=default

update_deps: clean_deps
	cd ./reddit &&helm dep update
	cd ./ingress-nginx &&helm dep update

clean_deps:
	rm -rf ./reddit/charts || true
	rm -rf ./ingress-nginx/charts || true

# install nginx-ingress
install_nginx:
	helm upgrade \
		--install \
		-set nginx-ingress.controller.scope.enabled=true \.
		--set nginx-ingress.controller.scope.namespace=$(NS) \.
		--namespace $(NS) \.
		nginx-ingress-$(NS) \
		./ingress-nginx
```

Installed nginx-ingress-controller
``shell
make update_deps
make install_nginx NS=default
```
``log
helm upgrade \
        --install \
        -set nginx-ingress.controller.scope.enabled=true \.
        --set nginx-ingress.controller.scope.namespace=default \
        --namespace default \
        nginx-ingress-default \
        ./ingress-nginx
Release "nginx-ingress-default" does not exist. Installing it now.
NAME: nginx-ingress-default
LAST DEPLOYED: Fri Feb 21 22:36:03 2020
NAMESPACE: default
STATUS: deployed
REVISION: 1
TEST SUITE: None
```

We prescribe annotations for monitoring services
``Yaml
Alertmanager:
  ingress:
    annotations:
      kubernetes.io/ingress.class: nginx
  service:
    type: LoadBalancer
...
server:
  ingress:
    annotations:
      kubernetes.io/ingress.class: nginx
```

In `Kubernetes/Charts/Makefile` added a target
``makefile
# deploy prometheus
deploy_prometheus:
	helm upgrade \
		--install \
		-f ./prometheus/custom_values.yml \.
    --namespace default \
		prom \
		./prometheus
```

Deploymer prometheus
``shell
make deploy_prometheus
```

Here the analysis of `kubectl get service` suddenly showed the presence of two nginx-ingress-controllers... There's a suspicion that mine was redundant ^_^...
``log
...
nginx-ingress-default-controller LoadBalancer 10.4.3.90 <pending> 80:31784/TCP,443:30099/TCP 27m
nginx-ingress-default-backend ClusterIP 10.4.0.73 <none> 80/TCP 27m
nginx-nginx-ingress-controller LoadBalancer 10.4.7.187 34.69.197.128 80:32087/TCP,443:30552/TCP 5d6h
nginx-nginx-ingress-default-backend ClusterIP 10.4.5.206 <none> 80/TCP 5d6h
```

We'll have to uninstall)).

Add to `Kubernetes/Charts/Makefile` target
``makefile
# uninstall nginx-ingress
uninstall_nginx:
	helm uninstall --namespace $(NS) nginx-ingress-$(NS)
```

And let's uninstall(((())
``shell
make uninstall_nginx NS=default
```
``shell
kubectl get service
```
``log
kubectl get service            
NAME TYPE CLUSTER-IP EXTERNAL-IP PORT(S) AGE
grafana NodePort 10.4.7.117 <none> 80:31701/TCP 3d
kubernetes ClusterIP 10.4.0.1 <none> 443/TCP 5d7h
nginx-nginx-ingress-controller LoadBalancer 10.4.7.187 34.69.197.128 80:32087/TCP,443:30552/TCP 5d6h
nginx-nginx-ingress-default-backend ClusterIP 10.4.5.206 <none> 80/TCP 5d6h
prom-prometheus-alertmanager LoadBalancer 10.4.2.75 <pending> 80:32024/TCP 49m
prom-prometheus-kube-state-metrics ClusterIP None <none> 80/TCP,81/TCP 5d1h
prom-prometheus-node-exporter ClusterIP None <none> 9100/TCP 5d
prom-prometheus-server LoadBalancer 10.4.15.25 34.67.57.194 80:31921/TCP 5d5h
reddit-test-comment ClusterIP 10.4.7.46 <none> 9292/TCP 3d1h
reddit-test-mongodb ClusterIP 10.4.0.108 <none> 27017/TCP 3d1h
reddit-testpost ClusterIP 10.4.12.14 <none> 5000/TCP 3d1h
reddit-test-ui NodePort 10.4.14.209 <none> 9292:31304/TCP 3d1h
```

now it all looks a little more decent.)

Check out .

http://reddit-alertmanager

And now there's... Looks like I jumped in the wrong steppe...
``shell
kubectl describe service prom-prometheus-alertman
```
``log
Error syncing load balancer: failed to ensure load balancer: failed to ensure a static IP for load balancer (adff8df779459482fad7d84091869a95(default/prom-prometheus-alertmanager)): error creating gce static IP address: googleapi: Error 403: QUOTA_EXCEEDED - Quota 'STATIC_ADDRESSES' exceeded.  Limit: 1.0 in region us-central1.
```

What does that have to do with the ip, though? We'll be fine with a dynamic one... Let's try to make a change...

We'll add a `Kubernetes/Charts/Makefile` target
``makefile
# uninstall prometheus
uninstall_prometheus:
	helm uninstall --namespace default prom
```

And we're going to change.
``shell
make uninstall_prometheus
# ...wait for removal
make deploy_prometheus
# done
```

No allertmanager's gonna make a mistake.
``shell
kubectl logs prom-prometheus-alertmanager-5fb4dd8574-6mzfw -c prometheus-alertmanager
```
``log
flag provided but not defined: -cluster.advertise-address
...
```

apparently because the server's serial is still `pending`.
``log
prom-prometheus-server LoadBalancer 10.4.11.106 <pending> 80:30165/TCP 5m23s
```

Something's missing our ip addresses.
``shell
kubectl describe service prom-prometheus-server
```
``log
Normal EnsuringLoadBalancer 43s (x7 over 6m11s) service controller Ensuring load balancer
  Warning SyncLoadBalancerFailed 41s (x7 over 6m9s) service controller Error syncing load balancer: failed to ensure a static IP for load balancer (a9642f8c6a0d149c5bb046eecfd6fd9a(default/prom-prometheus-server)): error creating gce static IP address: googleapi: Error 403: QUOTA_EXCEEDED - Quota 'STATIC_ADDRESSES' exceeded.  Limit: 1.0 in region us-central1.
```

Stop putting up with this! Let's install `service.type: NodePort' for the prometheus `server' and `alertmanager' services so as not to take up static ip.

`kubernetes/Charts/prometheus/custom_values.yml`.
``Yaml
aletrmanager:
  service:
    type: NodePort
...
server:
  service:
    type: NodePort
```

And after applying the changes.
``shell
make deploy_prometheus
```
we've got the prometheus-server back on line.

#### Fix alertmanager

But the alert-manager never wants to stick his face out ^_^.

nginx-ingress-controller says `503 Service Temporarily Unavailable`

And that's because... We see a mistake in the logs...
``shell
kubectl logs prom-prometheus-alertmanager-5fb4dd8574-5tr56 prometheus-alertmanager
```
``log
flag provided but not defined: -cluster.advertise-address
```

The value of the flag `cluster.advertise-address`
``shell
kubectl describe pod prom-prometheus-alertmanager-5
fb4dd8574-5tr56
```
``log
...
Containers:
  prometheus-alertmanager:
    ...
    -cluster.Multi-Attach error for volume "pvc-1cba0a70-2b87-4e67-afec-f1f7b0876f93" Volume is already used by pod(s) prometheus-alertmanager-5fb4dd8574-5tr56=$(POD_IP):6783
...
```

But we don't have an alertmanager-office cluster, and if we make it a `replicaCount: 1', the second one won't take off because it can't use the same volume.
``log
Multi-Attach error for volume "pvc-1cba0a70-2b87-4e67-afec-f1f7b0876f93" Volume is already used by pod(s) prom-prometheus-alertmanager-5fb4dd8574-5tr56
```

It makes sense to remove this parameter, which we will do in `kubernetes/Charts/prometheus/templates/alertmanager-statefulset.yaml` by commenting on line 53.
``Yaml
...
          args:
            --config.file=/etc/config/{{ .Values.alertmanager.configFileName }}.
            -storage.path={{ .Values.alertmanager.persistentVolume.mountPath }}.
            #- --cluster.advertise-address=$(POD_IP):6783
```

but now we get the same situation and something weird in the log.
``shell
kubectl logs -f prom-prometheus-alertmanager-567447967c-5tgct prometheus-alertmanager
```
``log
level=info ts=2020-02-23T20:41:52.492813385Z caller=main.go:155 msg="Starting Alertmanager" version="(version=0.10.0, branch=HEAD, revision=133c888ef3644b47a52acbaeffb09f4cc637df1b)".
level=info ts=2020-02-23T20:41:52.492891792Z caller=main.go:156 build_context="(go=go1.9.2, user=root@01302b7cd08a, date=20171109-15:34:53)".
level=info ts=2020-02-23T20:41:52:494359403Z caller=main.go:293 msg="Loading configuration file" file=/etc/config/alertmanager.yml
level=error ts=2020-02-23T20:41:52.494481786Z caller=main.go:296 msg="Loading configuration file failed" file=/etc/config/alertmanager.yml err="yaml: unmarshal errors:\n line 1: cannot unmarshal !str `global:...` into config.plain".
```

Prri replacing `$(POD_IP)` with `127.0.0.1`, we get a strange result again.
``log
flag provided but not defined: -cluster.advertise-address
```
Conclusion: `$(POD_IP)` it is possible and not empty, but the parameter is transferred by the wrong address...

Further dancing with a tambourine did not bring the result, the same error.

After updating alertmanager to the current version `v0.20.0 ` (by remote control was `v0.10.0 `), it was possible to get started, but the adventures with config.

As a result, we came to the working version.
``Yaml
Alertmanager:
  image:
    tag: v0.20.0
  baseURL: "http://reddit-alertmanager"
  service:
    type: NodePort
  ...
server:
  service:
    type: NodePort
  ...
AlertmanagerFiles:
  alertmanager.yml:
    receivers:
      - name: default-receiver
        slack_configs:
          - api_url: "https://hooks.slack.com/services/hereisasecret"
            channel: "#vscoder-k5"
            send_resolved: true

    The route:
      group_wait: 10s
      group_interval: 5m
      default-receiver
      repeat_interval: 3h
```

and you can finally see the web interface at http://reddit-alertmanager.


#### Alert rules

Let's add a couple of alerts.

`custom-values.yml`
``Yaml
...
## Prometheus server ConfigMap entries
##
serverFiles:
  alerts: {}
  Rules: {}

  ## Alerts configuration
  ## Ref: https://prometheus.io/docs/prometheus/latest/configuration/alerting_rules/
  ## alerting_rules.yml: {}
  Alerting_rules.yml:
    groups:
      - name: Instances
        Rules:
          - alert: InstanceDown
            expr: up == 0
            for: 30s
            The labels:
              severity: page
            annotations:
              description: "of job {{{{$labels.job}} has been down for more than five minutes."
              summary: "Instance {{{{$labels.instance}} down."
      - "name." "kubernetes-apps"
        "rules."
          - "alert." "KubePodCrashLooping."
            "annotations."
              "message." 'Pod {{{$labels.namespace }}/{{$labels.pod }}. ({{{$labels.container }}) is restarting {{{printf "%.2f" $value }} times / 5 minutes'.
              "runbook_url." {{"pos(192,210)}"https://github.com/kubernetes-monitoring/kubernetes-mixin/tree/master/runbook.md#alert-name-kubepodcrashlooping."
            "expr." |
              rate(kube_pod_container_status_restarts_total{component="kube-state-metrics"}[15m]). * 60 * 5 > 0
            "for." "15m"
            "labels."
              "severity." "critical"
          - "alert." "KubePodNotReady."
            "annotations."
              "message." "Pod {{{$labels.namespace }}/{{$labels.pod }} has been in a non-ready state for longer than 15 minutes."
              "runbook_url." {{{"pos(192,210)}"https://github.com/kubernetes-monitoring/kubernetes-mixin/tree/master/runbook.md#alert-name-kubepodnotready."
            "expr." |
              sum by (namespace, pod) (max by(namespace, pod) (kube_pod_status_phase{component="kube-state-metrics", phase=~"Pending|Unknown"}) * on(namespace, pod) group_left(owner_kind) max by(namespace, pod, owner_kind) (kube_pod_owner{owner_kind!="Job"}). > 0
            "for." "15m"
            "labels."
              "severity." "critical"
          - "alert." "KubeDeploymentGenerationMismatch."
            "annotations."
              "message." "Deployment generation for {{{$labels.namespace }}/{{$labels.deployment }} does not match, this indicates that the Deployment has failed but has not been rolled back."
              "runbook_url." {{"pos(192,210)}"https://github.com/kubernetes-monitoring/kubernetes-mixin/tree/master/runbook.md#alert-name-kubedeploymentgenerationmismatch."
            "expr." |
              kube_deployment_status_observed_generation{component="kube-state-metrics"}
                !=
              kube_deployment_metadata_generation{component="kube-state-metrics"}
            "for." "15m"
            "labels."
              "severity." "critical"
          - "alert." "KubeDeploymentReplicasMismatch."
            "annotations."
              "message." "Deployment {{{$labels.namespace }}/{{$labels.deployment }} has not matched the expected number of replicas for longer than 15 minutes."
              "runbook_url." {{{"pos(192,210)}"https://github.com/kubernetes-monitoring/kubernetes-mixin/tree/master/runbook.md#alert-name-kubedeploymentreplicasmismatch."
            "expr." |
              kube_deployment_spec_replicas{component="kube-state-metrics"}
                !=
              kube_deployment_status_replicas_available{component="kube-state-metrics"}
            "for." "15m"
            "labels."
              "severity." "critical"
          - "alert." "KubeStatefulSetReplicasMismatch."
            "annotations."
              "message." "StatefulSet {{{$labels.namespace }}/{{$labels.statefulset }} has not matched the expected number of replicas for longer than 15 minutes."
              "runbook_url." "{{{{$labels, statefuls}}: https://github.com/kubernetes-monitoring/kubernetes-mixin/tree/master/runbook.md#alert-name-kubestatefulsetreplicasmismatch.
            "expr." |
              kube_statefulset_status_replicas_ready{component="kube-state-metrics"}
                !=
              kube_statefulset_status_replicas{component="kube-state-metrics"}
            "for." "15m"
            "labels."
              "severity." "critical"
          - "alert." "KubeStatefulSetGenerationMismatch."
            "annotations."
              "message." "StatefulSet generation for {{{$labels.namespace }}/{{$labels.statefulset }} does not match, this indicates that the StatefulSet has failed but has not been rolled back."
              "runbook_url." {{"pos(192,210)}"https://github.com/kubernetes-monitoring/kubernetes-mixin/tree/master/runbook.md#alert-name-kubestatefulsetgenerationmismatch."
            "expr." |
              kube_statefulset_status_observed_generation{component="kube-state-metrics"}
                !=
              kube_statefulset_metadata_generation{component="kube-state-metrics"}
            "for." "15m"
            "labels."
              "severity." "critical"
          - "alert." "KubeStatefulSetUpdateNotRolledOut."
            "annotations."
              "message." "StatefulSet {{{$labels.namespace }}/{{$labels.statefulset }}} update has not been rolled out."
              "runbook_url." {{{{$labels}} "https://github.com/kubernetes-monitoring/kubernetes-mixin/tree/master/runbook.md#alert-name-kubestatefulsetupdatenotrolledout."
            "expr." |
              max without (revision) (
                kube_statefulset_status_current_revision{component="kube-state-metrics"}
                  

                kube_statefulset_status_update_revision{component="kube-state-metrics"}
              )
                *
              (
                kube_statefulset_replicas{component="kube-state-metrics"}
                  !=
                kube_statefulset_status_replicas_updated{component="kube-state-metrics"}
              )
            "for." "15m"
            "labels."
              "severity." "critical"
          - "alert." "KubeDaemonSetRolloutStuck."
            "annotations."
              "message." "Only {{{$value |}} of the desired Pods of DaemonSet {{{$labels.namespace }}/{{{$labels.daemonset }} are scheduled and ready."
              {{{{$labels.daemonset }}"runbook_url." "{{{{$labels}} https://github.com/kubernetes-monitoring/kubernetes-mixin/tree/master/runbook.md#alert-name-kubedaemonsetrolloutstuck.
            "expr." |
              kube_daemonset_status_number_ready{component="kube-state-metrics"}
                /
              kube_daemonset_status_desired_number_scheduled{component="kube-state-metrics"} < 1.00
            "for." "15m"
            "labels."
              "severity." "critical"
          - "alert." "KubeContainerWaiting."
            "annotations."
              "message." "Pod {{{$labels.namespace}}/{{$labels.pod }} container {{{$labels.container}} has been in waiting state for longer than 1 hour."
              "runbook_url." {{"pos(192,210)}"https://github.com/kubernetes-monitoring/kubernetes-mixin/tree/master/runbook.md#alert-name-kubecontainerwaiting."
            "expr." |
              sum by (namespace, pod, container) (kube_pod_container_status_waiting_reason{component="kube-state-metrics"}) > 0
            "for." "1h"
            "labels."
              "severity." "warning"
          - "alert." "KubeDaemonSetNotScheduled."
            "annotations."
              "message." "{{$value }} Pods of DaemonSet {{{$labels.namespace}}/{$labels.daemonset} are not scheduled."
              {{{{$labels.}}"runbook_url." {{{{$labels}} "https://github.com/kubernetes-monitoring/kubernetes-mixin/tree/master/runbook.md#alert-name-kubedaemonsetnotscheduled."
            "expr." |
              kube_daemonset_status_desired_number_scheduled{component="kube-state-metrics"}
                -
              kube_daemonset_status_current_number_scheduled{component="kube-state-metrics"} > 0
            "for." "10m"
            "labels."
              "severity." "warning"
          - "alert." "KubeDaemonSetMisScheduled."
            "annotations."
              "message." "{{$value }} Pods of DaemonSet {{{$labels.namespace}}/{$labels.daemonset} are running where they are not supposed to run."
              "{{{{$labels.daemonset}} are running where they are not supposed to run." {{"pos(192,210)}"https://github.com/kubernetes-monitoring/kubernetes-mixin/tree/master/runbook.md#alert-name-kubedaemonsetmisscheduled."
            "expr." |
              kube_daemonset_status_number_misscheduled{component="kube-state-metrics"} > 0
            "for." "10m"
            "labels."
              "severity." "warning"
      - "name." "kubernetes-resources"
        "rules."
          - "alert." "KubeCPUOvercommit."
            "annotations."
              "message." "Cluster has overcommitted CPU resource requests for Pods and cannot tolerate node failure."
              "runbook_url." "https://github.com/kubernetes-monitoring/kubernetes-mixin/tree/master/runbook.md#alert-name-kubecpuovercommit."
            "expr." |
              sum(namespace:kube_pod_container_resource_requests_cpu_cores:sum)
                /
              sum(kube_node_status_allocatable_cpu_cores)
                >
              (count(kube_node_status_allocatable_cpu_cores)-1) / count(kube_node_status_allocatable_cpu_cores)
            "for." "5m"
            "labels."
              "severity." "warning"
          - "alert." "KubeMemOvercommit."
            "annotations."
              "message." "Cluster has overcommitted memory resource requests for Pods and cannot tolerate node failure."
              "runbook_url." "https://github.com/kubernetes-monitoring/kubernetes-mixin/tree/master/runbook.md#alert-name-kubememovercommit."
            "expr." |
              sum(namespace:kube_pod_container_resource_requests_memory_bytes:sum)
                /
              sum(kube_node_status_allocatable_memory_bytes)
                >
              (count(kube_node_status_allocatable_memory_bytes)-1)
                /
              count(kube_node_status_allocatable_memory_bytes)
            "for." "5m"
            "labels."
              "severity." "warning"
          - "alert." "KubeCPUOvercommit."
            "annotations."
              "message." "Cluster has overcommitted CPU resource requests for Namespaces."
              "runbook_url." "https://github.com/kubernetes-monitoring/kubernetes-mixin/tree/master/runbook.md#alert-name-kubecpuovercommit."
            "expr." |
              sum(kube_resourcequota{component="kube-state-metrics", type="hard", resource="cpu"}")
                /
              sum(kube_node_status_allocatable_cpu_cores)
                > 1.5
            "for." "5m"
            "labels."
              "severity." "warning"
          - "alert." "KubeMemOvercommit."
            "annotations."
              "message." "Cluster has overcommitted memory resource requests for Namespaces."
              "runbook_url." "https://github.com/kubernetes-monitoring/kubernetes-mixin/tree/master/runbook.md#alert-name-kubememovercommit."
            "expr." |
              sum(kube_resourcequota{component="kube-state-metrics", type="hard", resource="memory"})
                /
              sum(kube_node_status_allocatable_memory_bytes{job="node-exporter"}).
                > 1.5
            "for." "5m"
            "labels."
              "severity." "warning"
          - "alert." "KubeQuotaExceeded."
            "annotations."
              "message." "Namespace {{{$labels.namespace }} is using {{{$value |} of its {{{$labels.resource }}} quota."
              "runbook_url." {{{{$labels}} "https://github.com/kubernetes-monitoring/kubernetes-mixin/tree/master/runbook.md#alert-name-kubequotaexceeded."
            "expr." |
              kube_resourcequota{component="kube-state-metrics", type="used"}
                / ignoring(instance, job, type)
              (kube_resourcequota{component="kube-state-metrics", type="hard"} > 0)
                > 0.90
            "for." "15m"
            "labels."
              "severity." "warning"
          - "alert." "CPUThrottlingHigh"
            "annotations."
              "message." "{{{$value | humanizePercentage }}} throttling of CPU in namespace {{{$labels.namespace }}} for container {{{$labels.container }}} in pod {{{$labels.pod }}."
              "runbook_url." {{{"pos(192,210)}"https://github.com/kubernetes-monitoring/kubernetes-mixin/tree/master/runbook.md#alert-name-cputhrottlinghigh."
            "expr." |
              sum(increase(container_cpu_cfs_throttled_periods_total{container!=", }[5m])) by (container, pod, namespace)
                /
              sum(increase(container_cpu_cfs_periods_total{}[5m])) by (container, pod, namespace)
                > ( 25 / 100 )
            "for." "15m"
            "labels."
              "severity." "warning"
      - "name." "kubernetes-storage"
        "rules."
          - "alert." "KubePersistentVolumeUsageCritical."
            "annotations."
              "message." "The PersistentVolume claimed by {{{$labels.persistentvolumeclaim}} in Namespace {{{$labels.namespace }}} is only {{{$value |} free."
              "runbook_url." {{{"pos(192,210)}"https://github.com/kubernetes-monitoring/kubernetes-mixin/tree/master/runbook.md#alert-name-kubepersistentvolumeusagecritical."
            "expr." |
              kubelet_volume_stats_available_bytes{job="kubernetes-nodes"}
                /
              kubelet_volume_stats_capacity_bytes{job="kubernetes-nodes"}
                < 0.03
            "for": "1m"
            "labels."
              "severity." "critical"
          - "alert." "KubePersistentVolumeFullInFourDays."
            "annotations."
              "message." "Based on recent sampling, the PersistentVolume claimed by {{{$labels.persistentvolumeclaim }} in Namespace {{{$labels.namespace }} is expected to fill up within four days. Currently {{{$value | humanizePercentage }} is available."
              "runbook_url." "{{{$value}} https://github.com/kubernetes-monitoring/kubernetes-mixin/tree/master/runbook.md#alert-name-kubepersistentvolumefullinfourdays.
            "expr." |
              (
                kubelet_volume_stats_available_bytes{job="kubernetes-nodes"}
                  /
                kubelet_volume_stats_capacity_bytes{job="kubernetes-nodes"}
              ) < 0.15
              and
              predict_linear(kubelet_volume_stats_available_bytes{job="kubernetes-nodes"}[6h], 4 * 24 * 3600) < 0
            "for." "1h"
            "labels."
              "severity." "critical"
          - "alert." "KubePersistentVolumeErrors."
            "annotations."
              "message." "The persistent volume {{{$labels.persistentvolume }} has status {{{$labels.phase }}."
              {{{{$labels.persistentvolume }}} "runbook_url." {{{{$labels}} "https://github.com/kubernetes-monitoring/kubernetes-mixin/tree/master/runbook.md#alert-name-kubepersistentvolumeerrors."
            "expr." |
              kube_persistentvolume_status_phase{phase=~"Failed|Pending",component="kube-state-metrics"}. > 0
            "for." "5m"
            "labels."
              "severity." "critical"
      - "name." "kubernetes-system"
        "rules."
          - "alert." "KubeVersionMismatch."
            "annotations."
              "message." "There are {{{$value }} different semantic versions of Kubernetes components running."
              "runbook_url." {{{$value }}"https://github.com/kubernetes-monitoring/kubernetes-mixin/tree/master/runbook.md#alert-name-kubeversionmismatch"
            "expr." |
              count(count by (gitVersion) (label_replace(kubernetes_build_info{job!~"kube-dns|coredns"}, "gitVersion","$1", "gitVersion","(v[0-9]*.[0-9]*.[0-9]*).*)). > 1
            "for." "15m"
            "labels."
              "severity." "warning"
          - "alert." "KubeClientErrors"
            "annotations."
              "message." "Kubernetes API server client '{{{$labels.job }}/{{$labels.instance }}' is experiencing {{{$value | humanizePercentage }}}'.
              "runbook_url." {{{$value }}"https://github.com/kubernetes-monitoring/kubernetes-mixin/tree/master/runbook.md#alert-name-kubeclienterrors."
            "expr." |
              (sum(rate(rest_client_requests_total{code=~"5..."}[5m])) by (instance, job)
                /
              sum(rate(rest_client_requests_total[5m])) by (instance, job))
              > 0.01
            "for." "15m"
            "labels."
              "severity." "warning"
      - "name." "kubernetes-apiservers-error"
        "rules."
          - "alert." "ErrorBudgetBurn"
            "annotations."
              "runbook_url." "https://github.com/kubernetes-monitoring/kubernetes-mixin/tree/master/runbook.md#alert-name-errorbudgetburn"
            "expr." |
              (
                status_class_5xx:apiserver_request_total:ratio_rate1h{job="kubernetes-apiservers"} > (14.4*0.010000)
                and
                status_class_5xx:apiserver_request_total:ratio_rate5m{job="kubernetes-apiservers"} > (14.4*0.010000)
              )
              or
              (
                status_class_5xx:apiserver_request_total:ratio_rate6h{job="kubernetes-apiservers"} > (6*0.010000)
                and
                status_class_5xx:apiserver_request_total:ratio_rate30m{job="kubernetes-apiservers"} > (6*0.010000)
              )
            "labels."
              "job." "kubernetes-apiservers"
              "severity." "critical"
          - "alert." "ErrorBudgetBurn"
            "annotations."
              "runbook_url." "https://github.com/kubernetes-monitoring/kubernetes-mixin/tree/master/runbook.md#alert-name-errorbudgetburn"
            "expr." |
              (
                status_class_5xx:apiserver_request_total:ratio_rate1d{job="kubernetes-apiservers"} > (3*0.010000)
                and
                status_class_5xxx:apiserver_request_total:ratio_rate2h{job="kubernetes-apiservers"} > (3*0.010000)
              )
              or
              (
                status_class_5xx:apiserver_request_total:ratio_rate3d{job="kubernetes-apiservers"} > (0.010000)
                and
                status_class_5xx:apiserver_request_total:ratio_rate6h{job="kubernetes-apiservers"} > (0.010000)
              )
            "labels."
              "job." "kubernetes-apiservers"
              "severity." "warning"
          - "expr." |
              sum by (status_class) (
                label_replace(
                  rate(apiserver_request_total{job="kubernetes-apiservers"}[5m].
                ), "status_class", "${1}xx", "code", "([0-9])...").
              )
            "labels."
              "job." "kubernetes-apiservers"
            "record." "status_class:apiserver_request_total:rate5m".
          - "expr." |
              sum by (status_class) (
                label_replace(
                  rate(apiserver_request_total{job="kubernetes-apiservers"}[30m].
                ), "status_class", "${1}xx", "code", "([0-9])...").
              )
            "labels."
              "job." "kubernetes-apiservers"
            "record." "status_class:apiserver_request_total:rate30m".
          - "expr." |
              sum by (status_class) (
                label_replace(
                  rate(apiserver_request_total{job="kubernetes-apiservers"}[1h].
                ), "status_class", "${1}xx", "code", "([0-9])...").
              )
            "labels."
              "job." "kubernetes-apiservers"
            "record." "status_class:apiserver_request_total:rate1h".
          - "expr." |
              sum by (status_class) (
                label_replace(
                  rate(apiserver_request_total{job="kubernetes-apiservers"}[2h].
                ), "status_class", "${1}xx", "code", "([0-9])...").
              )
            "labels."
              "job." "kubernetes-apiservers"
            "record." "status_class:apiserver_request_total:rate2h".
          - "expr." |
              sum by (status_class) (
                label_replace(
                  rate(apiserver_request_total{job="kubernetes-apiservers"}[6h].
                ), "status_class", "${1}xx", "code", "([0-9])...").
              )
            "labels."
              "job." "kubernetes-apiservers"
            "record." "status_class:apiserver_request_total:rate6h".
          - "expr." |
              sum by (status_class) (
                label_replace(
                  rate(apiserver_request_total{job="kubernetes-apiservers"}[1d].
                ), "status_class", "${1}xx", "code", "([0-9])...").
              )
            "labels."
              "job." "kubernetes-apiservers"
            "record." "status_class:apiserver_request_total:rate1d".
          - "expr." |
              sum by (status_class) (
                label_replace(
                  rate(apiserver_request_total{job="kubernetes-apiservers"}[3d].
                ), "status_class", "${1}xx", "code", "([0-9])...").
              )
            "labels."
              "job." "kubernetes-apiservers"
            "record." "status_class:apiserver_request_total:rate3d".
          - "expr." |
              sum(status_class:apiserver_request_total:rate5m{job="kubernetes-apiservers",status_class="5xx"}).
              /
              sum(status_class:apiserver_request_total:rate5m{job="kubernetes-apiservers"}).
            "labels."
              "job." "kubernetes-apiservers"
            "record." "status_class_5xx:apiserver_request_total:rate5m".
          - "expr." |
              sum(status_class:apiserver_request_total:rate30m{job="kubernetes-apiservers",status_class="5xx"}).
              /
              sum(status_class:apiserver_request_total:rate30m{job="kubernetes-apiservers"}).
            "labels."
              "job." "kubernetes-apiservers"
            "record." "status_class_5xx:apiserver_request_total:ratio_rate30m".
          - "expr." |
              sum(status_class:apiserver_request_total:rate1h{job="kubernetes-apiservers",status_class="5xx"}).
              /
              sum(status_class:apiserver_request_total:rate1h{job="kubernetes-apiservers"}).
            "labels."
              "job." "kubernetes-apiservers"
            "record." "status_class_5xx:apiserver_request_total:rate1h".
          - "expr." |
              sum(status_class:apiserver_request_total:rate2h{job="kubernetes-apiservers",status_class="5xx"}).
              /
              sum(status_class:apiserver_request_total:rate2h{job="kubernetes-apiservers"}).
            "labels."
              "job." "kubernetes-apiservers"
            "record." "status_class_5xx:apiserver_request_total:rate2h".
          - "expr." |
              sum(status_class:apiserver_request_total:rate6h{job="kubernetes-apiservers",status_class="5xx"}).
              /
              sum(status_class:apiserver_request_total:rate6h{job="kubernetes-apiservers"}).
            "labels."
              "job." "kubernetes-apiservers"
            "record." "status_class_5xx:apiserver_request_total:rate6h".
          - "expr." |
              sum(status_class:apiserver_request_total:rate1d{job="kubernetes-apiservers",status_class="5xx"}).
              /
              sum(status_class:apiserver_request_total:rate1d{job="kubernetes-apiservers"}).
            "labels."
              "job." "kubernetes-apiservers"
            "record." "status_class_5xx:apiserver_request_total:ratio_rate1d".
          - "expr." |
              sum(status_class:apiserver_request_total:rate3d{job="kubernetes-apiservers",status_class="5xx"}).
              /
              sum(status_class:apiserver_request_total:rate3d{job="kubernetes-apiservers"}).
            "labels."
              "job." "kubernetes-apiservers"
            "record." "status_class_5xx:apiserver_request_total:ratio_rate3d".
      - "name." "kubernetes-system-apiserver"
        "rules."
          - "alert." "KubeAPILatencyHigh."
            "annotations."
              "message." "The API server has an abnormal latency of {{{$value }}} seconds for {{{$labels.verb }}. {{{$labels.resource}}."
              "runbook_url." {{"pos(192,210)}"https://github.com/kubernetes-monitoring/kubernetes-mixin/tree/master/runbook.md#alert-name-kubeapilatencyhigh."
            "expr." |
              (
                cluster:apiserver_request_duration_seconds:mean5m{job="kubernetes-apiservers"}
                >
                on (verb) group_left()
                (
                  avg by (verb) (cluster:apiserver_request_duration_seconds:mean5m{job="kubernetes-apiservers"} >= 0)
                  +
                  2*stddev by (verb) (cluster:apiserver_request_duration_seconds:mean5m{job="kubernetes-apiservers"}. >= 0)
                )
              ) > on (verb) group_left()
              1.2 * avg by (verb) (cluster:apiserver_request_duration_seconds:mean5m{job="kubernetes-apiservers"} >= 0)
              and on (verb,resource)
              cluster_quantile:apiserver_request_duration_seconds:histogram_quantile{job="kubernetes-apiservers",quantile="0.99"}
              >
              1
            "for." "5m"
            "labels."
              "severity." "warning"
          - "alert." "KubeAPILatencyHigh."
            "annotations."
              "message." "The API server has a 99th percentile latency of {{{$value }} seconds for {{{$labels.verb }}. {{{$labels.resource}}."
              "runbook_url." {{"pos(192,210)}"https://github.com/kubernetes-monitoring/kubernetes-mixin/tree/master/runbook.md#alert-name-kubeapilatencyhigh."
            "expr." |
              cluster_quantile:apiserver_request_duration_seconds:histogram_quantile{job="kubernetes-apiservers",quantile="0.99"} > 4
            "for." "10m"
            "labels."
              "severity." "critical"
          - "alert." "KubeAPIErrorsHigh."
            "annotations."
              "message." "API server is returning for {{$value | humanizePercentage}} of requests".
              "runbook_url": {{{$value }}"https://github.com/kubernetes-monitoring/kubernetes-mixin/tree/master/runbook.md#alert-name-kubeapierrorshigh"
            "expr." |
              sum(rate(apiserver_request_total{job="kubernetes-apiservers",code=~"5..."}[5m])).
                /
              sum(rate(apiserver_request_total{job="kubernetes-apiservers"}[5m]). > 0.03
            "for." "10m"
            "labels."
              "severity." "critical"
          - "alert." "KubeAPIErrorsHigh."
            "annotations."
              "message." "API server is returning for {{$value | humanizePercentage}} of requests".
              "runbook_url": {{{$value }}"https://github.com/kubernetes-monitoring/kubernetes-mixin/tree/master/runbook.md#alert-name-kubeapierrorshigh"
            "expr." |
              sum(rate(apiserver_request_total{job="kubernetes-apiservers",code=~"5..."}[5m])).
                /
              sum(rate(apiserver_request_total{job="kubernetes-apiservers"}[5m]). > 0.01
            "for." "10m"
            "labels."
              "severity." "warning"
          - "alert." "KubeAPIErrorsHigh."
            "annotations."
              "message." "API server is returning for {{{$value | humanizePercentage}} requests for {{{$labels.verb}}. {{$labels.resource}} {{{$labels.subresource}}."
              "runbook_url." {{"pos(192,210)}"https://github.com/kubernetes-monitoring/kubernetes-mixin/tree/master/runbook.md#alert-name-kubeapierrorshigh."
            "expr." |
              sum(rate(apiserver_request_total{job="kubernetes-apiservers",code=~"5..."}[5m])) by (resource,subresource,verb)
                /
              sum(rate(apiserver_request_total{job="kubernetes-apiservers"}[5m])) by (resource,subresource,verb) > 0.10
            "for": "10m"
            "labels."
              "severity." "critical"
          - "alert." "KubeAPIErrorsHigh."
            "annotations."
              "message." "API server is returning for {{{$value | humanizePercentage}} requests for {{{$labels.verb}}. {{$labels.resource}} {{{$labels.subresource}}."
              "runbook_url." {{"pos(192,210)}"https://github.com/kubernetes-monitoring/kubernetes-mixin/tree/master/runbook.md#alert-name-kubeapierrorshigh."
            "expr." |
              sum(rate(apiserver_request_total{job="kubernetes-apiservers",code=~"5..."}[5m])) by (resource,subresource,verb)
                /
              sum(rate(apiserver_request_total{job="kubernetes-apiservers"}[5m])) by (resource,subresource,verb) > 0.05
            "for": "10m"
            "labels."
              "severity." "warning"
          - "alert." "KubeClientCertificateExpiration."
            "annotations."
              "message." "A client certificate used to authenticate to the apiserver is expiring in less than 7.0 days."
              "runbook_url." "https://github.com/kubernetes-monitoring/kubernetes-mixin/tree/master/runbook.md#alert-name-kubeclientcertificateexpiration."
            "expr." |
              apiserver_client_certificate_expiration_seconds_count{job="kubernetes-apiservers"} > 0 and on(job) histogram_quantile(0.01, sum by (job, le) (rate(apiserver_client_certificate_expiration_seconds_bucket{job="kubernetes-apiservers"}[5m])). < 604800
            "labels."
              "severity." "warning"
          - "alert." "KubeClientCertificateExpiration."
            "annotations."
              "message." "A client certificate used to authenticate to the apiserver is expiring in less than 24.0 hours."
              "runbook_url." "https://github.com/kubernetes-monitoring/kubernetes-mixin/tree/master/runbook.md#alert-name-kubeclientcertificateexpiration."
            "expr." |
              apiserver_client_certificate_expiration_seconds_count{job="kubernetes-apiservers"} > 0 and on(job) histogram_quantile(0.01, sum by (job, le) (rate(apiserver_client_certificate_expiration_seconds_bucket{job="kubernetes-apiservers"}[5m])). < 86400
            "labels."
              "severity." "critical"
          - "alert." "KubeAPIDown"
            "annotations."
              "message." "KubeAPI has disappeared from Prometheus target discovery."
              "runbook_url." "https://github.com/kubernetes-monitoring/kubernetes-mixin/tree/master/runbook.md#alert-name-kubeapidown."
            "expr." |
              absent(up{job="kubernetes-apiservers"} == 1)
            "for." "15m"
            "labels."
              "severity." "critical"
      - "name." "kubernetes-system-kubelet"
        "rules."
          - "alert." "KubeNodeNotReady."
            "annotations."
              "message." "{{{$labels.node}} has been unready for more than 15 minutes."
              "runbook_url." "{{{{$labels.node}}
            "expr." |
              kube_node_status_condition{component="kube-state-metrics",condition="Ready",status="true"} == 0
            "for." "15m"
            "labels."
              "severity." "warning"
          - "alert." "KubeNodeUnreachable."
            "annotations."
              "message." "{{{$labels.node}} is unreachable and some workloads may be rescheduled."
              "runbook_url." {{{{$labels }}"https://github.com/kubernetes-monitoring/kubernetes-mixin/tree/master/runbook.md#alert-name-kubenodeunreachable"
            "expr." |
              kube_node_spec_taint{component="kube-state-metrics",key="node.kubernetes.io/unreachable",effect="NoSchedule"} == 1
            "for." "2m"
            "labels."
              "severity." "warning"
          - "alert." "KubeletTooManyPods."
            "annotations."
              "message." "Kubelet '{{$labels.node }}' is running at {{{$value |} of its Pod capacity."
              "runbook_url": {{{$value }}"https://github.com/kubernetes-monitoring/kubernetes-mixin/tree/master/runbook.md#alert-name-kubelettoomanypods."
            "expr": |
              max(max(kubelet_running_pod_count{job="kubernetes-nodes"}) by(instance) * on(instance) group_left(node) kubelet_node_name{job="kubernetes-nodes"}) by(node) / max(kube_node_status_capacity_pods{component="kube-state-metrics"}) by(node) > 0.95.
            "for": "15m"
            "labels."
              "severity": "warning"

  ## Records configuration
  ## Ref: https://prometheus.io/docs/prometheus/latest/configuration/recording_rules/
  recording_rules.yml: {}

  prometheus.yml:
    rule_files:
      - /etc/config/recording_rules.yml
      - /etc/config/alerting_rules.yml
      # - /etc/config/rules
      # - /etc/config/alerts
    ...
```

After application, we see the alerts in the chat room.
``shell
make deploy_prometheus
```

### Task from \ ##: Prometheus operator

- Install the Prometheus Operator in the cluster (you can use [helm chart] (https://github.com/helm/charts/tree/master/stable/prometheus-operator)).

- Configure post endpoints monitoring

- Attach the serviceMonitor manifest you are using

#### Install prometheus operator

The directory was created. 
``log
kubernetes/Charts/prometheus-operator
├── Chart.yaml
└── values.yaml

0 directories, 2 files
```

`kubernetes/Charts/prometheus-operator/Chart.yaml`
``Yaml
---
apiVersion: v2
name: prometheus-operator
version: 0.1.0
description: prometheus-operator by bitnami
I'm not:
  - name: Aleksey Koloskov
    email: vsyscoder@gmail.com

I'm sorry:
  - name: prometheus-operator
    version: 8.9.2
    repository: https://kubernetes-charts.storage.googleapis.com/
```

`kubernetes/Charts/prometheus-operator/values.yaml`
``Yaml
---
prometheus-operator:
  prometheus:
    ingress:
      enabled: true
      annotations:
        kubernetes.io/ingress.class: nginx
      Hosts:
        - reddit-prometheus

  Alertmanager:
    ingress:
      enabled: true
      annotations:
        kubernetes.io/ingress.class: nginx
      Hosts:
        - reddit-alertmanager

  grafana:
    ingress:
      enabled: true
      annotations:
        kubernetes.io/ingress.class: nginx
      Hosts:
        - reddit-grafana
```

Changed `kubernetes/Charts/Makefile`.
``makefile
# The installation/cleaning goals have been changed depending on
update_deps: clean_deps
	cd ./reddit &&helm dep update
	cd ./ingress-nginx &&helm dep update
	cd ./prometheus-operator &&helm dep update

clean_deps:
	rm -rf ./reddit/charts || true
	rm -rf ./ingress-nginx/charts || true
	rm -rf ./prometheus-operator/charts || true

...
# Targets have been created
# deploy prometheus operator
deploy_prometheus_operator:
	helm upgrade \
		--install \
		--namespace default \
		prometheus-operator \
		./prometheus-operator

# uninstall prometheus operator
uninstall_prometheus_operator:
	helm uninstall --namespace default prometheus-operator
```

Operator installed
``shell
make update_deps
make deploy_prometheus_operator
```
``log
helm upgrade \
        --install \
        --namespace default \
        prometheus-operator \
        ./prometheus-operator
Release "prometheus-operator" does not exist. Installing it now.
manifest_sorter.go:175: info: skipping unknown hook: "crd-install"
manifest_sorter.go:175: info: skipping unknown hook: "crd-install"
manifest_sorter.go:175: info: skipping unknown hook: "crd-install"
manifest_sorter.go:175: info: skipping unknown hook: "crd-install"
manifest_sorter.go:175: info: skipping unknown hook: "crd-install"
NAME: prometheus-operator
LAST DEPLOYED: Tue Feb 25 00:13:47 2020
NAMESPACE: default
STATUS: deployed
REVISION: 1
```

As you can see from the log, no CRDs were installed because helm3. There is [workaround] in the documentation on this topic (https://github.com/helm/charts/blob/master/stable/prometheus-operator/README.md#helm-fails-to-create-crds).

In `kubernetes/Charts/Makefile` the corresponding workaround is implemented.
``makefile
# deploy prometheus operator
deploy_prometheus_operator: install_prometheus_operator_crds
	helm upgrade \
		--install \
		-set prometheus-operator.prometheusOperator.createCustomResource=false \.
		--namespace default \
		prometheus-operator \
		./prometheus-operator

# uninstall prometheus operator
uninstall_prometheus_operator:
	helm uninstall --namespace default prometheus-operator
	$(MAKE) uninstall_prometheus_operator_crds

# install prometheus operator CRDs
install_prometheus_operator_crds:
	kubectl apply -n default -f https://raw.githubusercontent.com/coreos/prometheus-operator/release-0.35/example/prometheus-operator-crd/monitoring.coreos.com_alertmanagers.yaml
	kubectl apply -n default -f https://raw.githubusercontent.com/coreos/prometheus-operator/release-0.35/example/prometheus-operator-crd/monitoring.coreos.com_podmonitors.yaml
	kubectl apply -n default -f https://raw.githubusercontent.com/coreos/prometheus-operator/release-0.35/example/prometheus-operator-crd/monitoring.coreos.com_prometheuses.yaml
	kubectl apply -n default -f https://raw.githubusercontent.com/coreos/prometheus-operator/release-0.35/example/prometheus-operator-crd/monitoring.coreos.com_prometheusrules.yaml
	kubectl apply -n default -f https://raw.githubusercontent.com/coreos/prometheus-operator/release-0.35/example/prometheus-operator-crd/monitoring.coreos.com_servicemonitors.yaml

# uninstall prometheus operator CRDs
uninstall_prometheus_operator_crds:
	kubectl delete -n default -f https://raw.githubusercontent.com/coreos/prometheus-operator/release-0.35/example/prometheus-operator-crd/monitoring.coreos.com_alertmanagers.yaml
	kubectl delete -n default -f https://raw.githubusercontent.com/coreos/prometheus-operator/release-0.35/example/prometheus-operator-crd/monitoring.coreos.com_podmonitors.yaml
	kubectl delete -n default -f https://raw.githubusercontent.com/coreos/prometheus-operator/release-0.35/example/prometheus-operator-crd/monitoring.coreos.com_prometheuses.yaml
	kubectl delete -n default -f https://raw.githubusercontent.com/coreos/prometheus-operator/release-0.35/example/prometheus-operator-crd/monitoring.coreos.com_prometheusrules.yaml
	kubectl delete -n default -f https://raw.githubusercontent.com/coreos/prometheus-operator/release-0.35/example/prometheus-operator-crd/monitoring.coreos.com_servicemonitors.yaml
```

Operator installed `make deploy_prometheus_operator`

See graph dashboards http://reddit-grafana (default password is also available in the documentation, search or set (`grafana.adminPassword`). General impression: delight, with minimal effort we have a huge amount of information about our cluster))).

Next:
- Configure post endpoints monitoring
- Attach the serviceMonitor manifest you are using

#### ServiceMonitor

Very helpful documentation https://github.com/coreos/prometheus-operator/blob/master/Documentation/troubleshooting.md.

So, what was done to get the business metrics of the component `post` on the graphan dashboard:

Changed the chart of the component `post`.
`kubernetes/Charts/post/templates/service.yaml`
``Yaml
---
apiVersion: v1
kind: Service
metadata:
  name: {{{ template "post.fullname"}. }}
  The labels:
    app: reddit
    post
    release: {{ .Release.Name }}
spec:
  type: ClusterIP
  ports:
  - name: http # Added endpoint name to specify in ServiceMonitor
    port: {{{ .Values.service.externalPort }}.
    protocol: TCP
    targetPort: {{{ .Values.service.internalPort }}.
  Selector:
    app: reddit
    post
    release: {{ .Release.Name }}
...
```

Incremented version of the chart ` Kubernetes/Charts/post/Chart.yaml`.
``Yaml
---
name: post
version: 1.1.0
description: OTUS reddit application Post
I'm not:
  - name: Someone
    email: my@mail.com
appVersion: 1.0
```

The dependency version in `kubernetes/Charts/reddit/requirements.yaml` has been updated.
``Yaml
---
I'm sorry:
  ...
  - name: post
    version: 1.1.0
    repository: "file://.../post"
```

Dependencies have been established
``shell
helm dependency update --debug ./reddit
```

HINT: see _Service Monitor Selector_: `kubectl describe prometheus prometheus-operator-prometheus`.

Created `kubernetes/reddit/post-servicemonitor.
``Yaml
---
apiVersion: monitoring.coreos.com/v1
kind: ServiceMonitor
metadata:
  name: reddit-post
  The labels:
    app: reddit
    release: prometheus-operator # Must match with Service Monitor Selector: Match Labels: Release: prometheus-operator
spec:
  jobLabel: component # from which label to take the name job
  selector: # selector for service
    matchLabels: # it is possible to also specify matchName
      app: reddit
      post
  namespaceSelector:
    matchNames: # namespaces, you can specify any
      - default
      - production
      - staging
  endpoints:
    - port: http # must match the service spec.ports[].name
      path: /metrics # url path to get metrics
      scheme: http # wiring diagram, http/https
      interval: 10s # survey interval
```

The application has since been redesigned
``shell
helm upgrade reddit-test ./reddit --install
helm upgrade staging --namespace staging ./reddit --install
helm upgrade production --namespace production ./reddit --install
```

And the ServiceMonitor was created
``shell
kubectl apply -f ../reddit/post-servicemonitor.yaml
```

Now we see the target at http://reddit-prometheus.
```
default/reddit-post/0 (3/3 up)
```

Then we import into the graph dashboard `monitoring/grafana/dashboards/Business_Logic_Monitoring.json` (yes, it is the previous dashboard with the label `namespace` and not `kubernetes_namespace`) and see on the chart _Post count_ number of new posts... Profit!

It took more time than I expected... Next is logging.

### Logging

#### Preparations

1. This part of remote sensing is recommended to be poured out after implementation of remote sensing No. 25 (according to logging), the results of which are used in this work.
2. Performance of this part of the ERS is not mandatory.
3. Add the label of the most powerful node in the cluster (already done earlier when creating the infrastructure)


#### Stack

Logging in k8s will be built using the already known EFK stack:

- ElasticSearch - database + search engine
- Fluentd - Spreader (sender) and Log aggregator
- Kibana - web-interface for requests to the storage and displaying their results


#### EFK

Create files in a new folder `kubernetes/efk/`.

`fluentd-ds.yaml`
``Yaml
---
apiVersion: apps/v1beta2
kind: DaemonSet
metadata:
  name: fluentd-es-v2.0.2
  labels:
    k8s-app: fluentd-es
    version: v2.0.2
    kubernetes.io/cluster service: "true"
    addonmanager.kubernetes.io/mode: Reconcile
spec:
  selector:
    matchLabels:
      k8s-app: fluentd-es
      version: v2.0.2
  template:
    metadata:
      labels:
        k8s-app: fluentd-es
        kubernetes.io/cluster service: "true"
        version: v2.0.2
      # This annotation ensures that fluentd does not get evicted if the node
      # supports critical pod annotation based priority scheme.
      # Note that this does not guarantee on the nodes (#4073).
      annotations:
        scheduler.alpha.kubernetes.io/critical-pod: ''.
    spec:
      containers:
      - name: fluentd-es
        image: gcr.io/google-containers/fluentd-elasticsearch:v2.0.2
        env:
        - name: FLUENTD_ARGS
          value: --no-supervisor -q
        Resources:
          limits:
            memory: 500Mi
          Requests:
            cpu: 100m
            memory: 200Mi
        volumeMounts:
        - name: varlog
          mountPath: /var/log
        - name: varlibdockercontainers
          mountPath: /var/lib/docker/containers
          readOnly: true
        - name: libsystemddir
          mountPath: /host/lib
          readOnly: true
        - name: config-volume
          mountPath: /etc/fluent/config.d
      nodeSelector:
        beta.kubernetes.io/fluentd-ds-ready: "true"
      It's not the same: 30
      Oh..:
      - name: varlog
        hostPath:
          path: /var/log
      - name: varlibdockercontainers
        hostPath:
          path: /var/lib/docker/containers
      # It is needed to copy systemd library to decompress journals
      - name: libsystemddir
        hostPath:
          path: /usr/lib64
      - name: config-volume
        configMap:
          name: fluentd-es-config-v0.1.1
```

`fluentd-configmap.yaml`
``Yaml
kind: ConfigMap
apiVersion: v1
data:
  containers.input.conf: |-
    # This configuration file for Fluentd / td-agent is used
    # to watch changes to Docker log files. # The kubelet creates symlinks that
    # capture the pod name, namespace, container name & Docker container ID
    # to the docker logs for pods in the /var/log/containers directory on the host.
    # If running this fluentd configuration in a Docker container, the /var/log
    # directory should be mounted in the container.
    #
    # These logs are then submitted to Elasticsearch which assumes the
    # the fluent-plugin-elasticsearch & the
    # fluent-plugin-kubernetes_metadata_filter plugins.
    # See https://github.com/uken/fluent-plugin-elasticsearch &
    # https://github.com/fabric8io/fluent-plugin-kubernetes_metadata_filter for
    # more information about the plugins.
    #
    # Example
    # =======
    # A line in the Docker log file might look like this JSON. #
    #
    # {"log": "2014/09/25 21:15:03 Got request with path wombat\n",
    # "stream": "stderr."
    # "time": "2014-09-25T21:15:03.499185026Z"}
    #
    # The time_format specification below makes sure we properly
    # parse the time format produced by Docker # This will be
    # submitted to Elasticsearch and should appear like:
    # $ curl 'http://elasticsearch-logging:9200/_search?pretty'
    # ...
    # {
    # "_index" : "logstash-2014.09.25."
    # "_type" : "fluentd."
    # "_id" : "VBrbor2QTuGpsQyTCdfzqA",
    # "_score" : 1.0,
    # "_source":{"log": "2014/09/25 22:45:50 Got request with path wombat\n",
    # "stream": "stderr", "tag": "docker.container.all",
    # "@timestamp": "2014-09-25T22:45:50+00:00" }
    # },
    # ...
    #
    # The Kubernetes fluentd plugin is used to write the Kubernetes metadata to the log
    # record & add labels to the log record if properly configured. This enables users
    # to filter & search logs on any metadata. #
    # For example a Docker container's logs might be in the directory:
    #
    # /var/lib/docker/containers/997599971ee6366d4a5920d25b79286ad45ff37a74494f262e3bc98d909d0a7b
    #
    # and in the file:
    #
    # 997599971ee6366d4a5920d25b79286ad45ff37a74494f262e3bc98d909d0a7b-json.log
    #
    # where 997599971ee6... is the Docker ID of the running container.
    # The Kubernetes kubelet makes a symbolic link to this file on the host machine
    # in the /var/log/containers directory that includes the pod name and the Kubernetes
    # The name... #
    #
    # synthetic-logger-0.25lps-pod_default_synth-lgr-997599971ee6366d4a5920d25b79286ad45ff37a74494f262e3bc98d909d0a7b.log
    # ->
    # /var/lib/docker/containers/997599971ee6366d4a5920d25b79286ad45ff37a74494f262e3bc98d909d0a7b/997599971ee6366d4a5920d25b79286ad45ff37a74494f262e3bc98d909d0a7b-json.log
    #
    # The /var/log directory on the host is mapped to the /var/log directory in the container
    # running this instance of Fluentd and we end up collecting the file #
    #
    # /var/log/containers/synthetic-logger-0.25lps-pod_default_synth-lgr-997599971ee6366d4a5920d25b79286ad45ff37a74494f262e3bc98d909d0a7b.log
    #
    # This results in the tag:
    #
    # var.log.containers.synthetic-logger-0.25lps-pod_default_synth-lgr-997599971ee6366d4a5920d25b79286ad45ff37a74494f262e3bc98d909d0a7b.log
    #
    # The Kubernetes fluentd plugin is used to extract the namespace, pod name & container name
    # that are added to the log message as a kubernetes field object & the Docker container ID
    # is also added under the docker field object.
    # The final tag is:
    #
    # kubernetes.var.log.containers.synthetic-logger-0.25lps-pod_default_synth-lgr-997599971ee6366d4a5920d25b79286ad45ff37a74494f262e3bc98d909d0a7b.log
    #
    # And the final log record look like:
    #
    # {
    # "log": "2014/09/25 21:15:03 Got request with path wombat\n",
    # "stream": "stderr."
    # "time": "2014-09-25T21:15:03.499185026Z."
    # "kubernetes." {
    # "namespace": "default."
    # "pod_name." "synthetic-logger-0.25lps-pod."
    # "container_name." "synth-lgr"
    # },
    # "docker": {
    # "container_id" "997599971ee6366d4a5920d25b79286ad45ff37a74494f262e3bc98d909d0a7b."
    # }
    # }
    #
    # This makes it easier for users to search for logs by pod name or by
    # the name of the Kubernetes container regardless of how many times the
    # Kubernetes pod has been restarted (resulting in a few Docker container IDs).

    # Json Log Example:
    # {"log":"[info:2016-02-16T16:04:05.930-08:00] Some log text here\n", "stream": "stdout", "time": "2016-02-17T00:04:05.931087621Z"}
    # CRI Log Example:
    # 2016-02-17T00:04:05.931087621Z stdout F [info:2016-02-16T16:04:05.930-08:00] Some log text here
    <source>
      type tail
      path /var/log/containers/*.log
      pos_file /var/log/es-containers.log.pos
      time_format %Y-%m-%dT%H:%M:%S.%NZ
      tag kubernetes.
      read_from_head true
      format multi_format
      <pattern>
        format json
        time_key time
        time_format %Y-%m-%dT%H:%M:%S.%NZ
      </pattern>
      <pattern>
        format /^(?<time>.+) (?<stream>stdout|stderr) [^ ]* (?<log>.*)$/.
        time_format %Y-%m-%dT%H:%M:%S.%N%:z
      </pattern>
    </source>
  system.input.conf: |-
    # Example:
    # 2015-12-21 23:17:22,066 [salt.state ][INFO ] Completed state [net.ipv4.ip_forward] at time 23:17:22,066081
    <source>
      type tail
      format /^(?<time>[^ ]*[^ ,]*)[^\[[^\]]*\]\[(?<severity>[^ \]]*\]. (?<message>.*)$/
      time_format %Y-%m-%d %H:%M:%S
      path /var/log/salt/minion
      pos_file /var/log/es-salt.pos
      tag salt
    </source>

    # Example:
    # Dec 21 23:17:22 gke-foo-1-1-4b5cbd14-node-4eoj startupscript: Finished running startup script /var/run/google.startup.script
    <source>
      type tail
      format syslog
      path /var/log/startupscript.log
      pos_file /var/log/es-startupscript.log.pos
      tag startupscript
    </source>

    # Examples:
    # time="2016-02-04T06:51:03.053580605Z" level=info msg="GET /containers/json"
    # time="2016-02-04T07:53:57.505612354Z" level=error msg="HTTP Error" err="No such image: -f" statusCode=404
    <source>
      type tail
      format /^time="(?<time>[^)]*)" level=(?<severity>[^ ]*) msg="(?<message>[^"]*)"( err="(?<error>[^"]*)?( statusCode=($<status_code>\d+)?
      path /var/log/docker.log
      pos_file /var/log/es-docker.log.pos
      tag docker
    </source>

    # Example:
    # 2016/02/04 06:52:38 filePurge: successfully removed file /var/etcd/data/member/wal/000000000006d0-00000000010a23d1.wal
    <source>
      type tail
      # Not parsing this, because it doesn't have anything particularly useful to
      # " parse out of it (like severities).
      format none
      path /var/log/etcd.log
      pos_file /var/log/es-etcd.log.pos
      tag etcd
    </source>

    # Multi-line parsing is required for all the kube logs because a very large log
    # statements, such as those that include entire object bodies, get split into
    # multiple lines by glog.

    # Example:
    # I0204 07:32:30.020537 3368 server.go:1048] POST /stats/container/: (13.972191ms) 200 [[Go-http-client/1.1] 10.244.1.3:40537]
    <source>
      type tail
      format multiline
      multiline_flush_interval 5s
      format_firstline /^\w\d{4}//
      format1 /^(?<severity>\w)(?<time>\d{4} [^\s]*)\s+(?<pid>\d+)\s+(?<source>[^ \]]+)\. (?<message>.*)/
      time_format %m%d %H:%M:%S.%N
      path /var/log/kubelet.log
      pos_file /var/log/es-kubelet.log.pos
      tag kubelet
    </source>

    # Example:
    # I1118 21:26:53.975789 6 proxier.go:1096] Port "nodePort for kube-system/default-http-backend:http" (:31429/tcp) was opened before and is still needed
    <source>
      type tail
      format multiline
      multiline_flush_interval 5s
      format_firstline /^\w\d{4}//
      format1 /^(?<severity>\w)(?<time>\d{4} [^\s]*)\s+(?<pid>\d+)\s+(?<source>[^ \]]+)\. (?<message>.*)/
      time_format %m%d %H:%M:%S.%N
      path /var/log/kube-proxy.log
      pos_file /var/log/es-kube-proxy.log.pos
      tag kube-proxy
    </source>

    # Example:
    # I0204 07:00:19.604280 5 handlers.go:131] GET /api/v1/nodes: (1.624207ms) 200 [[kube-controller-manager/v1.1.3 (linux/amd64) kubernetes/6a81b50] 127.0.0.1:38266]
    <source>
      type tail
      format multiline
      multiline_flush_interval 5s
      format_firstline /^\w\d{4}//
      format1 /^(?<severity>\w)(?<time>\d{4} [^\s]*)\s+(?<pid>\d+)\s+(?<source>[^ \]]+)\. (?<message>.*)/
      time_format %m%d %H:%M:%S.%N
      path /var/log/kube-apiserver.log
      pos_file /var/log/es-kube-apiserver.log.pos
      tag kube-apiserver
    </source>

    # Example:
    # I0204 06:55:31.872680 5 servicecontroller.go:277] LB already exists and doesn't need updating for service kube-system/kube-ui
    <source>
      type tail
      format multiline
      multiline_flush_interval 5s
      format_firstline /^\w\d{4}//
      format1 /^(?<severity>\w)(?<time>\d{4} [^\s]*)\s+(?<pid>\d+)\s+(?<source>[^ \]]+)\. (?<message>.*)/
      time_format %m%d %H:%M:%S.%N
      path /var/log/kube-controller-manager.log
      pos_file /var/log/es-kube-controller-manager.log.pos
      tag kube controller-manager
    </source>

    # Example:
    # W0204 06:49:18.239674 7 reflector.go:245] pkg/scheduler/factory/factory.go:193: watch the *api.service ended with: 401: The event in requested index is outdated and cleared (the requested history has been cleared [2578313/2577886]) [2579312].
    <source>
      type tail
      format multiline
      multiline_flush_interval 5s
      format_firstline /^\w\d{4}//
      format1 /^(?<severity>\w)(?<time>\d{4} [^\s]*)\s+(?<pid>\d+)\s+(?<source>[^ \]]+)\. (?<message>.*)/
      time_format %m%d %H:%M:%S.%N
      path /var/log/kube-scheduler.log
      pos_file /var/log/es-kube-scheduler.log.pos
      tag kube-scheduler
    </source>

    # Example:
    # I1104 10:36:20.242766 5 rescheduler.go:73] Running Rescheduler
    <source>
      type tail
      format multiline
      multiline_flush_interval 5s
      format_firstline /^\w\d{4}//
      format1 /^(?<severity>\w)(?<time>\d{4} [^\s]*)\s+(?<pid>\d+)\s+(?<source>[^ \]]+)\. (?<message>.*)/
      time_format %m%d %H:%M:%S.%N
      path /var/log/rescheduler.log
      pos_file /var/log/es-rescheduler.log.pos.
      tag rescheduler
    </source>

    # Example:
    # I0603 15:31:05.793605 6 cluster_manager.go:230] Reading config from path /etc/gce.conf
    <source>
      type tail
      format multiline
      multiline_flush_interval 5s
      format_firstline /^\w\d{4}//
      format1 /^(?<severity>\w)(?<time>\d{4} [^\s]*)\s+(?<pid>\d+)\s+(?<source>[^ \]]+)\. (?<message>.*)/
      time_format %m%d %H:%M:%S.%N
      path /var/log/glbc.log
      pos_file /var/log/es-glbc.log.pos
      tag glbc
    </source>

    # Example:
    # I0603 15:31:05.793605 6 cluster_manager.go:230] Reading config from path /etc/gce.conf
    <source>
      type tail
      format multiline
      multiline_flush_interval 5s
      format_firstline /^\w\d{4}//
      format1 /^(?<severity>\w)(?<time>\d{4} [^\s]*)\s+(?<pid>\d+)\s+(?<source>[^ \]]+)\. (?<message>.*)/
      time_format %m%d %H:%M:%S.%N
      path /var/log/cluster-autoscaler.log
      pos_file /var/log/es-cluster-autoscaler.log.pos
      tag cluster-autoscaler
    </source>

    # Logs from systemd-journal for interesting services.
    <source>
      type systemd
      filters [{ "_SYSTEMD_UNIT": "docker.service" }].
      pos_file /var/log/gcp-journald-docker.pos
      read_from_head true
      tag docker
    </source>

    <source>
      type systemd
      filters [{ "_SYSTEMD_UNIT": "kubelet.service" }].
      pos_file /var/log/gcp-journald-kubelet.pos
      read_from_head true
      tag kubelet
    </source>

    <source>
      type systemd
      filters [{ "_SYSTEMD_UNIT": "node-problem-detector.service" }].
      pos_file /var/log/gcp-journald-node-problem-detector.pos
      read_from_head true
      tag node-problem-detector
    </source>
  forward.input.conf: |-
    # Takes the messages sent over TCP
    <source>
      type forward
    </source>
  monitoring.conf: |-
    # Prometheus Exporter Plugin
    # input plugin that exports metrics
    <source>
      @type prometheus
    </source>

    <source>
      @type monitor_agent
    </source>

    # input plugin that collects metrics from MonitorAgent
    <source>
      @type prometheus_monitor
      <labels>
        host ${hostname}
      </labels>
    </source>

    # input plugin that collects metrics for output plugin
    <source>
      @type prometheus_output_monitor
      <labels>
        host ${hostname}
      </labels>
    </source>

    # input plugin that collects metrics for in_tail plugin
    <source>
      @type prometheus_tail_monitor
      <labels>
        host ${hostname}
      </labels>
    </source>
  output.conf: |-
    # Enriches records with Kubernetes metadata
    <filter kubernetes.**>
      type kubernetes_metadata
    </filter>

    <match **>
       type elasticsearch
       log_level info
       include_tag_key true
       host elasticsearch-logging
       port 9200
       logstash_format true
       logstash_prefix fluentd
       # Set the chunk limits.
       buffer_chunk_limit 2M
       buffer_queue_limit 8
       flush_interval 5s
       # Never wait longer than five minutes between retries #
       max_retry_wait 30
       # Disable the limit on the number of retries (retry forever).
       disable_retry_limit
       # Use multiple threads for processing.
       num_threads 2
    </match>
metadata:
  name: fluentd-es-config-v0.1.1
  labels:
    addonmanager.kubernetes.io/mode: Reconcile
```

`eservice.yaml`
``Yaml
apiVersion: v1
kind: Service
metadata:
  name: elasticsearch-logging
  The labels:
    k8s-app: elasticsearch-logging
    kubernetes.io/cluster service: "true"
    addonmanager.kubernetes.io/mode: Reconcile
    kubernetes.io/name: "Elasticsearch"
spec:
  ports:
  - port: 9200
    Protocol: TCP
    targetPort: db
  Selector:
    k8s-app: elasticsearch-logging
```

`es-statefulSet.yaml`
``Yaml
apiVersion: apps/v1beta2
kind: StatefulSet
metadata:
  name: elasticsearch-logging
  The labels:
    k8s-app: elasticsearch-logging
    version: v5.6.4
    kubernetes.io/cluster service: "true"
    addonmanager.kubernetes.io/mode: Reconcile
spec:
  serviceName: elasticsearch-logging
  replicas: 1
  Selector:
    matchLabels:
      k8s-app: elasticsearch-logging
      version: v5.6.4
  template:
    metadata:
      labels:
        k8s-app: elasticsearch-logging
        version: v5.6.4
        kubernetes.io/cluster service: "true"
    spec:
      nodeSelector:
        elastichost: "true"
      I'm sorry:
      - image: k8s.gcr.io/elasticsearch:v5.6.4
        name: elasticsearch-logging
        Resources:
          # need more cpu upon initialization, therefore burstable class
          The limits:
            cpu: 1000m
          Requests:
            cpu: 100m
        ports:
        - containerPort: 9200
          name: db
          Protocol: TCP
        - containerPort: 9300
          name: transport
          Protocol: TCP
        volumeMounts:
        - name: es-pvc-volume
          mountPath: /data
        I'm sorry:
        - name: MINIMUM_MASTER_NODES
          value: "1"
        - name: "NAMESPACE"
          valueFrom:
            fieldRef:
              fieldPath: metadata.space
      Oh..:
      - name: es-pvc-volume
        The VolumeClaim:
          claimName: elasticsearch-logging-claim
      # Elasticsearch requires vm.max_map_count to be at least 262144.
      # If your OS already sets up this number to a higher value, feel free
      # to remove this init container.
      InitContainers:
      - image: alpine:3.6
        command: ["/sbin/sysctl", "-w", "vm.max_map_count=262144"]
        name: elasticsearch-logging-init
        securityContext:
          privileged: true
```

`es-pvc.yaml`
``Yaml
---
kind: PersistentVolumeClaim .
apiVersion: v1
metadata:
  name: elasticsearch-logging-claim
spec:
  storageClassName: standard
  accessModes:
    - ReadWriteOnce
  Resources:
    requests:
      storage: 2Gi
```

Run the stack on your k8s.
``shell
kubectl apply -f ./efk
```

Kibana will be on the helm chart.

``shell
helm upgrade --install kibana stable/kibana \
  -set "ingress.enabled=true" \.
  -set "ingress.hosts={reddit-kibana}" \
  -set "env.ELASTICSEARCH_URL=http://elasticsearch-logging:9200" \.
  --version 0.1.1
```

``shell
kubectl --namespace=default get pods -l "app=kibana"
```
``log
NAME READY STATUS RESTARTS AGE
kibana-65f8986c64-tpgb2 1/1 Running 0 4m24s
```

It's been a success since the first time O_o.

The interface is available at http://reddit-kibana.

Let's create an index pattern `fluentd-* `

Open the Discover tab in Kibana and enter the following expression into the search box
```
kubernetes.labels.component:post OR kubernetes.labels.component:comment OR
kubernetes.labels.component:ui
```
and we see our component logs =)

Open any of the search results - you can see a lot of information about k8s.

1. The peculiarity of fluentd's work in k8s is that its task is not only to collect logs of applications, services and hosts themselves, but also to recognize additional metadata (usually these are additional fields with labels).
2. Where and what logs fluentd collects - you can see in its `fluentd-configmap.yaml` and in `fluentd-ds.yaml`.
3. The general scheme of fluentd's work is presented on the trace. slide

### Task from \ ##: Helm Chart EFK

Create a Helm Chart to install the EFK stack and place it in the
charts directory

TODO: do... sometime later, maybe be, there's already some ready-made ones, like https://github.com/helm/charts/tree/master/stable/elastic-stack.
