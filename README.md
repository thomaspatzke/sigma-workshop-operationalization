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

* Python 3.9 to 3.13
* [Sigma CLI](https://github.com/SigmaHQ/sigma-cli):
  * Recommendation: install in separate Python environment with [pipx]([Sigma CLI](https://github.com/SigmaHQ/sigma-cli)) `pipx install sigma-cli`.
  * To follow the examples from the presentation install the Splunk and Elasticsearch plugins: `sigma plugin install splunk elasticsearch`
* Clone the SigmaHQ rule repository with `git clone https://github.com/SigmaHQ/sigma.git`
* Clone of this workshop repository with submodules: `git clone --recurse-submodules https://github.com/thomaspatzke/sigma-workshop-operationalization.git`

## Commands

1. Conversion without processing pipeline: `sigma convert -t splunk --without-pipeline sigma\rules\windows\process_creation\proc_creation_win_rundll32_obfuscated_ordinal_call.yml`

2. Conversion with first pipeline with field mappings, value conversions and removals: `sigma convert -t splunk -p pipeline-1.yml sigma\rules\windows\process_creation\proc_creation_win_rundll32_obfuscated_ordinal_call.yml`

3. Conversion that raises error due to unsupported value: `sigma convert -t splunk -p pipeline-2.yml sigma\rules\windows\process_creation\proc_creation_win_appvlp_uncommon_child_process.yml`

4. Addition of conditions: `sigma convert -t splunk -p pipeline-3.yml sigma\rules\windows\process_creation\proc_creation_win_rundll32_obfuscated_ordinal_call.yml`

5. Error on unhandled placeholders: `sigma convert -t splunk -p pipeline-3.yml sigma\rules-placeholder\windows\process_creation\proc_creation_win_userdomain_variable_enumeration.yml`

6. Replacement of placeholders: `sigma convert -t splunk -p pipeline-4.yml sigma\rules-placeholder\windows\process_creation\proc_creation_win_userdomain_variable_enumeration.yml`

7. Conversion of rule set without query postprocessing as separate queries: `sigma convert -t splunk -p pipeline-4.yml sigma\rules\windows\process_access\`

8. Conversion of rule set with query postprocessing to output a Splunk savedsearches.conf: `sigma convert -t splunk -p pipeline-5.yml sigma\rules\windows\process_access\`