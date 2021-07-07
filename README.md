# container-definitions

This repository contains recipes for docker containers that can be used 
for building singularity containers for some odd software packages that
use old or legacy or otherwise unavilable dependecnies.

## Recipes

All docker files are stored in recipes/. 
Naming convention: _swname.recipe_

Use default build docker file as specified by the software package.
MAy need to add the following sections:

- **%labels** section is used to add metadata to the container image, for example
  ```text
  %labels
    Author XYZ
    Version v0.0.1
  ```
-  **%help** section  is used for info about the image< for example
  ```text
  %help
    This container provides X.
    See URL-to-gitrepo for usage
   ```

## Container build

To create a singulartiy container from the recipe file:

```bash
cd /tmp
module load singularity/3.7.2 
singularity build hla.simg hla.recipe 
```

## Container check

Inspect labels in the image 

```bash
singularity inspect name.simg
```

Inspect the content of _%help_ section:
```bash
singularity run-help name.simg
```
## Container check

Container can be run with the followign commands

```bash
singularity shell hla.simg 
```
or
```bash
singularity run hla.simg 
```
