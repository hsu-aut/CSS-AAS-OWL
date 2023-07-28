# RDFex Mappings from OWL to AAS
This directory contains all mappings from a capability and skill ontology modeled in accordance to [this model](https://github.com/aljoshakoecher/caskman).

## Capability Mappings

### Capability Mapping
In this mapping, all capabilities, i.e., all individuals of the class `CSS:Capability` are retrieved and using SPARQL's `STRAFTER` function, the local name is extracted. Additionally, a `rdfs:comment` of each capability is retrieved in case there is one.

A CapabilitySet's value is used as the container so that capabilities together with their encapsulating containers are added into an AAS.
The snippet consists of a CapabilityContainer and a Capability together with a Comment in AAS JSON syntax. The variable `?capName` is used for the idShort of the capability container, the capability and the comment. The `rdfs:comment` is used to set the value of the capability's comment.


### Capability Property Mapping
This query is quite similar to the capability mapping above, but it goes one level deeper, into each capability's PropertySet. Thus it makes sense to first execute the capability mapping above in order to properly construct the capability structure before adding properties.
The query retrieves the properties of all capabilities together with an `rdfs:comment` that might exist for each property. 

In order to add properties correctly to the capabilities they belong to, the container definition targets each capability's property set. This is achieved by using the variable `?capability`, which holds each capability's IRI, inside the container definition. 
The JSON snippet consists of a PropertyContainer and a Property together with a Comment of the property in AAS JSON syntax. The variables `?capability` and `?propertyName` are used for the idShort of the property container, the capability and the comment in order to define unique. The `rdfs:comment` value `?propComment` is used to set the value of the property's comment.


### Capability Constraint Mapping
🚧
How capability constraints are modeled in AAS is currently not defined on a sufficient level of detail. This mapping is therefore not yet implemented.
🚧