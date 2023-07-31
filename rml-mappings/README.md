# RML Mappings from AAS to OWL
This directory contains all mappings from an AAS (containing capabilities and skills) into an ontology according to [this model](https://github.com/aljoshakoecher/caskman).

## Capability Mappings

### Capability Mapping
In this mapping, a JsonPath iterator is defined to find all capability containers inside an AAS. Inside the `subjectMap`, every capability's idShort is taken in order to create an individual of the OWL class `CSS:Capability`.
The `predicateObjectMap` is used to add each capability's AAS comment as an `rdfs:label` to the corresponding individual.Therefore, the iterator is extended to look into the comment of the current capability container and look for an English comment. This comment is then attached to the capability individual as an `rdfs:label`.

### Capability Property Mapping
This mapping starts out similar as the first one. In order to add capability properties to their corresponding capabilities, a JsonPath iterator looks for all capability containers. Then, inside the `subjectMap`, all capabilities are used as the subject. What's different here is that a `predicateObjectMap` is used to connect capability properties with the object property `CSS:isSpecfiedBy`. To find the corresponding property, the template appends a search path looking for properties inside the current container.

In addition to this rule, there is a second mapping rule that adds the comments of a capability property to the corresponding capability property. In order to get the pairs of properties with their comments, this second rule has an iterator looking for all property containers independent of a capability. Then, inside the `subjectMap`, each property is defined. This is basically a duplicate to the `objectMap` of the first rule in this section, but each rule must have a `subjectMap`. Then, inside the `predicateObjectMap`, each property's comment is added as an `rdfs:label`. This is comparable to the way a capability's comment is added as a label (see first section above).

### Capability Constraint Mapping
🚧
How capability constraints are modeled in AAS is currently not defined on a sufficient level of detail. This mapping is therefore not yet implemented.
🚧