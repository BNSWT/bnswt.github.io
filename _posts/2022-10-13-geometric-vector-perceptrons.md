---
title: 'Geometric Vector Perceptrons'
date: 2022-10-13
permalink: /posts/2022/10/geometric-vector-perceptrons/
tags:
  - structure modeling
  - graph neural network
  - convolutional neural network
---

The `geometric vector perceptron` is a simple module for learning vector-valued and scalar-valued functions over geometric vectors and scalars. GVP-GNN can be applied to any problem where the input domain is a structure of a single macromolecule or of molecules bound to one another.

## Problem Statement

`Structure modeling` can often be framed as functions mapping the input domain of structures to some property of interest. This is a representation extractor that often act as a submodule of some neural networks. It can be applied to some downstream tasks such as `Computational Protein Design (CPD)` and `Model Quality Assessment`.

## Structure representations

### Sequential Representations

In traditional models of learning from protein structure, each amino acid is represented as a feature vector using hand-crafted representations of the 3D structural environment, which may include:

+ residue contacts
+ orientations or positions collectively projected to local coordinates
+ physics-inspired energy terms
+ context-free grammars of protein topology

Structure is viewed as a sequence or collection of these features which can be fed into a 1D convolutional network, RNN or dense feedforward network.

### Voxelized representations

Directly use the positions of atoms in space and feed them to 3D CNN. This mainly focus on the geometric aspect of the domain. This representation is compatible with problems like:

+ the detection of structural motifs
+ binding pockets
+ specific shape of other important structural features

### Graph-structured representations

Protein structure can be represented as a `proximity graph` over amino acid nodes. All the structural neighborhoods could then be represented by individual edges rather than a single vector. GNN can perform complex `relational reasoning` over structures:

+ identify key relationships among amino acids
+ describe flexible structural motifs as a connectivity pattern rather than a rigid shape

The representation of geometry varies between different methods:

+ ProteinSolver and GraphQA: represent edges as a function of their length
+ Structured Transformer: encode the 3D
