# Sigma Operationalization Workshop

Operationalization of [Sigma rules](https://sigmahq.io/) requires that generic Sigma detection rules are transformed
into queries or detection rules that work in the SIEM or EDR. Furthermore, field names and values contained in the
detections must be transformed in a way that they match on the logs in the environment. This workshop gives an introduction
into how this conversion can be done with processing pipelines in [pySigma](https://github.com/SigmaHQ/pySigma) with the
command line interface [Sigma CLI](https://github.com/SigmaHQ/sigma-cli).

##  Topics

* Mapping field names
* Value transformations
* Adding conditions
* Placeholders
* Embedding queries into file structures

## Prerequisites

* Python 3.9 to 3.12
* [Sigma CLI](https://github.com/SigmaHQ/sigma-cli):
  * Recommendation: install in separate Python environment with [pipx]([Sigma CLI](https://github.com/SigmaHQ/sigma-cli)) `pipx install sigma-cli`.
* Clone the SigmaHQ rule repository with `git clone https://github.com/SigmaHQ/sigma.git`
* Clone of this workshop repository.

