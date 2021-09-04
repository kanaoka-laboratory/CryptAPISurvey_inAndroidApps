Data Description
====

## fil_rule_fix202008.tsv
This file is the filter data we used to find package names, class names, method names, and argument types that contain the keywords "encryp", "decryp", and "cipher".

One line in the file is one filter rule.
The package name, class name, method name, and argument type that contain these three keywords include those that are identified as not cryptography-related functions.
Therefore, the filter rule contains a flag to indicate whether it is a cryptographic related function or not.

A single filter rule is separated by tabs. Each element is described in the following table.

| Element | Description |
----|----
| 1st element | Type of rule. 0: package name, 1: package and class name, 2: package, class, method and argment type |


## fil_forApps.tsv




