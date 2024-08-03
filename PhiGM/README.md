# PhiGM

A TTRPG Game Master in a box. [Based on Phi-3 Mini](https://ollama.com/library/phi3).

I based this on Microsoft's Phi-3 "small language model" because it's comparatively small for a model, which makes it less resource intensive, but still fairly responsive and capable. This matters, in part, because I am thinking of deploying this model on a fairly resource-constrained edge system, such as a Raspberry Pi 5.

## Setup 

```
ollama pull phi3
ollama create PhiGM -f ./Modelfile
```

## Running

```
ollama run PhiGM
```