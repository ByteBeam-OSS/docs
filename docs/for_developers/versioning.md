# Naming Conventions and Versioning

Since the SexyCoders ecosystem is an open source and community based project, 
we have implemented and are strictly abiding to naming conventions so that everyone can follow.

Please follow them or you will risk your work not being approved by our review team.

## Helpers

To help navigate and automate these and many other proccesses we have created a set of commands under /bin
the SexyCoders main repository.

It is suggested to use those instead! Find documentation on them [here](/for_developers/helpers/).

If you still wish to do it by hand read on.

Please also look in the individual dirs for ".format" files that will direct
you further for the specifics of each service (like name conventions, reserved
naems, legacy compatibillity issues etc.)

## General Format

The general date format for versioning is 14-05-2023_1231_EEST and can be produced using the following:

```bash
date +'%d-%m-%Y_%H%M_%Z'
```

This date format was introduced in March 2023 and applied to all aspects of the
sexycoders ecosystem to create a unified approach to versioning.

We expect it to have fully replaced any old versioning within a couple of
months.

## Docker

For docker please use 

```bash
vXX_$(date +'%d-%m-%Y_%H%M_%Z')
```
for example if building "example_image" and latest version is 12 do:

```bash
docker build -t registry.sexycoders.org/example_image:v12_$(date +'%d-%m-%Y_%H%M_%Z')
```

## Git Branches

For git branches use a similar approach :

```bash
<branch_name>_$(date +'%d-%m-%Y_%H%M_%Z')
```

For example to create a branch named new_branch from the master:

```bash
git checkout -B new_branch_$(date +'%d-%m-%Y_%H%M_%Z')
```
