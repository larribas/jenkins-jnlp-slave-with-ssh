# jenkins-jnlp-slave-with-ssh

Based on [jenkinsci/jnlp-slave](https://github.com/jenkinsci/docker-jnlp-slave), but adding ssh access for git repositories.


## Background

When leveraging plugins such as [the one for Kubernetes integration](https://github.com/jenkinsci/kubernetes-plugin), one needs slaves to be able to clone private git projects via SSH.


## Usage

Just override the slave's base image. For example, using the Kubernetes plugin you would have to add the following container template to the pod template:

```
containerTemplate(name: 'jnlp', image: 'larribas/jenkins-jnlp-slave-with-ssh:1.0.0', args: '${computer.jnlpmac} ${computer.name}'),
```
